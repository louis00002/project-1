# project-1
                INSTALLING APACHE 
 
 
 Apache HTTP Server is the most widely used web server software. Developed and maintained by Apache Software Foundation, Apache is an open source software available for free. It runs on 67% of all webservers in the world. It is fast, reliable, and secure. It can be highly customized to meet the needs of many different environments by using extensions and modules. Most WordPress hosting providers use Apache as their web server software. However, websites and other applications can run on other web server software as well. Such as Nginx, Microsoft’s IIS, etc.

The Apache web server is among the most popular web servers in the world. It’s well documented, has an active community of users, and has been in wide use for much of the history of the web, which makes it a great default choice for hosting a website.

I will be Installing Apache using Ubuntu’s package manager ‘apt’:

After I had SSH into the AWS server through the terminal using the following commands 
 
  ssh -i "ubuntufromMac.pem" ubuntu@ec2-34-239-122-184.compute-1.amazonaws.com
  
  .ls
  
  .cd Downloads
  
  .ls
  
   ssh -i "ubuntufromMac.pem" ubuntu@ec2-34-239-122-184.compute-1.amazonaws.com
   
 When I was safely connected to the EC2 instance, i proceeded with the following commands to download APACHE2 WEB SERVER SOFTWARE. 
   
 First thing I had to do was to update a list of packages in package manager using the following command. 
 
         <sudo apt update>
         
Next, I ran apache2 package installation using the following command. 

       <sudo apt install apache2>

To verify that apache2 is running as a Service in my OS, i ran the following coomand

       <sudo systemctl status apache2>

this is what it looked like when Apache2 was up and running

<img width="1026" alt="Screenshot 2022-04-13 at 23 15 36" src="https://user-images.githubusercontent.com/103360590/163288448-ee27c8eb-d360-4e96-bbcb-0a1f4e845f9d.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 19 55" src="https://user-images.githubusercontent.com/103360590/163288485-a6afd98b-db38-45c3-942c-b9c807a3c6f7.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 47 38" src="https://user-images.githubusercontent.com/103360590/163288534-840bddfa-9e90-48b5-834e-62c3d7492f3c.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 48 33" src="https://user-images.githubusercontent.com/103360590/163288618-9cabef8b-bf4a-4c5b-8191-de54731ac6bc.png">

Before i could receive any traffic from the Web Server, i neeed to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet.

i then had to, check how I can access it locally in my Ubuntu shell, by running the conmmand: 

 curl http://localhost:80 or  curl http://127.0.0.1:80

I then had to test how my Apache HTTP server can respond to requests from the Internet by browing 
http://100.24.2.15:80 on my web browser which gave me the following page.

<img width="808" alt="Screenshot 2022-04-14 at 01 09 21" src="https://user-images.githubusercontent.com/103360590/163289429-0c010b2e-c817-46f4-bba7-c6adb7cbd66a.png">.

STEP 2 — INSTALLING MYSQL

Now that i have a web server up and running, i needed to install a Database Management System (DBMS) to be able to store and manage data for my site in a relational database. 

the DBMS that i will be installing is called MySQL which is a popular relational database management system used within PHP environments, so i will use it in my project.

So to install MYSQL, i had to use apt and run the command <sudo apt install mysql-server>
see picture of how it looked like after installation. 
 
 <img width="808" alt="Screenshot 2022-04-15 at 09 01 54" src="https://user-images.githubusercontent.com/103360590/163551880-c974a063-2ff8-4e82-9c9c-3f99a98c7147.png">
<img width="808" alt="Screenshot 2022-04-15 at 09 02 39" src="https://user-images.githubusercontent.com/103360590/163552670-19a56e99-dcfe-419b-bf72-bf00294c703e.png">
 
After installation is finished, it’s recommended that i run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lock down access to your database system. I Started the interactive script by running the comnmand
 
        <sudo mysql_secure_installation>.
 
 when i ran that command, it prompted me to VALIDATE PASSWORD PLUGIN. which i agreed by pressing y for yes. 
 
