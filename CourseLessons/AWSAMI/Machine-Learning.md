
# Jupyter Notebook Creation

## Creating The instance

1. Choose a Linux Deep Learning Base AMI (Amazon Linux) Version 18.0 - ami-0cc0847fd2d585a41  
2. Choose a c3.xlarge instance type  
3. Review and Launch  
4. Choose a key pair  


## Create the two instructions on a text editor

ssh -L localhost:8888:localhost:8888 -i GirardiKeyPairCTO.pem ubuntu@ec2-52-212-202-91.eu-west-1.compute.amazonaws.com  
ssh -i "GirardiKeyPairCTO.pem" ubuntu@ec2-52-212-202-91.eu-west-1.compute.amazonaws.com  

## Use the "connect" option on the instance to shortcut the instance dns name c2-52-212-202-91.eu-west-1.compute.amazonaws.com  


## Terminal Configuration

1. Open terminal
2. Connect to the ubuntu instance  
iMac-di-Andrea:awscto girardi69$ ssh -i "GirardiKeyPairCTO.pem" ubuntu@ec2-34-242-101-214.eu-west-1.compute.amazonaws.com  
exit from ububtu. 
ubuntu@ip-172-31-24-150:~$ exit  
3. Connect again with localhost reflection on the local browser
iMac-di-Andrea:awscto girardi69$ ssh -L localhost:8888:localhost:8888 -i GirardiKeyPairCTO.pem ubuntu@ec2-34-242-101-214.eu-west-1.compute.amazonaws.com   
4. Fire the Jupyter Notebook  
ubuntu@ip-172-31-24-150:~$ jupyter notebook  
  
[I 11:57:36.724 NotebookApp] Writing notebook server cookie secret to /run/user/1000/jupyter/notebook_cookie_secret  
[I 11:57:41.380 NotebookApp] Serving notebooks from local directory: /home/ubuntu  
[I 11:57:41.380 NotebookApp] The Jupyter Notebook is running at:  
[I 11:57:41.380 NotebookApp] http://localhost:8888/?token=454f5a6f51ae8d469f3669bee338ddc21dd35b8610121fc9. 
[I 11:57:41.380 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).  
[W 11:57:41.383 NotebookApp] No web browser found: could not locate runnable browser.  
[C 11:57:41.383 NotebookApp]  
      
    To access the notebook, open this file in a browser:  
        file:///run/user/1000/jupyter/nbserver-18669-open.html  
    Or copy and paste one of these URLs:  
        http://localhost:8888/?token=454f5a6f51ae8d469f3669bee338ddc21dd35b8610121fc9  
        
5. copy and paste in the browser:  
http://localhost:8888/?token=454f5a6f51ae8d469f3669bee338ddc21dd35b8610121fc9  

## Terminate the EC2 Instance!!!
