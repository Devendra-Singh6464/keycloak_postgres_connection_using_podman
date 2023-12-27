# KeyCloak authentication over Postgresql database(SIP Creation) 

## [Keycloak](https://www.keycloak.org/):
   Open Source Identity, Access Management, authentication to applications and secure services with minimum effort.
No need to deal with storing users or authenticating users.  
Keycloak provides user federation, strong authentication, user management, fine-grained authorization.

## Get started with Keycloak on Podman

## [Podman](https://docs.podman.io/en/latest/):
   Podman is a tool used to create, manage, and run containers. It allows users to package applications and their dependencies into isolated environments, making it easier to develop, deploy, and manage software.
   
## Prerequisite

Distributor ID:	Ubuntu  
Description:	Ubuntu 22.04.3 LTS  
Release:	22.04  
Codename:	jammy  

### postgresql version-

psql (PostgreSQL) 16.1 (Ubuntu 16.1-1.pgdg22.04+1)

### podman version-

podman version 3.4.4

## Podman install

## Command-
```
sudo apt-get update
```
## Output-
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

## Command -
```
sudo apt-get upgrade
```
## output-
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
## Command -
```  
sudo apt install podman
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo apt install podman
[sudo] password for deepak: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
podman is already the newest version (3.4.4+ds1-1ubuntu1.22.04.2).
The following packages were automatically installed and are no longer required:
  gir1.2-totem-1.0 gir1.2-totemplparser-1.0 libcdio-cdda2 libcdio-paranoia2
  libcdio19 libnetplan0 libnfs13 librsync2
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
I'm already install podman ,so I got this output. If you don't have podman so it will be installed.

## Command- 
```
Podman -v
```
## Output- 
```
podman version 3.4.4
```
## Command-
``` 
sudo apt-get update
```

Install  keycloak....

> Visit the Keycloak download page: [Keycloak Downloads](https://www.keycloak.org/downloads).   
> Click to TAR.GZ(sha1) and Download keycloak.
 
## After installation keycloak TAR.GZ(sha1) file unzip this file 
Go, files > Download > right click (on keycloak TAR.GZ(sha1) file and) > click Exteact Here


## Supported databases
The server has built-in support for different databases. You can query the available databases by viewing the expected values for the db configuration option. The following table lists the supported databases and their tested versions.

| Database           | Option value | Tested Version |
| -----------------  |  ----------- | -------------- |
|PostgreSQL          |  postgres    |      16.1      |

 
## Install PostgreSQL on Ubuntu using the terminal

## [PostgresSQL](https://www.postgresql.org/docs/current/intro-whatis.html):
   PostgreSQL is an object-relational database management system (ORDBMS) based on POSTGRES, Version 4.2, developed at the University of California at Berkeley Computer Science Department.


## Command-
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

 ## Command-
```
sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
```
 Import the repository signing key:

 ## Command -
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```
 Update the package lists:

 ## Command -
```
sudo apt install postgresql postgresql-contrib
```
## Another install postgresql source-

