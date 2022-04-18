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

[Log Your EC2 Linux User-Data and Then Ship It to the Console Logs](https://aws.amazon.com/premiumsupport/knowledge-center/ec2-linux-log-user-data/) 

[How do I log my EC2 Linux user-data and ship it to the console logs?  ](https://youtu.be/unMiTRw8JVE)

[![How do I log my EC2 Linux user-data and ship it to the console logs?](./image/youtube2.jpg)](https://youtu.be/unMiTRw8JVE)


*  Unfortunately when I try to connect from my browser I keep getting a 504 Gateway Time-out for the Backup Load Balancer DNS Name url that is output
* [Troubleshoot Your Application Load Balancers - Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-troubleshooting.html#http-504-issues)

Try to Access Logs for Your Application Load Balancer

* [Access Logs for Your Application Load Balancer - Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-access-logs.html)

## Load Balancer Checklist 
The load balancer has the correct type  
Has a Properties attribute  
In the Properties, it has the correct security groups, that allow traffic to and from it  
In the Properties, it has the correct subnets  
In the Properties, it has the type equal to application  
The load balancer has a related resource of type TargetGroup  
The load balancer has a related resource of type Listener  
The load balancer has a related resource of type ListenerRule
Target Group Checklist   
The target group has the correct type   
Has a Properties attribute
In the Properties, it has the VPCId   
In the Properties, it has the Port   
In the Properties, it has the Protocol equal to HTTP   
The Target Group has a related resource of type Listener
The Target Group has a related resource of type ListenerRule   
The Target Group has a related resource of type AutoScalingGroup
The Target Group is referenced in the AutoScalingGroup with the property TargetGroupARNs   
Listener Checklist   
The Listener has the correct type   
Has a Properties attribute   
In the Properties, it has the DefaultActions. For example:   
![image](https://user-images.githubusercontent.com/100445644/163737147-134ce195-a1ad-4acd-a75a-7b3208ee9516.png)

In the Properties, it has the LoadBalancerArn   
In the Properties, it has the Protocol equal to HTTP   
In the Properties, it has the Port   
The Listener has a related resource of type ListenerRule   
The Listener is referenced in the ListenerRule with the property ListenerArn   
Listener Rule Checklist   
The Listener Rule has the correct type   
Has a Properties attribute   
In the Properties, it has the DefaultActions. For example: 

![image](https://user-images.githubusercontent.com/100445644/163737137-28981a1f-22f3-4fcf-b30e-3127e6859052.png)

In the Properties, it has the Conditions   
In the Properties, it has the ListenerArn   
In the Properties, it has the Priority
9. I am having a problem with the LaunchConfiguration   
LaunchConfiguration Checklist   
The LaunchConfiguration has the correct type   
Has a Properties attribute   
In the Properties, it has the UserData   
You tested the UserData in an EC2 instance and it works   
You included at the top of the UserData the #!/bin/bash   

![image](https://user-images.githubusercontent.com/100445644/163737116-b254ba26-275d-4c5b-a0a5-f9fcaf73e661.png)

In the Properties, it has the ImageId   
In the Properties, it has the InstanceType   
In the Properties, it has the BlockDeviceMappings   
In the Properties, it has the SecurityGroups   
In the Properties, it has the LaunchConfigurationName   
How to use multiple templates?   
You need to create one stack for each template with the create-stack command   
How to find the correct imageId for the LaunchConfiguration?   
This link will teach you: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/finding-an-ami.html   
I want to show this good and short solution:   

How to fix in cloudformation that my instances say unhealthy 502 or the logs say “Restart services during package updates without asking”?   
Use this code in the LaunchConfiguration   
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
The make sure that you are using an Image of Ubuntu. Select the correct one for your Zone   

How to test a UserData for a LaunchConfiguration in AWS?   
https://www.youtube.com/watch?v=xOqEQdc_eRo&t=7s   


## resources
* [1](https://github.com/andresaaap?tab=repositories)
* [2](https://andresaaap.medium.com/deploy-a-high-availability-web-app-using-cloudformation-project-faq-udacity-cloud-devops-53a115fde07e)
