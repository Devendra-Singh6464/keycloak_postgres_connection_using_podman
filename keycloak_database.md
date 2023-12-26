# KeyCloak authentication over Postgresql database(SIP Creation) 

## [Keycloak](https://www.keycloak.org/):
   Open Source Identity, Access Management, authentication to applications and secure services with minimum effort.
No need to deal with storing users or authenticating users.  
Keycloak provides user federation, strong authentication, user management, fine-grained authorization.

## Get started with Keycloak on Podman

## [Podman](https://docs.podman.io/en/latest/):
   Podman is a daemonless, open source, Linux native tool designed to make it easy to find, run, build, share and deploy applications using Open Containers Initiative (OCI) Containers and Container Images. Podman provides a command line interface (CLI) familiar to anyone who has used the Docker Container Engine. Most users can simply alias Docker to Podman (alias docker=podman) without any problems.
   
## Prerequisite
```
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy
```

## Podman install
```
sudo apt-get update
```
```
deepak@deepak-Inspiron-3502:~$ sudo apt-get update
[sudo] password for deepak: 
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Ign:2 https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/4.4 InRelease      
Ign:3 https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 InRelease      
Hit:4 https://download.docker.com/linux/ubuntu jammy InRelease                 
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/4.4 Release        
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease   
Get:10 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]    
Get:11 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]     
Hit:12 https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 Release       
Hit:13 https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease
Hit:15 https://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease           
Get:16 http://ppa.launchpad.net/tektoncd/cli/ubuntu eoan InRelease [15.9 kB]   
Hit:17 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EFE0E0A2F2F60AA
Reading package lists... Done
W: https://repo.mongodb.org/apt/ubuntu/dists/jammy/mongodb-org/4.4/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/5.0/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease' doesn't support architecture 'i386'
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

```
sudo apt-get upgrade
```
```
deepak@deepak-Inspiron-3502:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gir1.2-totem-1.0 gir1.2-totemplparser-1.0 libcdio-cdda2 libcdio-paranoia2
  libcdio19 libnetplan0 libnfs13 librsync2
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  python3-update-manager update-manager update-manager-core
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
```  
sudo apt install podman
```
## output-
```
podman version 3.4.4
```

``` 
sudo apt-get update
```

Install  keycloak....

