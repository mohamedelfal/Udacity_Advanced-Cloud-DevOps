* create an [`index.html`](./index.html) as `Udagram` app
* [`UserData`](./script.yml) script this is example of a [`UserData`](./script.yml) that you can use:
```
UserData: 
    Fn::Base64: !Sub |
        #!/bin/bash -xe
        exec > >(tee /var/log/user-data.log|logger -t user-data -s 2>/dev/console) 2>&1
        apt update -y
        apt install -y apache2
        systemctl start apache2
        systemctl enable apache2
        rm ../../var/www/html/index.html
        wget -P ../../var/www/html https://s3.us-east-2.amazonaws.com/test-udagram-1/index.html
  ```

> * code explanation

    #!/bin/bash
This line indicated that we are going to use the bash engine

    apt update -y
To ensure that all of your software packages are up to date, perform a quick software update on your instance.  
This process may take a few minutes, but it is important to make sure that you have the latest security updates and bug fixes

    apt install -y httpd
install the Apache web server

    systemctl start httpd
Start the Apache web server

    wget -P ../../var/www/html https://s3.us-east-2.amazonaws.com/test-udagram-1/index.html
Download an HTML file that I store in a S3 bucket.  
In this case you will need to create your own S3 bucket, upload your HTML file and make the file publicly accessible

To read more about this you can use this links:
* 1- [Tutorial: Install a LAMP Web Server with the Amazon Linux AMI - Amazon Elastic Compute Cloud](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-LAMP.html)
* 2- [Walkthrough: Set Up an Apache Web Server and Serve Amazon EFS Files - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/wt2-apache-web-server.html)
* 3- [How To Start / Stop / Restart / Enable / Reload The Apache (HTTPD) Service In Linux?](https://www.2daygeek.com/start-stop-restart-enable-reload-apache-httpd-web-server-service-in-linux/)


* check network is still setup correctly. Should be able to ping the elastic IP’s
* The first test to ensure that the network is setup correctly is to verify that every resource was successfully created
* The second test is to manually verify in the AWS console that every resource created has the correct configuration and values
* The third test it to deploy some simple server resources in that network, like a server in the public subnet and make sure that you can connect to it

# X
so how would I put an index.html in my code or somewhere else so that when I enter my load balancer (on the internet in real life) and after it directs me into one of my private subnets and into one of my servers that its message will show up

* The UserData in the LaunchConfiguration needs some commands to download the index.html from the s3 bucket into the instance. these commands are executed in the instance and that how it works. Please look at question 3 https://medium.com/@andresaaap/deploy-a-high-availability-web-app-using-cloudformation-project-faq-udacity-cloud-devops-53a115fde07e

* does the bucket need to be created in the cloud formation script or can it just be created in the console?  
The bucket is not created in the cloudformation script, do it manually


*  I am having problems with the load balancer or with the EC2 instance. 
 I don’t know how to verify that the commands in the UserData executed correctly and if the problems are in the EC2 instances.
There are 2 ways to troubleshoot the servers and the UserData:
* Test the UserData first by creating a EC2 instances with the same specifications in the LaunchConfiguration. Launch the instance in the EC2 dashboard, NOT in CloudFormation.
* Configure your UserData in your CloudFormation script so that you can see the logs of the invocation of the UserData in the System Log.


To troubleshoot issues on your EC2 instance bootstrap without having to access the instance through SSH, you can add code to your user-data bash script that redirects all the output both to the /var/log/user-data.log and to /dev/console. When the code is executed, you can see your user-data invocation logs in your console.

* Please look at these tutorials: 
* 
[Log Your EC2 Linux User-Data and Then Ship It to the Console Logs](https://aws.amazon.com/premiumsupport/knowledge-center/ec2-linux-log-user-data/) 

[How do I log my EC2 Linux user-data and ship it to the console logs?  ](https://youtu.be/unMiTRw8JVE)

[![How do I log my EC2 Linux user-data and ship it to the console logs?](./image/youtube.jpg)](https://youtu.be/unMiTRw8JVE)

<video src=https://youtu.be/unMiTRw8JVE width=180/>

[<img src="https://img.youtube.com/vi/<VIDEO ID>/maxresdefault.jpg" width="50%">](https://youtu.be/unMiTRw8JVE/<VIDEO ID>)

[![Demo CountPages alpha](https://share.gifyoutube.com/KzB6Gb.gif)](https://youtu.be/unMiTRw8JVE)

[![Watch the video](https://img.youtube.com/vi/unMiTRw8JVE/hqdefault.jpg)](https://youtu.be/unMiTRw8JVE)

<iframe width="560" height="315" src="https://www.youtube.com/embed/unMiTRw8JVE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## resources
* [1](https://github.com/andresaaap?tab=repositories)
* [2](https://andresaaap.medium.com/deploy-a-high-availability-web-app-using-cloudformation-project-faq-udacity-cloud-devops-53a115fde07e)
