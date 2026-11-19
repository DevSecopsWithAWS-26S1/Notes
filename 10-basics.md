# Linux packages and services

## Package management

RHEL 9 uses `dnf` as its package manager.

```sh
sudo dnf install git -y
sudo dnf install <package-name> -y
sudo dnf update <package-name> -y
sudo dnf remove <package-name> -y
```

Search and list packages:

```sh
dnf search java-11-openjdk
dnf list installed
dnf list available
```

## Change an EC2 instance type

An instance type may be changed in the AWS console or CLI:

1. Stop the instance.
2. Change the instance type.
3. Start the instance.

Stopping and restarting an EC2 instance does not change its private IP when it remains in the same subnet. A public IPv4 address is normally released and replaced when the instance restarts.

## Nginx

Nginx is a web server and reverse proxy. It commonly serves static HTML, CSS, and JavaScript files and forwards requests to backend services.

```sh
sudo dnf install nginx -y
```

## Proxy and client-server concepts

- A **client** requests a resource.
- A **server** provides the resource.
- A **forward proxy** represents clients to external networks. A VPN is an example.
- A **reverse proxy** represents backend servers to clients. Nginx is commonly used for this.

For example, a browser is a client and `amazon.com` is a server.

![Client-server example](./Images/basics4.png)

## Service management

Use `systemctl` to manage and inspect services:

```sh
sudo systemctl status <service>
sudo systemctl start <service>
sudo systemctl stop <service>
sudo systemctl restart <service>
sudo systemctl enable <service>
sudo systemctl enable --now <service>
```

`enable` starts the service automatically after a reboot. `enable --now` enables it and starts it immediately.

## Process management

```sh
ps -ef
top
kill <process-id>
kill -9 <process-id>
```

- `ps -ef` displays running processes.
- `top` shows live CPU and memory usage.
- `kill` asks a process to stop.
- `kill -9` forces a process to stop and should be used only when normal termination fails.

## Network management

Install common network tools on RHEL:

```sh
sudo dnf install net-tools -y
```

Inspect listeners and test connectivity:

```sh
sudo netstat -lntp
ping <ip-address>
telnet <ip-address> 80
```

- `netstat -lntp` lists listening TCP ports and process IDs.
- `ping` tests network reachability.
- `telnet` tests whether a TCP port accepts connections.

## Application architectures

### Frontend

The frontend presents the user interface. It may use HTML, CSS, JavaScript, React, or similar technologies.

### Backend

The backend handles business logic and APIs. Common choices include Java, Node.js, Python, and .NET.

### Database

- SQL databases include MySQL and PostgreSQL.
- NoSQL databases include MongoDB and DynamoDB.

### Architecture styles

- A **monolithic application** runs all components together.
- A **three-tier application** separates presentation, application logic, and data.
- **Microservices** split functionality into independently deployed services.

![Monolithic and tiered architecture](./Images/basics5.png)
