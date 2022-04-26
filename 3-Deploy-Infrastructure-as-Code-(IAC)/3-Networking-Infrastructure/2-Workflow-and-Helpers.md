**Reference diagram**  
The file [AWSWebApp.jpeg](https://github.com/udacity/nd9991-c2-Infrastructure-as-Code-v1/tree/master/supporting_material) is complete a reference diagram that we exported from LucidChart in Jpeg format. Luckily, our VS code editor supports the jpeg format, and we can quickly reference this as a visual checklist to make sure we don’t forget any component when writing our CloudFormation script.

![awswebapp-2.jpeg](./image/awswebapp-2.jpeg)

AWSWebApp.jpeg diagram. We will create only the network-related resources in the current lesson.

The unidirectional directional arrows in the diagram above show the inbound requests and help you track the sequence of resource creation. The actual traffic flow would be bidirectional, with the following considerations:

The NAT gateway serves as an intermediary to take a private resource's outbound request, connect to the Internet gateway, and then relay the response back to the private resource without exposing that private resource's IP address to the public. We will learn more about the NAT gateways in the current lesson.
We will deploy the (publicly visible) load balancer in the same VPC having both public and private subnets. Note that all resources within a VPC can connect to each other directly using the private IP address. Therefore, the elastic load balancer can directly distribute the ingress requests across multiple targets VMs with the same VPC, even if the VMs are in a private subnet. We will learn more about the load balancers in the Lesson 4: Servers and Security Groups.
Let's start with creating the networking infrastructure first, such as, VPC, subnets, Internet gateway, NAT gateway, and route tables.

![networking infrastructures](./image/networking-infrastructures.jpg)
Filtered out networking infrastructures, such as VPC, subnets, Internet gateway, NAT gateway, and route tables.

**Learning about the YAML file**  
The video above shows you the testcfn.yml file, which you'd have created in the previous lesson. In the upcoming video demos, you will have to create a new YAML file. Let's learn about the sections present the testcfn.yml file:

Format version: The AWSTemplateFormatVersion section is optional. The current valid value is 2010-09-09. You can add it to your file as:
```yml
AWSTemplateFormatVersion: 2010-09-09
```
Description: TheDescription field is also optional. Here we start by adding a short description of the project we are working on.
```yml
AWSTemplateFormatVersion: 2010-09-09
Description: Carlos Rivas / Udacity - This template deploys a VPC
```
Resouces: Although a description is optional, the Resources section is required. Remember to include at least one resource (e.g., a VPC, an EC2 instance, a database) in the CloudFormation template, otherwise, it will give an error when you try to run the script.
```yml
AWSTemplateFormatVersion: 2010-09-09
Description: Carlos Rivas / Udacity - This template deploys a VPC
Resources:
UdacityVPC:
 Type: 'AWS::EC2::VPC'
 Properties:
   CidrBlock: 10.0.0.0/16
   EnableDnsHostnames: 'true'
```
Reference: [Template anatomy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html)
AWS command in a Shell script
As demonstrated in the video above, you can save your aws cloudformation command in a shell (.sh) script, so that you can run it multiple times easily. The instructor has created the following two shell scripts for the current course:

1-**create.sh**: This file contains the create-stack command, which expects three command-line arguments.
```sh
aws cloudformation create-stack --stack-name $1 --template-body file://$2  --parameters file://$3 --region=us-east-1
```
2-**update.sh**: This file contains the update-stack command, and this too expects three command-line arguments.
```sh
aws cloudformation update-stack --stack-name $1 --template-body file://$2  --parameters file://$3 --region=us-east-1
```
>Note: As stated earlier, you can choose either region, us-west-2 or us-east-1.

Moving forward, we will learn and add an additional option, --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM", in these commands as:
```sh
aws cloudformation create-stack --stack-name $1 --template-body file://$2  --parameters file://$3 --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-east-1
```
**Practice Fixing Errors**
* Practice fixing errors, as this will help you prepare for real scenarios on the job.
* For instance, try altering correct, working YAML scripts to see if they generate an error.
* Practice reading error messages to understand what caused the error, and how to fix them.

