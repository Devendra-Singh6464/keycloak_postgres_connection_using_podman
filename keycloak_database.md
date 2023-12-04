# KeyCloak authentication over multiple database(SIP Creation) 

## [Keycloak](https://www.keycloak.org/):
   Open Source Identity, Access Management, authentication to applications and secure services with minimum effort.
No need to deal with storing users or authenticating users.  
Keycloak provides user federation, strong authentication, user management, fine-grained authorization.

## Get started with Keycloak on Podman

## [Podman](https://docs.podman.io/en/latest/):
   Podman is a daemonless, open source, Linux native tool designed to make it easy to find, run, build, share and deploy applications using Open Containers Initiative (OCI) Containers and Container Images. Podman provides a command line interface (CLI) familiar to anyone who has used the Docker Container Engine. Most users can simply alias Docker to Podman (alias docker=podman) without any problems.


## Podman install
```sh
sudo apt-get update
```
```
sudo apt-get upgrade
```
```  
sudo apt install podman
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
   

```
sudo  apt update
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

To access PostgreSQL, you can switch to the default postgres user, which is automatically created during installation:

```
sudo -i -u postgres
```
Once you're logged in as the postgres user, access the PostgreSQL prompt by typing:
```
psql
```
To exit the PostgreSQL prompt:
```
\q
```
```
exit
```


## CONNECT KEYCLOAK TO POSTGRES DATABASE USING PODMAN:

1. First Step  —
- Create pod :
```
podman pod create --name deepak -p 5432:5432 -p 8080:8080
```
Check running container status :
```
podman ps 
```
Check container status:
```
podman ps -a
```
2. Second Step —
```
podman run --pod=deepak --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

Inside the postgres terminal--
```
podman exec -it some-postgres bash
```
```
psql -U postgres
```

Check postgres default databases    
```
\l
```
stop the terminal
```
ctrl + z
```
```
psql -U postgres
```
- If you want to create postgres database, try these queries:
```
CREATE DATABASE keycloak;
```
```
CREATE ROLE keycloak WITH LOGIN PASSWORD 'deepak';
```
```
GRANT ALL PRIVILEGES ON DATABASE keycloak TO keycloak;
```
```
ALTER DATABASE keycloak OWNER TO keycloak;
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

4. FINAL STEP:
Going to root directory
```
podman exec -it some-postgres bash
```
 ```
psql -U keycloak
```
```
\l
```
Go to browser and write 
```
localhost:8080
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
