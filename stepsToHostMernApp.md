# Connect to Vps Server

<code>ssh root@ipAddress</code>

# update and Upgrade

<code> sudo apt update</code>
<code>sudo apt upgrade</code>

# insatlling Node.js using Nvm

<code>curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash</code>

check if nvm is installed or not by running the following command
<code>nvm --version</code>
now, Restart the terminal

Installing node
<code>nvm install --lts</code>

# installing mongodb

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/#std-label-install-mdb-community-ubuntu

1. <code>curl -fsSL https://pgp.mongodb.com/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
</code>

2. <code>echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list</code>

3. <code>sudo apt-get update</code>
4. <code>sudo apt-get install -y mongodb-org</code>

5. Check the status of mongodb-org
   <code>sudo systemctl status mongod</code>

6. activate the mongodb-org
   <code>sudo systemctl start mongod</code>
   <code>sudo enable mongod</code>

# installing the git

1. Installing the git
   <code>sudo apt install git</code>

2. Installing git cli
   <code>sudo apt install gh</code>

3. how to login to github
   <code>gh auth login</code>

4. cloning the repository
   <code>git clone <github-repo></code>
   <code>cd <your-project-folder> </code>

# setup the backend

1. installing the node modules

   <code>npm install</code>
   <code>npm i -g pnpm</code>
   <code>pnpm i</code>

2. Setting up the environment variables

   1. adding file .env

   <code> nano .env</code>

   2. show the content of .env file
      <code>cat .env</code>

# installing process manger pm2

1. installing

   <code>npm i -g pm2</code>

2. starting backend server

   <code>pm2 start npm --name "test_server" -- start --watch</code>

3. Check logs for server

<code>pm2 logs test_server</code>
curl -o http://localhost:8080

# setting ufw

1. sudo apt update
2. sudo apt install ufw
3. sudo systemctl start ufw
4. sudo systemctl enable ufw
5. sudo ufw allow ssh
6. sudo ufw allow http
7. sudo ufw allow https

# setting up nginx server

1.  sudo apt install nginx
2.  cd /etc/nginx
3.  cd sites-enabled
4.  ls
5.  cat default.conf
6.  rm default.conf
7.  cd /etc/nginx/sites-available
8.  nano your_ip.config or domain.config
9.  paste the code in this file
    <code>
    server{
       listen 80;
       listen [::]:80;
    server_name your_domain.com www.your_domain.com;
    root /var/www/html; 
    index index.html index.htm;
    
    location / {
    
proxy_pass http://localhost:8080; # or which other port your app runs on
proxy_http_version 1.1;
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection 'upgrade';
proxy_set_header Host $host;
proxy_cache_bypass $http_upgrade;
} </code>

# for not serving statically
server{
listen 80;
root /root/your_buildfolder;

location / {
try_files $uri $uri/ =404;
}
}


for apache2
<code>
<VirtualHost *:80>
    ServerName your_domain.com
    ServerAlias www.your_domain.com

    DocumentRoot /var/www/html

    <Directory /var/www/html>
        Options -Indexes
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    ProxyPass /api http://localhost:8080/
    ProxyPassReverse /api http://localhost:8080/
   <Location/>
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/
    </Location>
</VirtualHost>

</code>
11. check all files are good
    <code>sudo nginx -t</code>
12. making symbolic link
go to /etc/nginx/sites-enabled
<code>
   
   ln -s ../sites-available/website.com.conf
</code>

13. systemctl restart nginx

# SSL Certificate

1. sudo apt-get install certbot python3-certbot-nginx
2. sudo certbot --nginx -d mywebsite.com -d www.mywebsite.com
3. 
