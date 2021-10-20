# ami

Steps:
1. Run terraform script and create vpc with appropriate CIDR
2. Use VPC subnet address as input to the AMI you are going to create
3. Create AMI - ./build.sh
4. Create EC2 instance and create key for the instance and security groups – tcp, http, https, ssh from anywhere and port for tcp - 5000
5. Ssh into the instance ->  ssh -I amissh.cer ubuntu@ip -p 22
6. Change permission if you get error – chmod 400 amissh.cer
7. If it shows bad permissions – locate file on file explorer, select properties-> security->advanced->change owner to you and save permissions
8. Change root permissions with: sudo mysql -u root -p
   ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '<passord>';
9. Create database on root
10. Transfer node files from local machine to EC2
    scp -i certificate -r node-app-directory ubuntu@publicroute:/home/ubuntu/
11. run the ec2 instance again using ssh command
12. go to node application and install dependencies
13. run the node application
14. Use postman to check apis on public ip of ec2 instance
15. Go to AWS console, Route 53
16. Inside hosted routes copy the public ip address on ec2 instance under Type A configuration
17. Check the hosted dns using Google Admin Toolbox or using dig command
    dig A dev.dns.me
18. change the access control headers in the node application to accept from origin "dev.dns.me"
19. check the api on this dns using postman