# webapp

## Cloud Native Web Application

## Getting Started

### Prerequisites

- [Java](https://www.java.com/) installed on your machine
- [Maven](https://maven.apache.org/) installed on your machine

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/cloudapp6225/webapp.git

2. Install postgresql

    ```bash
    sudo apt install -y postgresql postgresql-contrib

3. Navigate to the project

   ```bash
   cd webapp/

4. Build project

    ```bash
    mvn clean install

5.  Run Locally

    ```bash
    mvn spring-boot:run

## Development

### User Schema

```
{
    id:	string($uuid)
    first_name: string
    last_name: string
    password: string($password)
    username: string($email)
    account_created: string($date-time)
    account_updated: string($date-time)
}
```
### Testing

- [Postman client](https://www.postman.com/) install on your machine

### API Endpoints

### `POST http://localhost:8080/v1/user`
Create a new User
```
{
  "first_name": "Jane",
  "last_name": "Doe",
  "password": "skdjfhskdfjhg",
  "username": "jane.doe@example.com"
}
```
### Authenticated Endpoints
### `GET http://localhost:8080/v1/user/self`
Get a user by passing username and password in basic authentication header.

### `PUT http://localhost:8080/v1/user/self`
Update user details by providing authentication headers.

## Demo on Digital Ocean

1. Create a droplet on digital ocean
```
$ ssh-keygen
```
2. save as below
```
$ /Users/vinaykumarchelpuri/.ssh/digitalocean 
```
3. passpharase git
```
$ cd .ssh
$ cat digitalocean.pub
```
4. copy it and paste in digital ocean
5. ssh into vm using public ssh key
```
$ ssh -i ~/.ssh/digitalocean [root@](mailto:root@147.182.240.7)164.92.99.221
$ cd .ssh/
```
6. change permission on private key
```
$ chmod 600 .ssh/digitaloceanssh into vm now
```
## Recommended Commands in centOS
```
$ sudo dnf install vim -y

$ sudo yum install unzip -y

$ sudo yum install java-17-openjdk-devel -y

$ sudo dnf install maven-openjdk17 -y

$ sudo yum install postgresql-server postgresql-contrib -y

$ sudo postgresql-setup initdb

$ sudo systemctl start postgresql

$ sudo systemctl enable postgresql

$ sudo -u postgres psql

CREATE DATABASE app_db;
\l
\password postgres
CREATE USER web_app with PASSWORD 'XXXXXXX';
ALTER USER web_app WITH SUPERUSER;

$ vim  /var/lib/pgsql/data/pg_hba.conf —> md5 for all connections

$ vim /var/lib/pgsql/data/postgresql.conf —> listen_address = ‘*’ if it doesn’t work

$ sudo systemctl restart postgresql

$ scp -i .ssh/digitalocean ~/Downloads/vinaykumar_chelpuri_002207627_02.zip root@164.92.99.221:/tmp

$ unzip vinaykumar_chelpuri_002207627_02.zip
$ cd vinaykumar_chelpuri_002207627_02
$ cd webapp
$ mvn clean install
$ mvn spring-boot:run
$ ps
$ kill pid
```

## License

MIT License

Copyright (c) 2024 cloudapp6225

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
