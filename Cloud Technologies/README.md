## AWS S3

- Experiment
    
    https://github.com/AndyFooGuoZhen/AWS-S3-tutorial
    
- Amazon storage service, can be used to store files, images
- Offers services to allow for public/private access to files and buckets ( database)
- Used with boto3 to interact with python
- When sending to specific folders, add directory path and append file name

---

## Docker

https://github.com/AndyFooGuoZhen/Docker_basics

---

## Kubernetes

https://github.com/AndyFooGuoZhen/Kubernetes_basics

---

## Jenkins

- automation server
- USed for CICD
- provide standardized test enviornment
- TIPS on accessing Jenkins : <IP> : 8080

---

### AWS EC2 + Jenkins + Github integration

- Virtual server, can be used for hosting applications remotely
- Steps to create  : https://www.youtube.com/watch?v=W1UQhLuxCo8
- Experiment
    
    https://github.com/AndyFooGuoZhen/AWS-S3-tutorial
    
Setup and installation of packages
  
1. go to aws console and create ec2 instance with ubuntu, give it a name, create key pair and allow access to all ports
2. Once .pem file downloaded, launch terminal and do chmod 400 <name>.pem 
3.  then run this command to access server, ssh -i <name>.pem ubuntu@<public ip>
4. install and configure jenkins on ubuntu server : install link : https://pkg.jenkins.io/debian-stable/
5. Check if java is installed by “java” command
6. Check if jenkins is installed by “jenkins” command
7. Install node js : sudo apt update sudo apt install nodejs
8. Install npm : sudo apt-get update , sudo apt-install npm 
9. restart server : reboot
10. Log in again , check if jenkins running : systemctl status jenkins
11. go to aws console for ec2 instance, navigate to security>security groups > edit inbound rules, add custom tcp rule with port 8080 and anywhere ipv4
12. paste public ip of server:8080 into browser, jenkins log in should appear
13. copy file path from jenkins log in page , and do sudo cat <copied filepath> to get key
14. paste key to log in , install suggested plugins
15. while installing, go back to terminal , sudo apt-get update, sudo apt-get install docker.io
16. go back browser page , create admin user with name : admin, passowrd : password, password
17. save , next step , and start using jenkins
18. verify docker has been installed on ec2 server : docker
19. new item on jenkins server, copy github repo link
20. freestyle project, paste github link, 
21. Source code management is git , paste github repo link
22. and hit apply
23. generate ssh key to allow jenkins to login to server : ssh-keygen
24. no passphrase, then open up ssh [key.pub](http://key.pub) using cat commanmd and copy key
25. go to github settings, ssh and gpg, create new ssh key, leave it for authentication and paste ssh key 
26. go to ec2 instance terminal, open up ssh private key file with cat command and copy private key
27. on jenkins server, go to configure, add credentials, kind : ssh and username
28. username is ubuntu, paste private key, save and run build
29. make sure git branch is main
30. Configure ec2 instance volume size → increase volume size to prevent npm installation errors
31. Configure inbound rules to allow port 3000
32. Run npm start to see if it runs
33. Create docker file : vim Dockerfile
34. refer to dockerfile example for react
35. run docker build to create image
36. and run docker run to create running container, make sure port is exposed
37. Once running verified, kill docker container and head to jenkins server to configure trigger
38. enable github hook trigger on project 
39. head to github repo, click on settings for repo, and head to webhooks
40. change content type to application/json
41. copy and paste jenkins url + /github-webhook  http://3.149.234.124:8080/github-webhook
42. head back to jenkins server, head to dashboard > manage jenkins > plugins
43. install github integration plugin
44. configure build steps with execute shell command
45. paste docker build and run command
46. if github webhook fails, deliver again , make sure end of url contains / slashes
47. Try to commit a change in github
48. configure permission settings for docker (Docker has no permission) 
49. at ec2 instance terminal, paste this command : sudo usermod -a -G docker jenkins, sudo usermod -a -G jenkins $USER
50. Restart jenkins: systemctl restart jenkins
51. Commit change in github to verify change

    ---
  
## Volumes in EC2

- Extending Volume Size
    - https://www.youtube.com/watch?v=usOv-5_hzu0
    - When running out of memory, you can configure to extend the size of a volume in aws console
    - Note : Take a snapshot of the volume (Backup in case something bad happens)
- Attaching new volume
    - https://www.youtube.com/watch?v=VnO3Lz7Qr0U
    - Creating a new folder with bigger disk space to current EC2 instance
    
    ---
    
## Ngninx

- Tool/Server used to manage network traffic (EX: when application deployed on server, many users uses the application)
- Can be used as proxy as well
- When network traffic is high, we scale out infrastructure by increasing number of servers
- Nginx acts as a load balancer, forwards http request to appropriate server that’s ready to handle the request
