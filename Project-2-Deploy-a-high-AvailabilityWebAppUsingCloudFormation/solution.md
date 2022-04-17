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

> * code explanation(

    #!/bin/bash
This line indicated that we are going to use the bash engine

    apt update -y
To ensure that all of your software packages are up to date, perform a quick software update on your instance. This process may take a few minutes, but it is important to make sure that you have the latest security updates and bug fixes

    apt install -y httpd
install the Apache web server

    systemctl start httpd
Start the Apache web server

    wget -P ../../var/www/html https://s3.us-east-2.amazonaws.com/test-udagram-1/index.html
Download an HTML file that I store in a S3 bucket. In this case you will need to create your own S3 bucket, upload your HTML file and make the file publicly accessible

To read more about this you can use this links:
* 1- [Tutorial: Install a LAMP Web Server with the Amazon Linux AMI - Amazon Elastic Compute Cloud](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-LAMP.html)
* 2- [Walkthrough: Set Up an Apache Web Server and Serve Amazon EFS Files - Amazon Elastic File System](https://docs.aws.amazon.com/efs/latest/ug/wt2-apache-web-server.html)
* 3- [How To Start / Stop / Restart / Enable / Reload The Apache (HTTPD) Service In Linux?](https://www.2daygeek.com/start-stop-restart-enable-reload-apache-httpd-web-server-service-in-linux/)

## resources
* [1](https://github.com/andresaaap?tab=repositories)
* [2](https://andresaaap.medium.com/deploy-a-high-availability-web-app-using-cloudformation-project-faq-udacity-cloud-devops-53a115fde07e)
