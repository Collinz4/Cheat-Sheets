# Cheat Sheet

### Bash Operators/Separators

`|` Sends standard output `stdout` from one command into the standard output of another. Standard error is still directed to it's default destination.

`|&` Directs `stdout` and `stderr` from one command to another.

`&&` Executes the right hand command of `&&` only if the previous one succeeded.

`||` Executes the right hand command of `||` only if the previous one failed.

`;` Executes the right hand command of `;` regardless if the previous command succeeded or failed. Unless `set -e` was previously invoked, which causes `bash` to fail on an error.

### Green Unicorn Worker Formula

`number of works = 2 * number of system cores + 1`

Arguement `--workers=[n]` specifies the amount of works to use.

### GIT

#### [Updating Forked Repo](https://medium.com/@topspinj/how-to-git-rebase-into-a-forked-repo-c9f05e821c8a)

1. Add remote and call it 'upstream'.

   `git remote add upstream <url to repo>`

2. Fetch all branches of remote upstream.

   `git fetch upstream`

3. Rewrite local master with upstream master.

   `git rebase upstream/master`

4. Push updates to master.

   `git push origin master --force`

#### Duplicating a GIT Branch

```bash
git checkout -b <new branch> <existing branch>
```

### Docker

#### Commonly Used Commands

##### Remove Container

​	`docker container rm <container ID>`

##### Remove all Containers

​	`docker container rm $(docker ps -a -q)`

##### Remove all Images

​	`docker rmi $(docker images -a -q) --force`

##### Stop Docker Container

​	`docker stop <container ID`

##### Create Docker Network

​	`docker network create <network name>`

##### Shell into a running Container

​	`docker exec -it <container name> bash`

##### Shell into Container at Startup

​	`docker run -it <image name> bash`

### Docker Compose

#### Commonly Used Commands

##### Docker Compose Logs

​	`docker-compose logs -f`

##### Docker Compose Logs (from specific container)

​	`docker-compose logs <container ID> -f`

### MySQL

##### Creating User and Setting Privileges

```mysql
CREATE USER '<user>'@'<host address>' IDENTIFIED BY '<password>';
```

```mysql
GRANT SELECT, INSERT, UPDATE, DELETE ON <schema>.<tables> TO 'user'@'host address';
```

```mysql
FLUSH PRIVILEGES;
```

```mysql
SHOW GRANTS username;
```

##### Removing a User

```mysql
DROP USER '<user>'@'<host address>';
```

### Setting Up SSH On New Server

1. Generate 2048 Bit Key

```bash
$ ssh-keygen
```

2. Sending RSA Key To New Server

```bash
$ ssh-copy-id <username>@<ip address>
```

3. Harden SSH Security Settings (https://blog.devolutions.net/2017/4/10-steps-to-secure-open-ssh)

```bash
$ vim /etc/ssh/sshd_config

AllowUsers <user 1> <user 2>
PermitEmptyPasswords no
PasswordAuthentication no
PermitRootLogin no

$ service sshd restart
```

### Linux Firewalls (rpm based)

1. Open a specific port.

   ```bash
   sudo firewall-cmd --zone=public --add-port=<port>/<protocol (tcp/udp)> --permanent
   ```

2. Reload Firewall

   ```bash
   sudo firewall-cmd --reload
   ```

   

