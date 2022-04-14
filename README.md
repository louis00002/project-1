# project-1
 INSTALLING APACHE 
 first thing i had to do was to SSH into the AWS server using the terminal using the following commands 
 
  ssh -i "ubuntufromMac.pem" ubuntu@ec2-34-239-122-184.compute-1.amazonaws.com
  ls
  cd Downloads
  ls
   ssh -i "ubuntufromMac.pem" ubuntu@ec2-34-239-122-184.compute-1.amazonaws.com
   
  when i was safely connected to the EC2 instance, i proceeded with the following commands to download APACHE2 WEB SERVER SOFTWARE. 
  
  'sudo apt update'. to check for updates and 
sudo apt install apache2 to download the software.


To verify that apache2 is running as a Service in my OS, i ran the following coomand
sudo systemctl status apache2
this is what it looked like when Apache2 was up and running<img width="1026" alt="Screenshot 2022-04-13 at 23 15 36" src="https://user-images.githubusercontent.com/103360590/163288448-ee27c8eb-d360-4e96-bbcb-0a1f4e845f9d.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 19 55" src="https://user-images.githubusercontent.com/103360590/163288485-a6afd98b-db38-45c3-942c-b9c807a3c6f7.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 47 38" src="https://user-images.githubusercontent.com/103360590/163288534-840bddfa-9e90-48b5-834e-62c3d7492f3c.png">
<img width="1026" alt="Screenshot 2022-04-13 at 23 48 33" src="https://user-images.githubusercontent.com/103360590/163288618-9cabef8b-bf4a-4c5b-8191-de54731ac6bc.png">

Before i could receive any traffic from the Web Server, i neeed to open TCP port 80 which is the default port that web browsers use to access web pages on the Internet.

i then had to, check how we can access it locally in our Ubuntu shell, by running the conmmand: 

 curl http://localhost:80 or  curl http://127.0.0.1:80

i then had to test how our Apache HTTP server can respond to requests from the Internet by browing 
http://100.24.2.15:80 on my web browser which gave me the following page.

<img width="808" alt="Screenshot 2022-04-14 at 01 09 21" src="https://user-images.githubusercontent.com/103360590/163289429-0c010b2e-c817-46f4-bba7-c6adb7cbd66a.png">.












