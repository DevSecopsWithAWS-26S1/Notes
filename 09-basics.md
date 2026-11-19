# Linux user and group management

## Local users

Create a user and set a password:

```sh
sudo adduser <username>
sudo passwd <username>
```

Delete a user:

```sh
sudo userdel <username>
```

Delete a user and their home directory:

```sh
sudo userdel -r <username>
```

## Enable password authentication

Password login is not enabled on every SSH server. If required, review the SSH configuration and snippet files before changing settings:

```sh
sudo vi /etc/ssh/sshd_config
sudo ls /etc/ssh/sshd_config.d/
```

Set these options in the active SSH configuration:

```text
PasswordAuthentication yes
PubkeyAuthentication yes
UsePAM yes
```

Back up and inspect included configuration files, then restart SSH and verify connectivity:

```sh
sudo systemctl restart sshd
sudo systemctl status sshd
```

Keep another active SSH session while testing. Incorrect SSH settings can block access.

## Groups

Create a group:

```sh
sudo groupadd <groupname>
```

Add a user to a secondary group:

```sh
sudo usermod -aG <groupname> <username>
```

Set a user's primary group:

```sh
sudo usermod -g <groupname> <username>
```

Remove a user from a group:

```sh
sudo gpasswd -d <username> <groupname>
```

A user must belong to at least one group. List membership or available groups with:

```sh
groups <username>
getent group
cat /etc/group
```

## Add SSH key access

The user generates a key pair on their local machine:

```sh
ssh-keygen
```

Send the **public** key to the server administrator. On the server, create or update the user's SSH directory:

```sh
sudo adduser <username>
sudo mkdir -p /home/<username>/.ssh
sudo vi /home/<username>/.ssh/authorized_keys
sudo chmod 700 /home/<username>/.ssh
sudo chmod 600 /home/<username>/.ssh/authorized_keys
sudo chown -R <username>:<username> /home/<username>/.ssh
```

Never send or store a private key on the server.

## Grant administrative access

Add a user to the `wheel` group on RHEL-based systems:

```sh
sudo usermod -aG wheel <username>
```

For passwordless `sudo`, edit the sudoers configuration safely:

```sh
sudo visudo
```

Add a dedicated rule, for example:

```text
krishna ALL=(ALL) NOPASSWD: ALL
```

Prefer scoped sudo privileges when full passwordless access is not required.

## Create a system account

System accounts do not normally log in or receive a home directory:

```sh
sudo adduser -r -M -s /sbin/nologin <username>
```
