- Locate your private key file. MykeyFile.pem
- Run this command, if necessary, to ensure your key is not publicly viewable:
 
    ```chmod 400 aws_personal.pem```
1. Connect to your EC2 install through using ssh:
```ssh -i "MyKeyFile.pem" Ec2InstanceAdress```

When you already connected to your instance install postgresql. In my case I have installed postgresql 14
```
> sudo apt update
> sudo apt install postgresql-14
```

And then change the user password: 

```
> sudo -u postgres psql
ALTER USER postgres PASSWORD 'tu-contraseña';
```

2. Run the following command to check the firewall configuration:

```
sudo iptables -L
```

3. Ensure that the firewall allows incoming connections on the PostgreSQL port (5432).

4. If the firewall is blocking incoming connections, run the following command to open the port:

```
sudo iptables -A INPUT -p tcp --dport 5432 -j ACCEPT
```

5. Check the PostgresQL configuration 
You can know where is this file executing the following command: 
```
sudo -u postgres psql -c 'SHOW config_file'
```
In my case I'm using postgresql 14 so this file is in the path: 
```/etc/postgresql/14/main/postgresql.conf```

Then, find the line 

```#listen_addresses = 'localhost'``` 

and uncomment it (remove the # character at the beginning of the line).

Next, change the value of “listen_addresses” to “*”. This allows PostgreSQL to listen on all available IP addresses. Alternatively, you can specify a specific IP address or a range of IP addresses that are allowed to connect to the server.

6. Modify the ```pg_hba.conf``` file. 
In my case this file is in the path: 
```/etc/postgresql/14/main/pg_hba.conf```

and add the following: 

```
hosts    postgres    postgres    201.218.184.112/32    md5
```

- host: Indicates that the conection will be performed  using http
- postgres: database name
- postgresL The second postgres is the user name
- 201...: That address is the origin from which we are allowing the conection. You can use: "0.0.0.0/0" for allow conection from anywhere but this is less secure. 
- md5 Indicates password encription authentication will be used. 
7. Restart postgresql service:
```
sudo service postgresql restart
```

Finally Try to Connect to your Database allocated in your EC2 instance with the following parameters:
- Name: Any name you want to give
- Host: Public IP address of the Amazon EC2 instance
- Port: 5432
- Maintenance Database: postgres
- Username: postgres
- Password: Password you set for the postgres user in my case was: tu-contraseña