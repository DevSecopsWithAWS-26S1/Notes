* DNS propagation.

## Type of records:
* A  - route trafffic to ipv4 
* AAAA - route traffic to ipv6 
* CNAME - route domain to another domain or AWS service 
* MX - mailing records 
* TXT - key:value 
* TTL - Time to live - It decides how much a cache can be used on the ISP DNS servers 

## ExpenseTracker application:
### nginx 
* It is popular web server which can hosts html,csss,.js . It is popular for reverse proxy 
* logs path - /var/log/nginx 

### nodejs 
* It is designed on nodejs 
* logs  - journalctl -u backend

### mysql - database 
* SQL - Structured Query Language 
* SQL - Schemas >>  tables >> rows and colums 
* logs - journalctl -u mysqld
* logs path - /var/log/mysql 

## http methods & status code 

& http methods :

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





### Task:
* Setup Expense tracker and try to fix the issues 


### Troubleshooting :
* file permissins issue / ownership issue  >>   /var/log/nginx/error.log 

* check the mysqld service and logs 
    * systemctl status mysqld - service check 
    * journalctl -u mysqld 
    * /var/log/mysql/mysqld.log
    * /var/log/mysql/mysql.log
    * netstat -lntp 
    * firewall SG is allowed or not . (All allow)
    * check the mqsql server is configured with correct password 
        * for both root and expense users 
    * Check whether the transactions DB is available &  table is available 

* check the backend service and logs 
    * systemctl service backend 
    * journactl -u backend 
    * /var/log/messages 
    * netstat -lntp
    * firewall SG is allowed or not . (All allow)
    * /app 
    * code is deployed proper 
    * backend service configuration - /etc/systemd/system/backend.service
        * whether we provided correct mysql ip address & password 
        * running command for the backend - /bin/node /app/index.js


* check the frontend service and logs
    * systemctl status nginx 
    * journalctl -u nginx 
    * /var/log/nginx/access.log 
    * /var/log/nginx/error.log 
    * reverse proxy configuration -/etc/nginx/default.d/expense.conf
        * check the backend ip is proper provided
    * /user/share/nginx/html - default files removed or not 
    * Verify whther frontend code is properly deployed 
    * folder permissions and ownership permissions 


## subdomains :
* you can create subdomains to a main domain in hosted zone 