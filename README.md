# LinuxServerTesting_Assignment_HeroVired
Linux Server Testing

Tasks Detail:

## Task 1: System Monitoring Setup

Objective: Configure a monitoring system to ensure the development environment’s health, performance, and capacity planning.

### Scenario:

The development server is reporting intermittent performance issues.

New developers need visibility into system resource usage for their tasks.

System metrics must be consistently tracked for effective capacity planning.

### Requirements:

Installed and configured monitoring tools (htop or nmon) to monitor CPU, memory, and process usage.

Set up disk usage monitoring to track storage availability using df and du.

Implement process monitoring to identify resource-intensive applications.

Create a basic reporting structure (e.g., save outputs to a log file for review).

```
sudo apt update
sudo apt install htop
sudo apt install nmon
htop
nmon
df
du
```
<img width="941" height="1167" alt="image" src="https://github.com/user-attachments/assets/15e9bb1b-1c16-4c5f-8d23-2e87bbd21879" />



## Task 2: User Management and Access Control

Objective: Set up user accounts and configure secure access controls for the new developers.

### Scenario:

Two new developers, Sarah and Mike, require system access.

Each developer needs an isolated working directory to maintain security and confidentiality.

Security policies must ensure proper password management and access restrictions.

### Requirements:

Create user accounts for Sarah and Mike with secure passwords.

Set up dedicated directories: 

Sarah: /home/Sarah/workspace

Mike: /home/mike/workspace

Ensure only the respective users can access their directories using appropriate permissions.
```
sudo useradd -m Sarah
sudo useradd -m Mike
sudo passwd Sarah
sudo passed Mike
```

<img width="939" height="1148" alt="image" src="https://github.com/user-attachments/assets/cf0d18df-38fc-4e1b-b7a3-1fa55cf4e917" />


```
su - Sarah
nano private_Sarah.txt
cat private_Sarah.txt
su - Mike
nano private_Mike.txt
cat private_Mike.txt
```

<img width="738" height="1453" alt="image" src="https://github.com/user-attachments/assets/f43d433b-2762-4054-8264-86773b84c0bf" />


<img width="856" height="1278" alt="image" src="https://github.com/user-attachments/assets/8588e345-f961-4866-88d3-d53aae307400" />

```
su - Mike
nano Log
ls -alh
chmod 700 Log
ls -ld Log
su - Sarah
nano Log
chmod 700 Log
ls -alh
ls -ld Log
```

<img width="726" height="1259" alt="image" src="https://github.com/user-attachments/assets/53a7e627-14a1-46c6-ad2d-449fdf00167e" />


<img width="802" height="431" alt="image" src="https://github.com/user-attachments/assets/dad13e5d-ae24-4b1b-9f8e-347abf268b7e" />


<img width="722" height="344" alt="image" src="https://github.com/user-attachments/assets/c0428941-45da-4018-b172-0c3635965e4a" />


```
mkdir /backup/nginx
cat /etc/group | tail -10
sudo groupadd NginxWebServer
sudo usermod -aG NginxWebServer Mike
cat /etc/group | tail -10
sudo chown Mike:NginxWebServer nginx
```

<img width="817" height="975" alt="image" src="https://github.com/user-attachments/assets/0b8fa8bb-3c08-48d3-9d65-c84265fdc6c2" />


```
sudo groupadd ApacheWebServer
sudo usermod -aG ApacheWebServer Sarah
cat /etc/group |tail -5
```

<img width="800" height="122" alt="image" src="https://github.com/user-attachments/assets/504c2c4e-a47f-4cba-a2ac-0db76a771de7" />


<img width="630" height="167" alt="image" src="https://github.com/user-attachments/assets/125f0f27-68e9-4ca2-be40-7ba04b1ad706" />



## Implement a password policy to enforce expiration and complexity (e.g., passwords expire every 30 days).

