# ExpenseTracker

## DNS records

| Record | Purpose |
|---|---|
| A | Routes a domain to an IPv4 address |
| AAAA | Routes a domain to an IPv6 address |
| CNAME | Routes a domain to another domain or AWS service |
| MX | Routes email to mail servers |
| TXT | Stores text data such as verification or configuration values |

TTL controls how long DNS servers may cache a record.
DNS changes may take time to propagate.

## Application components

| Component | Purpose | Logs |
|---|---|---|
| Nginx | Serves the frontend and acts as a reverse proxy | `/var/log/nginx/` |
| Node.js backend | Runs the application API | `journalctl -u backend` |
| MySQL | Stores application data | `journalctl -u mysqld` and `/var/log/mysql/` |

SQL organizes data with schemas, tables, rows, and columns.

## HTTP methods

| HTTP Method | Description |
| :--- | :--- |
| GET | Retrieve data from a server |
| POST | Send data to create a new resource |
| PUT | Replace an existing resource entirely |
| PATCH | Partially update an existing resource |
| DELETE | Remove a specified resource |
| HEAD | Retrieve response headers without the response body |
| OPTIONS | Describe communication options for the target resource |
| CONNECT | Establish a tunnel to the server |
| TRACE | Perform a message loop-back test along the path to the target resource |


* Error codes :



| Status Code | Name | Category | Detailed Meaning | Common Real-World Cause |
| :--- | :--- | :--- | :--- | :--- |
| **200** | OK | 2xx Success | Request succeeded and returned the requested data in the response body | Standard `GET` fetch or `PUT`/`PATCH` update succeeding |
| **201** | Created | 2xx Success | Request succeeded and a **new resource was created** on the server | Successful `POST` request inserting a new record into the database |
| **202** | Accepted | 2xx Success | Request accepted for processing, but the task is not yet finished | Triggering an asynchronous background job or batch task |
| **204** | No Content | 2xx Success | Request succeeded, but the server intentionally returns no response body | Successful `DELETE` request removing a record |
| **301** | Moved Permanently | 3xx Redirection | Resource has permanently moved to a new URL; clients should update links | Redirecting HTTP to HTTPS (`http://` -> `https://`) in Nginx/ALB |
| **302** | Found | 3xx Redirection | Resource is temporarily located at a different URL | GitHub `?raw=true` redirecting to `://githubusercontent.com` or OAuth login redirects |
| **304** | Not Modified | 3xx Redirection | Cached version of the resource is still valid; no need to re-download | Browser loading cached CSS/JS assets instead of fetching them again |
| **307** | Temporary Redirect | 3xx Redirection | Temporary redirect that strictly preserves the original HTTP method (`POST` stays `POST`) | Maintenance routing or API gateway temporary forwarding without changing request method |
| **400** | Bad Request | 4xx Client Error | Server cannot process the request due to invalid client syntax or payload | Malformed JSON body or missing required fields in a `POST` request |
| **401** | Unauthorized | 4xx Client Error | Request lacks valid authentication credentials | Missing, invalid, or expired API token / JWT |
| **403** | Forbidden | 4xx Client Error | Server understands the identity, but refuses access to the resource | Insufficient user permissions or Nginx/OS file permission blocks |
| **404** | Not Found | 4xx Client Error | Requested URL endpoint or file does not exist on the server | Typo in API route path or wrong GitHub file URL |
| **500** | Internal Server Error | 5xx Server Error | Generic catch-all error indicating the backend application crashed | Unhandled code exception, wrong `DB_HOST` env var, or SQL query error |
| **502** | Bad Gateway | 5xx Server Error | Reverse proxy (Nginx/ALB) got an invalid or empty response from upstream | Node.js backend service is stopped (`systemctl status backend`) or wrong port |
| **503** | Service Unavailable | 5xx Server Error | Server is temporarily unable to handle the request | Server overloaded, restarting, or under maintenance |
| **504** | Gateway Timeout | 5xx Server Error | Proxy waited too long for a response from the upstream backend server | Backend hanging on a blocked database connection (e.g., AWS Security Group) |





## Task

Set up the ExpenseTracker application and troubleshoot all reported issues.

## Troubleshooting

Check Nginx file permissions and ownership:

```bash
sudo journalctl -u nginx
sudo tail -f /var/log/nginx/error.log
```

Check MySQL:

```bash
sudo systemctl status mysqld
sudo journalctl -u mysqld
sudo tail -f /var/log/mysql/mysqld.log
sudo tail -f /var/log/mysql/mysql.log
sudo ss -lntp
```

Verify:

- The MySQL security group allows the required application traffic.
- The server has the correct password for `root` and `expense`.
- The `transactions` database and required tables exist.

Check the Node.js backend:

```bash
sudo systemctl status backend
sudo journalctl -u backend
sudo tail -f /var/log/messages
sudo ss -lntp
```

Verify:

- `/app` contains the deployed code.
- `/etc/systemd/system/backend.service` has the correct database IP and password.
- The backend service runs `/bin/node /app/index.js`.

Check the frontend:

```bash
sudo systemctl status nginx
sudo journalctl -u nginx
sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
```

Verify:

- `/etc/nginx/default.d/expense.conf` points to the correct backend IP.
- `/usr/share/nginx/html` contains the deployed frontend files.
- Folder permissions and ownership allow Nginx to read the files.

## Subdomains

You can create subdomains of a main domain in its Route 53 hosted zone.