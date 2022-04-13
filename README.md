# Advanced Cloud DevOps 
## Nanodegree Program by Udacity 
[[Program Link](https://www.udacity.com/course/cloud-dev-ops-nanodegree--nd9991)] [[Program Syllabus](https://d20vrrgs8k4bvw.cloudfront.net/documents/en-US/Cloud+DevOps+Nanodegree+program+Syllabus.pdf)]
## Project 1
 ## [Deploy Static Website on AWS](./Project-1-DeployStaticWebsiteOnAWS/README.md)
>  * [README](./Project-1-DeployStaticWebsiteOnAWS/README.md)
>    * [1-Introduction](./Project-1-DeployStaticWebsiteOnAWS/1-Introduction.md)
>    * [2-CreateS3Bucket](./Project-1-DeployStaticWebsiteOnAWS/2-CreateS3Bucket.md)
>    * [3-UploadFilesToS3Bucket](./Project-1-DeployStaticWebsiteOnAWS/3-UploadFilesToS3Bucket.md)
>    * [4-SecureBucketViaIAM](./Project-1-DeployStaticWebsiteOnAWS/4-SecureBucketViaIAM.md)
>    * [5-ConfigureS3Bucket](./Project-1-DeployStaticWebsiteOnAWS/5-ConfigureS3Bucket.md)
>    * [6-DistributeWebsiteViaCloudFront](./Project-1-DeployStaticWebsiteOnAWS/6-DistributeWebsiteViaCloudFront.md)
>  * [Download Udacity Starter Website](./Project-1-DeployStaticWebsiteOnAWS/udacity-starter-website.zip) [Download from GitHub](/Project-1-DeployStaticWebsiteOnAWS/udacity-starter-website/)
## [Project 1 Solution](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md)
* [Project 1 :Deploy Static Website on AWS](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#project-1-deploy-static-website-on-aws)
  * [1- Website Files](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#1--website-files-)
    * [1-The S3 bucket is created.](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#1-the-s3-bucket-is-created)
    * [2-all the website Files uploaded to the newly created S3 bucket.](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#2-all-the-website-files-uploaded-to-the-newly-created-s3-bucket-)
    * [3- The S3 bucket is conFigured to support static website hosting.](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#3--the-s3-bucket-is-configured-to-support-static-website-hosting-)
    * [4- The S3 bucket has an IAM bucket policy that makes the bucket contents publicly accessible.](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#4--the-s3-bucket-has-an-iam-bucket-policy-that-makes-the-bucket-contents-publicly-accessible-)
    
  * [2- Website Distribution](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#2--website-distribution-)
    * [CloudFront has been conFigured to retrieve and distribute website Files.](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#cloudfront-has-been-configured-to-retrieve-and-distribute-website-files-)
  * [3- Access Website In Web Browser](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#3--access-website-in-web-browser-)
    * [1-Access the`https` secured website **without appending** `/index.html` at the end: `https://d25g3zasxgsb3t.cloudfront.net`](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#1--open-a-web-browser-like-google-chrome-and-paste-the-copied-cloudfront-domain-name-httpsd25g3zasxgsb3tcloudfrontnet-without-appending-indexhtml-at-the-end-the-cloudfront-domain-name--httpsd25g3zasxgsb3tcloudfrontnet-show-the-content-of-the-default-home-page-as-shown-below-)
    * [2- Access the website via website-endpoint:`http://first-udacity-website.s3-website.eu-west-3.amazonaws.com/`](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#2--access-the-website-via-website-endpointhttpfirst-udacity-websites3-websiteeu-west-3amazonawscom-)
    * [3- Access the bucket object via its S3 object URL:`https://first-udacity-website.s3.amazonaws.com/index.html`](./Project-1-DeployStaticWebsiteOnAWS/project1solution.md#3--access-the-bucket-object-via-its-s3-object-url-httpsfirst-udacity-websites3amazonawscomindexhtml-)
    
# project 2
## Deploy a high-availability web app using CloudFormation
* [1-Project Introduction](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#1-project-introduction-)
 * [Starter Code](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#starter-code)
* [2-Problem](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#2-problem-)
 * [Scenario](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#scenario)
* [3-Project Requirements](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#3-project-requirements-)
 * [Server Specs](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#server-specs)
* [4-Other Considerations](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#4-other-considerations-)
 * [Other Considerations](./Project-2-Deploy-a-high-AvailabilityWebAppUsingCloudFormation/README.md#other-considerations)