it then asked me to select a level of password validation
There are three levels of password validation policy: low, medium, strong. i picked the stong password.
 
MY server then ask me to select and confirm a password for the MySQL root user which i did. i then press yes for the rest of the questions. 
 
 After the installation, i had to test if i"m able to log in to the MySQL console by typing: 
         
         <sudo mysql>
 
 it connect to the MySQL server as the administrative database user root, which is inferred by the use of sudo when running this command. 
 
 see pictures of how the sudo mysql_secure_installation looked like.<img width="808" alt="Screenshot 2022-04-15 at 09 21 11" src="https://user-images.githubusercontent.com/103360590/163559624-14821043-9d58-4bdb-b790-d9633528ee04.png">
 <img width="808" alt="Screenshot 2022-04-15 at 09 23 36" src="https://user-images.githubusercontent.com/103360590/163559714-56370159-4fcd-4a3f-8779-ba9497de9e76.png">

 
 STEP 3 — INSTALLING PHP
 
 Apache is installed to serve my content and MySQL installed to store and manage my data. PHP is the component of our setup that will process code to display dynamic content to the end user. In addition to the php package, I will need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. I will also need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies. 

 so to install these 3 packages at once, i had to run the following command.
 
 <sudo apt install php libapache2-mod-php php-mysql>
 
 ones it finnised installing, I ran the command <php -v> to confirm the PHP version: as seen bellow<img width="808" alt="Screenshot 2022-04-15 at 09 54 50" src="https://user-images.githubusercontent.com/103360590/163562235-6a278278-8265-4c4d-8fc0-c04caef71d54.png">
<img width="808" alt="Screenshot 2022-04-15 at 10 58 25" src="https://user-images.githubusercontent.com/103360590/163562436-6d13fae9-31ab-471c-8832-a43475e01fd3.png">
 
I have now fully installed 
 
Linux (Ubuntu)
Apache HTTP Server
MySQL
PHP

 To test my setup with a PHP script, it’s best I set up a proper Apache Virtual Host to hold my website’s files and folders. Virtual host will allows me to have multiple websites located on a single machine and users of the websites will not even notice it.
 
 
 STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
 
 In this project, i will be seting up a domain called projectlamp.
 
 Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory. I will leave this configuration as it is and will add my own directory text next to the default one.
 
To Create the directory for projectlamp, i had to use ‘mkdir’ command as follows:
 
 <sudo mkdir /var/www/projectlamp>
  After creating the directory, i had to assign ownership of the directory with my current system user: by running the following command.
  
  <sudo chown -R $USER:$USER /var/www/projectlamp>
   
 I then had to create and open a new configuration file in Apache’s sites-available directory using my preferred command-line editor. Here, I’ll be using vi or vim (They are the same by the way): I did this by running the following commdand. 
   
   <sudo vi /etc/apache2/sites-available/projectlamp.conf>
    
  This then created a new blank file. I Pasted the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:
    
 <VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
  
    I then press esc. then : then wq. and pressed enter to save and close the file. 

 I used the ls command to show the new file in the sites-available directory as follows
    
    <sudo ls /etc/apache2/sites-available>
     
  With this VirtualHost configuration, i am telling Apache to serve projectlamp using /var/www/projectlampl as its web root directory. If i wanted to test Apache without a domain name, i can remove or comment out the options ServerName and ServerAlias by adding a # character in the beginning of each option’s lines. Adding the # character there will tell the program to skip processing the instructions on those lines.
     
 I then used the a2ensite command to enable the new virtual host:
     
     <sudo a2ensite projectlamp>
      
I then disable the default website that comes installed with Apache. This is required if I'm not using a custom domain name, because in this case Apache’s default configuration would overwrite my virtual host. To disable Apache’s default website I used a2dissite command , type:
      
      <sudo a2dissite 000-default>
       
To make sure my configuration file didnt  contain syntax errors,i ran the following command:
       
       <sudo apache2ctl configtest>

