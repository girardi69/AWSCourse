## Installing Node.js on Amazon Linux AMI

The following will guide you through the process of installing [Node.js](https://nodejs.org/en/) on an AWS EC2 instance running Amazon Linux AMI 2016.09 - [Release Notes](https://aws.amazon.com/amazon-linux-ami/2016.09-release-notes/)

For this process I'll be using a t2.micro EC2 instance running 
Amazon Linux AMI (**ami-d41d58a7**).
Once the EC2 instance is up-and-running, connect to your server via ssh  

* Make sure our server has the [latest packages](https://aws.amazon.com/amazon-linux-ami/2016.09-packages/) : 
`sudo yum update -y`
* Install required packages : `sudo yum install -y gcc gcc-c++ make openssl-devel`  

### Installing Node.js
For the next steps, use `/tmp` as the working directory

* Download the Node.js source code, select the recommended LTS version via the [Node.js download page](https://nodejs.org/en/download/) and copy the URL of the "Source Code" -package : `curl -O https://nodejs.org/dist/v4.6.0/node-v4.6.0.tar.gz`

> At this time of writing the current 
version is  **v4.6.0** (which includes npm 2.15.9)  

* Unpack and cleanup : `tar -xvf node-v4.6.0.tar.gz && rm node-v4.6.0.tar.gz`
* Configure, make and install,... this may take a while, especially the compiling part.

```
$ cd node-v4.6.0
$ ./configure
$ make
$ sudo make install
```

You can verify afterwards if the installation was successful by checking the versions of **node** and **npm** :

* `node -v`, returns value **v4.6.0**
* `npm -v`, returns value **2.15.9**

If by any chance, your are in the root environment and the previous command returns "**-bash: node: command not found**", you can fix this by creating the following symbolic links :

```
sudo ln -s /usr/local/bin/node /usr/bin/node
sudo ln -s /usr/local/lib/node /usr/lib/node
sudo ln -s /usr/local/bin/npm /usr/bin/npm	
```


### Testing Node.js
The best method to test Node.js is actually run an application. This this prurpose we'll configure and runs a simple webserver. Again, let's use `/tmp` as our working directory..

* Create a subdirectory : `mkdir www`
* Enter the directory : `cd www`
* Create a file called **server.js** and edit the contents of the file : `nano server.js`
* Paste the following code and save : 

```
var http = require('http');

var server = http.createServer(function (request, response) {  
  response.writeHead(200, {"Content-Type": "text/html"});
  response.end("<h3>Node webserver running</h3>\n");
});

server.listen(8080);
console.log("Node.js is listening on port 8080");  
```

* Start the application : `node server.js`
* Open a browser and go to the public IP address of the EC2 instance to test : `http://<ip-address-ec2-instance>:8080`
* As a result you should see the "**Node webserver running**" -message

> Make sure the security group applied to your EC2 instance allows inbound traffic to port 8080 !

 
