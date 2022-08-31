# LocalServerSetup
#### Versions
`Apache Version 2.4.46`

`MySQL Version 8.0.23`

`phpMyAdmin Version 5.1.0`

`php Version 7.4.15`

## Prerequisites

#### Requirements
`Visual C++ Redistributable for Visual Studio 2015-2019`

[Download `mysqld.pdb`](https://drive.google.com/file/d/1pJo-Yx_K5Q6Ee8adUhXpoJXM09vbVIT3/view?usp=sharing) and add to folder `..\Server\bin\mysql-8.0.23\bin` (Too large for GitHub)

#### Set the directory path
If your path is `C:\CphuxWebsite\Server` you can skip this section

Locate the file `..\Server\bin\Apache24\conf\httpd.conf`

Change the following lines to resemble your path
```
Define SRVROOT "C:/CphuxWebsite/Server/bin/Apache24"
DocumentRoot "C:/CphuxWebsite/Server/data/htdocs/"
<Directory "C:/CphuxWebsite/Server/data/htdocs/">
PHPIniDir "C:/CphuxWebsite/Server/bin/PHP"
LoadModule php7_module "C:/CphuxWebsite/Server/bin/php/php7apache2_4.dll"
```
Locate the file `..\Server\bin\mysql-8.0.23\my.ini`

Change the following line to resemble your path
```
datadir="C:/CphuxWebsite/Server/data/DB/data/"
```
Locate the file `..\Server\bin\php\php.ini`

Change the following lines to resemble your path
```
curl.cainfo = C:\CphuxWebsite\Server\certs\cacert.pem
```

#### Create Empty Folders
```
..\Server\data\DB\data
```

## Setup

#### MySQL
Open Command Prompt (as Admin) and run:
```
C:\CphuxWebsite\Server\bin\mysql-8.0.23\bin\mysqld --initialize-insecure --user=root
C:\CphuxWebsite\Server\bin\mysql-8.0.23\bin\mysqld --install
net start mysql
```

#### PHP
Add your php directory to PATH (system environment variables) default `C:\CphuxWebsite\Server\bin\php`

#### Apache Server
Open Command Prompt (as Admin) and run:
```
c:\CphuxWebsite\Server\bin\Apache24\bin\httpd.exe -k install
```

If you see a Firewall prompt, select ‘Allow access’.

#### Composer
Download and install [composer](https://getcomposer.org/download/)

## Testing

#### Apache
Open Command Prompt (as Admin) and run:
```
c:\CphuxWebsite\Server\bin\Apache24\bin\httpd.exe -k start
```
Open your browser, go to http://localhost/ you'll see something like this
`Index of/`

It means: Apache works
directory c:\CphuxWebsite\Server\data\htdocs\ is empty

#### phpMyAdmin
Open your browser, go to http://localhost/phpmyadmin/

Enter root as name, do not fill password.



## Delete server
Open Command Prompt (as Admin) and run: (Stop services and remove them from auto start)
```
C:\CphuxWebsite\Server\bin\Apache24\bin\httpd.exe -k stop
C:\CphuxWebsite\Server\bin\Apache24\bin\httpd.exe -k uninstall
net stop mysql
C:\CphuxWebsite\Server\bin\mysql-8.0.23\bin\mysqld --remove
```
Delete the folder C:\CphuxWebsite\Server\

Remove php from PATH (system environment variables)