I then had to reload Apache so these changes take effect by typing the folowing command:
        
        <sudo systemctl reload apache2>
         
My new website is now active, but the web root /var/www/projectlamp is still empty. So I Created an index.html file in that location so that I could test that the virtual host works as expected: I did this by running the following command:
         
    sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html
         
All this steps can bee seen on the screenshot bellow
         
<img width="1438" alt="Screenshot 2022-04-15 at 15 46 18" src="https://user-images.githubusercontent.com/103360590/163585111-cb40a049-24e5-4384-8173-8d8979d28f20.png">


 I then went to my browser and tried to open my website URL using the following IP address which worked just fine. 
      http://54.211.146.31:80
         
         
    STEP 5 — ENABLE PHP ON THE WEBSITE
         
         
 With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. This is useful for setting up maintenance pages in PHP applications, by creating a temporary index.html file containing an informative message to visitors. Because this page will take precedence over the index.php page, it will then become the landing page for the application. Once maintenance is over, the index.html is renamed or removed from the document root, bringing back the regular application page.
         
I had to change this behavior, by editing the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive: this was done by running the following command.
         
         <sudo vim /etc/apache2/mods-enabled/dir.conf>
          
I then pasted and saved the following text. 
          
<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
         
I then reloaded Apache by running the following command again. 
          
          <sudo systemctl reload apache2>
           
 But when i reloaded apache this time, it gave me the following failed message. 
 
<< Job for apache2.service failed.
See "systemctl status apache2.service" and "journalctl -xe" for details.>>
      
To solve this problem, I had to uninstall and intall Apache2 again by running the following commands. 
           
           sudo apt-get purge apache2
           sudo apt-get install apache2
To check the installed version, i had to run the following command. 
           
           <apache2 -v>
           
then I checked apache status using the following command:
           
           <sudo systemctl status apache2.service>

when i was sure that Apache is up and running again, I tried reloading again and it worked just fine thid time. 
            
I Finally, had to create a PHP script to test that PHP is correctly installed and configured on my server.

Now that I had a custom location to host my website’s files and folders, I had to create a PHP test script to confirm that Apache is able to handle and process requests for PHP files.
            
I Created a new file named index.php inside my custom web root folder by typing the following command: 
            
            <vim /var/www/projectlamp/index.php>
             
this then opened a blank file, i then added the following text, which is valid PHP code, inside the file.
             

             <?php
             phpinfo();

I then saved and close the file, refreshed the page and the following page came up. 
<img width="818" alt="Screenshot 2022-04-15 at 16 09 23" src="https://user-images.githubusercontent.com/103360590/163587667-70f11b9e-f90e-4e27-928e-e7752e28ddb8.png">

I then had to remove the file I created as it contains sensitive information about my PHP environment -and my Ubuntu server. I used rm to do so as follows:

       <sudo rm /var/www/projectlamp/index.php>

The following pictured demonstrates the steps.

<img width="652" alt="Screenshot 2022-04-15 at 16 24 01" src="https://user-images.githubusercontent.com/103360590/163592325-8a112fef-954f-4d13-b634-bc675ad63590.png">
<img width="652" alt="Screenshot 2022-04-15 at 16 24 31" src="https://user-images.githubusercontent.com/103360590/163592355-edcb0e99-0577-4e89-ad2a-8e8b5d30fd05.png">
<img width="652" alt="Screenshot 2022-04-15 at 16 25 02" src="https://user-images.githubusercontent.com/103360590/163592382-d697b327-8496-4308-b040-02b0ca372183.png">

I couldnt see the php page on my server when i reloaded. I had to check the vervion on the virtual machine using the following command just to be sure its been installed. 
       
             <php --version>

<img width="717" alt="Screenshot 2022-04-16 at 21 39 07" src="https://user-images.githubusercontent.com/103360590/163690897-adc83c33-c20e-469b-b91e-5b3f382f605f.png">







            
            






























 





























