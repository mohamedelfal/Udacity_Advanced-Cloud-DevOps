**What is CloudFormation?**

[CloudFormation](https://youtu.be/Omppm_YUG2g) is an AWS tool for creating, managing, configuring, and deploying cloud resources.  
This tool is beneficial if you have to provision a set of cloud resources multiple times, at scale.  
You can do so by simply writing (YAML or JSON) scripts that you can easily edit and run numerous times.  
In the script, we mention each resource's necessary configuration that we want to provision and then use the AWS CLI tool and commands to execute the scripts.

**Tools required for the current course**  
**1-AWS CLI tool**: If you haven't installed and configured [AWS CLI tool](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) yet, we will learn to do that in the upcoming pages again.  
You can verify the installation using the following command in your terminal (macOS)/cmd (Windows).
```
# See the current version
aws --version
```
Recall that you will have to configure AWS CLI after the installation as:

* Create an IAM User and copy the access key

* Configure the credentials in CLI

On the next page, you will see the demo showing the above two steps.

**2-Terminal** (macOS/Linux) or **CMD** (Windows)  
**3-Git** - [Download and install the Git for your system](https://git-scm.com/downloads).  
Git is an open-source distributed Version Control System (VCS).  
Github is a repository hosting and version control service, where you can store, share, or download the repository content in collaboration with multiple contributors.  
Once downloaded, you can use Git as a command-line tool in your Terminal (macOS) or Git bash(Windows).

**4-Code editor**: The instructor has used the VS code editor in his demonstrations.  
You are free to choose any code editor of your choice. However, you can download and install VS code [here](https://code.visualstudio.com/download).  
Once you have the editor installed, you can run the following commands in your Terminal (macOS)/Git bash (Windows):
```
# Clone the repository to your local system
git clone https://github.com/udacity/nd9991-c2-Infrastructure-as-Code-v1.git
cd nd9991-c2-Infrastructure-as-Code-v1
# See the content in the current directory. You will see README.md, project_starter, and supporting_material directories. 
ls
# Get inside the supporting_material
cd supporting_material
# Open the VS code editor to display your content
code .
```
In addition to the tools above,

* **Language proficiency**: It will be beneficial to have a little familiarity with the JSON and YAML programming language basics.  
* Even if you are not acquainted, you can still learn on-the-go. 
* **AWS region** used for this course: Prefer to choose either **US West (Oregon)`us-west-2`** or**US East (N. Virginia) `us-east-1`**.  
* This will guarantee the options are the same for all students.
