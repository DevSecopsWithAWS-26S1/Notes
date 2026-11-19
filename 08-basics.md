# Linux file and text commands

## View file portions

```sh
head <filename>       # First 10 lines
head -n 5 <filename>  # First 5 lines
tail <filename>       # Last 10 lines
tail -n 5 <filename>  # Last 5 lines
```

## Search file content

```sh
grep "<pattern>" <filename>       # Search
grep -i "<pattern>" <filename>    # Ignore case
grep -r "<pattern>" <directory>   # Search recursively
```

## Download content

```sh
wget <url>
curl -O <url>
```

Use `curl` to print a response in the terminal or `curl -o <file> <url>` to save it.

## Extract fields

`cut` and `awk` extract columns from structured text. For example:

```text
root:x:0:0:root:/root:/bin/bash
```

The fields are separated by `:`:

```sh
cut -d ":" -f 1 /etc/passwd
cut -d ":" -f 1,6 /etc/passwd

awk -F ":" '{print $1}' /etc/passwd
awk -F ":" '{print $NF}' /etc/passwd
awk -F ":" '{print $1, $6}' /etc/passwd
```

Combine commands with a pipe (`|`) to filter output:

```sh
cut -d ":" -f 1,6 /etc/passwd | grep "ec2-user"
grep -i "ec2-user" /etc/passwd
```

## AWS EC2 server access

AWS EC2 instances normally use key-based authentication. Connect with the default user for the selected AMI:

```sh
ssh -i "<key.pem>" ec2-user@<public-ip>
```

Ubuntu images commonly use `ubuntu` as the default login user.

```sh
ssh -i "<key.pem>" ubuntu@<public-ip>
```

Use `sudo` for administrative commands:

```sh
sudo cat /etc/ssh/sshd_config
sudo su
sudo su -
```

`sudo su -` switches to root and loads root's environment. Use it carefully.

## Important system files

- `/etc/passwd` contains local user account information.
- `/root` is the root user's home directory.
- `/etc/ssh/sshd_config` controls SSH server settings.

Always back up configuration files before editing them:

```sh
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

## Security groups

AWS security groups are stateful virtual firewalls.

- **Inbound rules** control traffic entering the instance.
- **Outbound rules** control traffic leaving the instance.

Common ports:

| Service | Port |
|---|---:|
| SSH | 22 |
| HTTP | 80 |
| Application server | 8080 |
| HTTPS | 443 |

`0.0.0.0/0` allows access from every IPv4 address. Use it only when public access is required.
