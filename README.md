I am Tousif Tasrik student of university of scholars
14th batch CSE. I am struggling to install the oracle21c express edition on the uubuntu.
I found the way to make it work. So, i am sharing the method. 
Any Queries you can get me in discord: tousiftasrik

---
# Installation of Oracle21C Express Edition in Ubuntu 22.04+

Pulling the image of Oracle21C express edition using docker 

So, first of all you need to install the docker . If you have the docker installed then it is great.

Follow the steps to setup the Oracle21C express edition 

Step-1:
```bash
sudo apt update
```

Step-2:
```bash
sudo apt install docker.io
```

Step-3:
```bash
sudo systemctl enable docker --now
```

Step-4: Pull the Oracle21C express edition docker image 
```bash
sudo docker pull gvenzl/oracle-xe:21-slim
```

Step-5:
Run the command below for the initial password setup and container setup
```bash 
sudo docker run -d \
  --name oracle-xe \
  -p 1521:1521 -p 5500:5500 \
  -e ORACLE_PASSWORD=<your-default-password> \
  gvenzl/oracle-xe:21-slim
```

Host-name: localhost
Port: 1521
Service Name: XEPDB1
User: system
Password: YourPassword123

`ORACLE_PASSWORD=<your-default-password>` carefully change the line here ORACLE_PASSWORD = set your password . it will be your default password. So, remember it.


### Check if the Oracle21C express edition installed or not

run this following command to know if it's installed or not

```bash 
sudo docker ps -a
```

Will show the exact same output as the image below

![enter image description here](https://i.imgur.com/ZNCxrU8.png)


### Start the Oracle21C express edition

```bash
sudo docker start oracle-xe-21c
```

### Stop the Oracle21C express edition

```bash
sudo docker stop oracle-xe-21c
```

## Using the SQL Plus 

```bash
sudo docker exec -it oracle-xe-21c sqlplus system/tousif@localhost/XEPDB1
```

After successfully ran the command you can see exact same image like the below

![enter image description here](https://i.imgur.com/ek4lcus.png)

### Important Note
1.You are currently logged in as the system user.
2.system/tousif@localhost/XEPDB1 change the tousif to your default password
3.Everytime you start the sql plus you need to execute the
--> sudo docker start oracle-xe-21c 
command

### Creating a new user

Here you don't need any kind of c## thing. You can create user without it.

```sql
CREATE USER tousiftasrik identified by tousif;
```

```sql
grant dba to tousiftasrik;
```

```sql
disconn;
```

```sql
conn;
```

```sql
Enter user-name: tousiftasrik
Enter password: tousif
```


Give it a star if you like it 🌟
Follow me : [Click me](https://github.com/lowercase-tousif)
Made by Tousif Tasrik 💖
