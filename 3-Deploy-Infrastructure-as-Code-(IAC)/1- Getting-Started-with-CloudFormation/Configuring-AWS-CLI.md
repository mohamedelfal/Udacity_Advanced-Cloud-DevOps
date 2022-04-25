**Configuring the AWS Command Line Interface (CLI)**  
Assuming you have already installed the [AWS CLI tool](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) and copied the access key for an administrator IAM user, follow the steps below:

* Verify, if you already have a CLI v1 installed.  
If yes, prefer to [uninstall CLI v1](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html) and have CLI v2 installed, which is the latest one.  
You can verify the version using:
```
aws --version
```
To set up your AWS CLI, type either of the following commands in the terminal: 
```shell
aws configure
aws configure --profile default
```
Upon prompt: 
* Paste the copied access key (access key id and secret access key). 
* Enter the default region either as as `us-east-1` or `us-west-2`, even if you’re living closer to another available region. 
* Enter the output format either as `json` or leave it blank  
 
**Verifying your Setup**  
Verify the successful configuration of the AWS CLI, by running any AWS command:
```shell
# List your S3 buckets. This will be blank if you have no S3 buckets
aws s3 ls
# List the IAM users in your account
aws iam list-users
```
The output of `aws iam list-users` command will display the details of the recently created user:
```shell output
{
  "Users": [
      {
          "Path": "/",
          "UserName": "NameOfUser",
          "UserId": "AIDAZMXYZ3LY2BNC5ZM5E",
          "Arn": "arn:aws:iam::388752792305:user/Admin",
          "CreateDate": "2021-01-28T13:44:15+00:00"
      }
  ]
}
```