> Visit the Keycloak download page: [Keycloak Downloads](https://www.keycloak.org/downloads).   
> Click to TAR.GZ(sha1) and Download keycloak.


## Supported databases
The server has built-in support for different databases. You can query the available databases by viewing the expected values for the db configuration option. The following table lists the supported databases and their tested versions.

| Database           | Option value | Tested Version |
| -----------------  |  ----------- | -------------- |
|MariaDB Server      |  mariadb     |     10.11      |
|Microsoft SQL Server|    mssql     |     2022       |
|MySQL               |    mysql     |      8.0       |
|Oracle Database     |    Oracle    |     19.3       |
|PostgreSQL          |  postgres    |      16.1      |

 
## Install PostgreSQL on Ubuntu using the terminal

## [PostgresSQL](https://www.postgresql.org/docs/current/intro-whatis.html):
   PostgreSQL is an object-relational database management system (ORDBMS) based on POSTGRES, Version 4.2, developed at the University of California at Berkeley Computer Science Department.


## postgresql version--
```
deepak@deepak-Inspiron-3502:~$ psql --version
psql (PostgreSQL) 16.1 (Ubuntu 16.1-1.pgdg22.04+1)
```
```
sudo apt-get update
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo apt-get update
[sudo] password for deepak: 
Hit:1 http://packages.microsoft.com/repos/code stable InRelease
Ign:2 https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/4.4 InRelease      
Ign:3 https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 InRelease      
Hit:4 https://download.docker.com/linux/ubuntu jammy InRelease                 
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease                  
Hit:6 https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/4.4 Release        
Hit:7 http://in.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:8 https://ppa.launchpadcontent.net/deadsnakes/ppa/ubuntu jammy InRelease   
Get:10 http://in.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]    
Get:11 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]     
Hit:12 https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 Release       
Hit:13 https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/jammy pgadmin4 InRelease
Hit:15 https://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease           
Get:16 http://ppa.launchpad.net/tektoncd/cli/ubuntu eoan InRelease [15.9 kB]   
Hit:17 http://in.archive.ubuntu.com/ubuntu jammy-backports InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EFE0E0A2F2F60AA
Reading package lists... Done
W: https://repo.mongodb.org/apt/ubuntu/dists/jammy/mongodb-org/4.4/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/5.0/Release.gpg: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease' doesn't support architecture 'i386'
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
 Create the file repository configuration:
```
sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
```
 Import the repository signing key:
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```
 Update the package lists:
 
```
sudo apt install postgresql postgresql-contrib
```
```
sudo apt-get update
```

## Verify PostgreSQL Installation:
Once the installation is complete, PostgreSQL should start automatically. You can check the status of the PostgreSQL service to ensure it's running:

```
sudo systemctl status postgresql
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo systemctl status postgresql
[sudo] password for deepak: 
● postgresql.service - PostgreSQL RDBMS
     Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor pr>
     Active: active (exited) since Wed 2023-12-20 16:15:34 IST; 5 days ago
    Process: 1489 ExecStart=/bin/true (code=exited, status=0/SUCCESS)
   Main PID: 1489 (code=exited, status=0/SUCCESS)
        CPU: 1ms

Dec 20 16:15:34 deepak-Inspiron-3502 systemd[1]: Starting PostgreSQL RDBMS...
Dec 20 16:15:34 deepak-Inspiron-3502 systemd[1]: Finished PostgreSQL RDBMS.
lines 1-9/9 (END)
```
If postgresql.service not active so run this command

```
sudo systemctl start postgresql.service
```

Then: ctrl + z

To access PostgreSQL, you can switch to the default postgres user, which is automatically created during installation:

```
sudo -i -u postgres
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo -i -u postgres
postgres@deepak-Inspiron-3502:~$ 
```

Once you're logged in as the postgres user, access the PostgreSQL prompt by typing:
```
psql
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo -i -u postgres
postgres@deepak-Inspiron-3502:~$ psql
psql (16.1 (Ubuntu 16.1-1.pgdg22.04+1))
Type "help" for help.

postgres=#
```

To exit the PostgreSQL prompt:
```
\q
```
## output-
```
postgres=# \q
postgres@deepak-Inspiron-3502:~$
```

```
exit
```
## output-
```
postgres@deepak-Inspiron-3502:~$ exit
logout
deepak@deepak-Inspiron-3502:~$
```

## CONNECT KEYCLOAK TO POSTGRES DATABASE USING PODMAN:

1. First Step  —
- Create pod :
```
podman pod create --name deepak -p 5432:5432 -p 8080:8080
```
- Output:
```
podman pod create --name deepak -p 5432:5432 -p 8080:8080
<Container pod ID> 
```

Check running container status :
```
podman ps 
```
- OutPut:
```
CONTAINER ID  IMAGE                               COMMAND     CREATED     STATUS           PORTS                                           NAMES
```

Check container status:
```
podman ps -a
```
- Output:
```
podman ps -a
CONTAINER ID  IMAGE                               COMMAND     CREATED     STATUS           PORTS                                           NAMES
713a2756f29f  k8s.gcr.io/pause:3.5                            7 days ago  Up 24 hours ago  0.0.0.0:5432->5432/tcp, 0.0.0.0:8080->8080/tcp  82148f547b1b-infra
```

2. Second Step —
```
podman run --pod=deepak --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```
- Output:
  
```
podman run --pod=deepak --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
<container ID>
```

Inside the postgres terminal--
```
podman exec -it some-postgres bash
```
- Output:
```
podman exec -it some-postgres bash
root@deepak:/# 
```
```
psql -U postgres
```
- Output:
```
root@deepak:/# psql -U postgres
psql (16.1 (Debian 16.1-1.pgdg120+1))
Type "help" for help.

postgres=#
```


stop the postgres terminal
```
ctrl + z
```

- Create postgres database, try these queries:
```
CREATE DATABASE keycloak;
```
- Output:
```
postgres=# CREATE DATABASE keycloak;
CREATE DATABASE
postgres=# 
```
```
CREATE ROLE keycloak WITH LOGIN PASSWORD 'deepak';
```
- Output:
```
postgres=# CREATE ROLE keycloak WITH LOGIN PASSWORD 'deepak';
CREATE ROLE
postgres=# 
```
```
GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak;
```
- Output:
```
postgres=# GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak;
GRANT ALL
postgres=# 
```
```
ALTER DATABASE keycloak OWNER TO keycloak;
```
- Output:
```
postgres=# ALTER DATABASE keycloak OWNER TO keycloak;
ALTER DATABASE 
postgres=#   
```
Check postgres databases    
```
\l
```
- Output:
```
   Name    |  Owner   | Encoding | Locale Provider |  Collate   |   Ctype    | ICU Locale | ICU Rules |   Access privileges   
-----------+----------+----------+-----------------+------------+------------+------------+-----------+-----------------------
 keycloak  | keycloak | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | =Tc/keycloak         +
           |          |          |                 |            |            |            |           | keycloak=CTc/keycloak
 postgres  | postgres | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | 
 template0 | postgres | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | =c/postgres          +
           |          |          |                 |            |            |            |           | postgres=CTc/postgres
 template1 | postgres | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | =c/postgres          +
           |          |          |                 |            |            |            |           | postgres=CTc/postgres
(4 rows)
```

Exit the postgres terminal
```
\q
```
```
exit
```
 
3. THIRD STEP:  
``` 
podman run --pod=deepak -d --name keycloak -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin -e KC_DB=postgres -e KC_DB_URL_DATABASE=keycloak -e KC_DB_URL_HOST=0.0.0.0 -e KC_DB_URL_PORT=5432 -e KC_DB_USERNAME=keycloak -e KC_DB_PASSWORD=deepak docker.io/keycloak/keycloak:latest start-dev
```
- Output:
```
podman run --pod=deepak -d --name keycloak -e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin -e KC_DB=postgres -e KC_DB_URL_DATABASE=keycloak -e KC_DB_URL_HOST=0.0.0.0 -e KC_DB_URL_PORT=5432 -e KC_DB_USERNAME=keycloak -e KC_DB_PASSWORD=deepak docker.io/keycloak/keycloak:latest start-dev
Your <CONTAINER ID>
deepak@deepak-Inspiron-3502:~$
```
Check container status:
```
podman ps -a
```

Go to browser and write 
```
localhost:8080
```

4. FINAL STEP:
Going to root directory
```
podman exec -it some-postgres bash
```
- Output:
```
podman exec -it some-postgres bash
root@deepak:/# 
```
 ```
psql -U keycloak
```
- Output:
```
root@deepak:/# psql -U postgres
psql (16.1 (Debian 16.1-1.pgdg120+1))
Type "help" for help.

keycloak=#
```
```
\l
```
```
\dt
```

## [Welcome to Keycloak page](https://www.keycloak.org/getting-started/getting-started-podman):
Click on `Administrations Console`
 
Then i am go sign in page
>
  - username - `admin`  
  - password - `admin` 
> 

# Create a realm

A realm in Keycloak is equivalent to a tenant. Each realm allows an administrator to create isolated groups of applications and users. Initially, Keycloak includes a single realm, called master. Use this realm only for managing Keycloak and not for managing any applications.

## Use these steps to create the first realm.
>
1. Open the Keycloak Admin Console.  
2. Click the word master in the top-left corner, then click Create Realm.  
3. Enter myrealm in the Realm name field.  
4. Click Create.
>

## Create a user  
Initially, the realm has no users. Use these steps to create a user:
1. Open the Keycloak Admin Console.
2. Click the word master in the top-left corner, then click myrealm.
3. Click Users in the left-hand menu.
4. Click Add user.
5. Fill in the form with the following values:
   -  Username: `any username`
   -  First name: `any first name`
   -  Last name: `any last name`
6. Click Create.


This user needs a password to log in. To set the initial password:
1. Click Credentials at the top of the page.
2. Fill in the Set password form with a password.
3. Toggle Temporary to Off so that the user does not need to update this password at the first login.

## Log in to the Account Console
You can now log in to the Account Console to verify this user is configured correctly.
1. Open the Keycloak Account Console.
2. Log in with Deepak and the password you created earlier.


    As a user in the Account Console, you can manage your account including modifying your profile, adding two-factor authentication, and including identity provider a


## Secure the first application
To secure the first application, you start by registering the application with your Keycloak instance:

1. Open the Keycloak Admin Console.
2. Click the word master in the top-left corner, then click myrealm.
3. Click Clients.
4. Click Create client
5. Fill in the form with the following values:
   -  Client type: `OpenID Connect`
   - Client ID:   `myclient`
6. Click Next
7. Confirm that Standard flow is enabled.
8. Click Next.
9. Click Save.

From a terminal, enter the following command to start Keycloak:-

> This command starts Keycloak exposed on the local port 8080 and creates an initial admin user with the username admin and password admin.

I execute this command then i am go browser and write `localhost:8080`(localhost:port)