```
sudo chage -M 30 Sarah
sudo chage -M 30 Mike
sudo nano /etc/security/pwquality.conf
sudo chage -W 7 Sarah
sudo chage -W 7 Mike
sudo chage -l Sarah
cat /etc/security/pwquality.conf
```

<img width="581" height="177" alt="image" src="https://github.com/user-attachments/assets/44d8b049-aba9-4933-964b-96a1b8735b88" />

<img width="911" height="448" alt="image" src="https://github.com/user-attachments/assets/7a4d8fef-8709-40e0-b3bf-635fa23377a2" />



## Task 3: Backup Configuration for Web Servers

Objective: Configure automated backups for Sarah’s Apache server and Mike’s Nginx server to ensure data integrity and recovery.

### Scenario:

## Sarah is responsible for managing an Apache web server.

```
sudo apt install apache2 -y
cd /etc/apache2
ls -alh
cd /var/www/html
ls -d /etc/apache2*
```

<img width="941" height="236" alt="image" src="https://github.com/user-attachments/assets/e8ffbbf4-3144-46d8-a71f-21bf2490d0dd" />


<img width="844" height="722" alt="image" src="https://github.com/user-attachments/assets/7140f9a8-3d0f-4669-896c-e31e334bfac0" />


<img width="725" height="67" alt="image" src="https://github.com/user-attachments/assets/6a63c742-573e-4cb2-a60d-80fb7096a900" />


```
sudo systemctl status apache2
ls -d /etc/apache2*
cd /etc/apache2
```

<img width="939" height="519" alt="image" src="https://github.com/user-attachments/assets/735e8d9f-87e3-4234-86da-e2681e97f7fc" />


<img width="858" height="542" alt="image" src="https://github.com/user-attachments/assets/7c26d953-9f5f-462a-bd3d-3a07480307ac" />


```
su - Sarah
cd Sarah
ls -alh
mkdir backup
cd backup
mkdir apache
ls -alh /etc | grep apache2
ls -alh /home/Sarah/backup/apache
su - Sarah
ls -alh /home/Sarah/backup/apache
```

<img width="941" height="1261" alt="image" src="https://github.com/user-attachments/assets/d38876b0-ec9b-4824-a727-86cb0249b104" />


<img width="975" height="311" alt="image" src="https://github.com/user-attachments/assets/c934ae61-5853-4045-b6a9-2ca1cc21f4e5" />


```
sudo apt install tar -y
tar --version
```

<img width="975" height="430" alt="image" src="https://github.com/user-attachments/assets/c43e4156-3506-4f4d-9c12-ed168da20598" />



## Mike is responsible for managing a Nginx web server. 

```
sudo apt update
sudo apt install nginx -y
nginx -v
sudo systemctl start nginx
```

<img width="941" height="975" alt="image" src="https://github.com/user-attachments/assets/6a4faacd-0483-4e73-9a7c-30bce87c9bee" />

<img width="916" height="509" alt="image" src="https://github.com/user-attachments/assets/067c1656-4473-4aa3-a3b7-91fef4f7e10d" />

<img width="975" height="592" alt="image" src="https://github.com/user-attachments/assets/12cd03c5-c8ec-4fa3-a2ea-ea479044496c" />

# error prompting apache cron job is already running and so stopping the apache server

```
nginx -v
apache2 -v
sudo systemctl stop apache2
sudo systemctl start nginx
sudo systemctl enable nginx
```

<img width="934" height="975" alt="image" src="https://github.com/user-attachments/assets/855b0b28-27ea-4a0e-bffd-95944a609436" />

```
sudo systemctl status nginx
cd /
ls -d /etc/nginx*
ls -d /var/www/html*
ls -d /var/log/nginx

```
<img width="975" height="763" alt="image" src="https://github.com/user-attachments/assets/3eecc4cb-471f-4bcc-8a09-8022ef852b71" />


Both servers require regular backups to a secure location for disaster recovery.

### Requirements:

Sarah and Mike need to automate backups for their respective web server configurations and document roots: 

# Sarah: Backup the Apache configuration (/etc/httpd/) and document root (/var/www/html/).

```
su - Sarah
tar -czvf /backup/apache/first.tar.gz /etc/apache2/
sudo mkdir -p /backup/apache
ls -ld /backup/apache
sudo chown -R Sarah:ApacheWebServer /backup/apache
ls -lh /backup/apache
tar -czvf /backup/apache/first_html.tar.gz /var/www/html/
```

<img width="975" height="581" alt="image" src="https://github.com/user-attachments/assets/2752e289-6c55-432d-8537-69cb81b0fbd3" />


<img width="709" height="975" alt="image" src="https://github.com/user-attachments/assets/b9a3b878-dfa1-4761-991a-049c04cd0aae" />


```
crontab -e
ls -lh /backup/apache
tar -czvf /backup/apache/first_html.tar.gz /var/www/html/
```

<img width="731" height="975" alt="image" src="https://github.com/user-attachments/assets/5941eb46-aa42-45e4-8671-74f3edc43bfb" />


<img width="975" height="331" alt="image" src="https://github.com/user-attachments/assets/a1751c60-2e0d-475b-85fe-ee716fc7dd4e" />


## cron job triggere for every 2 mins


<img width="975" height="583" alt="image" src="https://github.com/user-attachments/assets/3be07bcc-7361-410f-9e69-f31a675106fa" />



# Mike: Backup the Nginx configuration (/etc/nginx/) and document root (/usr/share/nginx/html/).

```
su - Mike
cd /backup/nginx
ls -alh
tar -cvzf /backup/nginx/first.tar.gz /etc/nginx/
tar -cvzf /backup/nginx/first_html.tar.gz /var/www/html
ls -alh
ls -alh /backup/nginx
ls -alh /backup/apache
```

<img width="717" height="975" alt="image" src="https://github.com/user-attachments/assets/61bf1a7d-3955-41c6-8325-0426252d7222" />


<img width="703" height="975" alt="image" src="https://github.com/user-attachments/assets/9cdf4028-a894-4fe5-bc2e-dab99585f2a7" />


<img width="798" height="975" alt="image" src="https://github.com/user-attachments/assets/72bdb284-fff7-417c-b579-b0ef733bfa32" />


```
crontab -e
systemstl status cron
systemstl status nginx
```


<img width="975" height="805" alt="image" src="https://github.com/user-attachments/assets/4cea6d4a-86d6-4b5e-ab8e-22a331260d0d" />


<img width="927" height="975" alt="image" src="https://github.com/user-attachments/assets/fff36cfa-cebc-426c-89b2-767e9d71dc53" />




# Schedule the backups to run every Tuesday at 12:00 AM using cron jobs.

```
# Tuesday at 12:00 AM  
0 0 * * 2 tar –czf /backup/nginx/config_bck_$(date +\%F_\%H_\%M).tar.gz /backup/nginx
0 0 * * 2 tar –czf /backup/nginx/html_bck_$(date +\%F_\%H_\%M).tar.gz /var/www/html

0 0 * * 2 tar –czf /backup/apache/config_bck_$(date +\%F_\%H_\%M).tar.gz /backup/apache
0 0 * * 2 tar –czf /backup/apache/html_bck_$(date +\%F_\%H_\%M).tar.gz /var/www/html

```

Save the backups as compressed files in /backups/ with filenames including the server name and date (e.g., apache_backup_YYYY-MM-DD.tar.gz).

Verify the backup integrity after each run by listing the contents of the compressed file.


### Expected Output:

Cron job configurations for Sarah and Mike.

Backup files are created in the /backups/ directory.

<img width="975" height="903" alt="image" src="https://github.com/user-attachments/assets/7cc50342-e8aa-4497-ad87-bde6fab755d8" />

A verification log showing the backup integrity.