[Postgresql install hint source in ubuntu](https://www.commandprompt.com/education/how-to-install-postgresql-database-on-ubuntu/)
## Command -
```
sudo apt-get update
```

## Verify PostgreSQL Installation:
Once the installation is complete, PostgreSQL should start automatically. You can check the status of the PostgreSQL service to ensure it's running:


## postgresql version--
Postgresql version-
## Command -
```
psql --version
```
## Output-
```
deepak@deepak-Inspiron-3502:~$ psql --version
psql (PostgreSQL) 16.1 (Ubuntu 16.1-1.pgdg22.04+1)
```

if you follow all command but your postgres version not 16.1 so follow this -  
Click the link then click, v16.1 then postgresql-16.1.tar.bz2    

## After installation keycloak TAR.GZ(sha1) file unzip this file 
Go, files > Download > right click (on postgres TAR.GZ(sha1) file and) > click Exteact Here


[postgres](https://www.postgresql.org/ftp/source/)



## Command -
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
## Command -
```
sudo systemctl start postgresql.service
```

Then: ctrl + z

To access PostgreSQL, you can switch to the default postgres user, which is automatically created during installation:

## Command -
```
sudo -i -u postgres
```
## output-
```
deepak@deepak-Inspiron-3502:~$ sudo -i -u postgres
postgres@deepak-Inspiron-3502:~$ 
```

Once you're logged in as the postgres user, access the PostgreSQL prompt by typing:
## Command -
```
psql
```
## output-
```
postgres@deepak-Inspiron-3502:~$ psql
psql (16.1 (Ubuntu 16.1-1.pgdg22.04+1))
Type "help" for help.

postgres=#
```

To exit the PostgreSQL prompt:
## Command -
```
\q
```
## output-

```
postgres=# \q
postgres@deepak-Inspiron-3502:~$
```
or 

## Command -
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
   
- If you don't have postgres and keycloak images on your server,pull them first:
```
podman pull docker.io/library/postgres
```
### Output-
```
deepak@deepak-Inspiron-3502:~$ podman pull docker.io/library/postgres  
Trying to pull docker.io/library/postgres:latest...
Getting image source signatures
Copying blob 85f7bca87921 done  
Copying blob af107e978371 done  
Copying blob 644cfda281a1 done  
Copying blob 1a83ab26a0f0 done  
Copying blob 12bab27fafd3 done  
Copying blob 948f1cf08e62 done  
Copying blob 03299695f2b9 done  
Copying blob 6e36bf1505f3 done  
Copying blob 83b026289c5c done  
Copying blob a35465a6a76a done  
Copying blob c158e73dda41 done  
Copying blob 264ae53c0064 done  
Copying blob 2e3c2c5fbb6d done  
Copying blob 08c5357f23b5 done  
Copying config 398d34d3cc done  
Writing manifest to image destination
Storing signatures
398d34d3cc5e29c86077dbf95ad9da223c3a2d0227d12012087da9d468da9d5b
```

```
podman pull quay.io/keycloak/keycloak
```
### Output-
```
deepak@deepak-Inspiron-3502:~$ podman pull quay.io/keycloak/keycloak
Trying to pull quay.io/keycloak/keycloak:latest...
Getting image source signatures
Copying blob f72461870632 done  
Copying blob 65b190d0545b done  
Copying blob 7e11c5ba1fd2 done  
Copying blob a4503341e3e7 done  
Copying config 33825b7d2d done  
Writing manifest to image destination
Storing signatures
33825b7d2d9e317215939851e10b1e184b4f876de1b5b25cf448e425c47802bd
```

- Create pod :
## Command - 
```
podman pod create --name deepak -p 5432:5432 -p 8080:8080
```
- Output:
```
podman pod create --name deepak -p 5432:5432 -p 8080:8080
<Container pod ID> 
```

Check running container status :
## Command -
```
podman ps 
```
- OutPut:
```
CONTAINER ID  IMAGE                               COMMAND     CREATED     STATUS           PORTS                                           NAMES
```

Check container status:
## Command -
```
podman ps -a
```
- Output:
```
podman ps -a
CONTAINER ID  IMAGE                               COMMAND     CREATED     STATUS           PORTS                                           NAMES
713a2756f29f  k8s.gcr.io/pause:3.5                            7 days ago  Up 24 hours ago  0.0.0.0:5432->5432/tcp, 0.0.0.0:8080->8080/tcp  82148f547b1b-infra
```

if your podman pod status not up so please start podman pod

### command-

podman pod start <podman_names>
```
podman pod start 82148
```
or
```
podman pod start --latest
```

2. Second Step —
## Command -
```
podman run --pod=deepak --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

- Output:
  
```
podman run --pod=deepak --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
<container ID>
```

Inside the postgres terminal--
 ## Command -
```
podman exec -it some-postgres bash
```
- Output:
```
podman exec -it some-postgres bash
root@deepak:/# 
```
### command-
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
## Query run-
```
CREATE DATABASE keycloak;
```
- Output:
```
postgres=# CREATE DATABASE keycloak;
CREATE DATABASE
postgres=# 
```
## Query run-
```
CREATE ROLE keycloak WITH LOGIN PASSWORD 'deepak';
```
- Output:
```
postgres=# CREATE ROLE keycloak WITH LOGIN PASSWORD 'deepak';
CREATE ROLE
postgres=# 
```
## Query run-
```
GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak;
```
- Output:
```
postgres=# GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak;
GRANT ALL
postgres=# 
```
## Query run-
```
ALTER DATABASE keycloak OWNER TO keycloak;
```
- Output:
```
postgres=# ALTER DATABASE keycloak OWNER TO keycloak;
ALTER DATABASE 
postgres=#   
```
Check postgres databases-
### command-
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
### command-
```
\q
```
### command-
```
exit
```
 
3. THIRD STEP:
     
## Command -
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
## Command -
```
podman ps -a
```

Go to browser and write 
```
localhost:8080
```

4. FINAL STEP:
Going to root directory
## Command -
```
podman exec -it some-postgres bash
```
- Output:
```
podman exec -it some-postgres bash
root@deepak:/# 
```
## Command -
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
### Command-
```
\dt
```
- Output:
![image](https://github.com/Devendra-Singh6464/keycloak_postgres_connection_using_podman/assets/136952464/a41c732a-7fe7-4960-996c-af949b2375e4)

```  
keycloak=> \dt
                     List of relations
 Schema |             Name              | Type  |  Owner   
--------+-------------------------------+-------+----------
 public | admin_event_entity            | table | keycloak
 public | associated_policy             | table | keycloak
 public | authentication_execution      | table | keycloak
 public | authentication_flow           | table | keycloak
 public | authenticator_config          | table | keycloak
 public | authenticator_config_entry    | table | keycloak
 public | broker_link                   | table | keycloak
 public | client                        | table | keycloak
 public | client_attributes             | table | keycloak
 public | client_auth_flow_bindings     | table | keycloak
 public | client_initial_access         | table | keycloak
 public | client_node_registrations     | table | keycloak
 public | client_scope                  | table | keycloak
 public | client_scope_attributes       | table | keycloak
 public | client_scope_client           | table | keycloak
 public | client_scope_role_mapping     | table | keycloak
 public | client_session                | table | keycloak
 public | client_session_auth_status    | table | keycloak
 public | client_session_note           | table | keycloak
 public | client_session_prot_mapper    | table | keycloak
 public | client_session_role           | table | keycloak
 public | client_user_session_note      | table | keycloak
 public | component                     | table | keycloak
 public | component_config              | table | keycloak
 public | composite_role                | table | keycloak
 public | credential                    | table | keycloak
 public | databasechangelog             | table | keycloak
 public | databasechangeloglock         | table | keycloak
 public | default_client_scope          | table | keycloak
 public | event_entity                  | table | keycloak
 public | fed_user_attribute            | table | keycloak
 public | fed_user_consent              | table | keycloak
 public | fed_user_consent_cl_scope     | table | keycloak
 public | fed_user_credential           | table | keycloak
 public | fed_user_group_membership     | table | keycloak
 public | fed_user_required_action      | table | keycloak
 public | fed_user_role_mapping         | table | keycloak
 public | federated_identity            | table | keycloak
 public | federated_user                | table | keycloak
 public | group_attribute               | table | keycloak
 public | group_role_mapping            | table | keycloak
 public | identity_provider             | table | keycloak
 public | identity_provider_config      | table | keycloak
 public | identity_provider_mapper      | table | keycloak
 public | idp_mapper_config             | table | keycloak
 public | keycloak_group                | table | keycloak
 public | keycloak_role                 | table | keycloak
 public | migration_model               | table | keycloak
 public | offline_client_session        | table | keycloak
 public | offline_user_session          | table | keycloak
 public | policy_config                 | table | keycloak
 public | protocol_mapper               | table | keycloak
 public | protocol_mapper_config        | table | keycloak
 public | realm                         | table | keycloak
 public | realm_attribute               | table | keycloak
 public | realm_default_groups          | table | keycloak
 public | realm_enabled_event_types     | table | keycloak
 --More--
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
    
Keycloak myrealm Home page!
![image](https://github.com/Devendra-Singh6464/keycloak_postgres_connection_using_podman/assets/136952464/302fedf1-8fe5-4bb6-9c2b-673796e38cb6)



From a terminal, enter the following command to start Keycloak:-

> This command starts Keycloak exposed on the local port 8080 and creates an initial admin user with the username admin and password admin.

I execute this command then i am go browser and write `localhost:8080`(localhost:port)
