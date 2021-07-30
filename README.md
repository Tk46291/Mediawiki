# Mediawiki

Automate Mediawiki App Deployment using Cloudformation Template with AWS Cli.
I have used the AWS linux AMI and installed the Apacahe2 and PHP along with the Mediawiki configuration setup. 
Launched the AWS RDS for Mysql dB as a backend database. 
We also can use AWS marketplace subscription of mediawiki packaged ami for the application setup

Deployment involves:
1.	CFN Template 
2. Application load balancer (Access App) 
3. AWS CLI 


Steps:
1.	Git clone/Copy the repo in order to setup deployment. 
2.	Make sure that you have access to the AWS console or AWS CLI with necessary permission to create the stack.


To perform the Cloudformation create stack we can use the AWS CLI from the server having necessary permissions to All required services.

aws cloudformation create-stack —stack-name mediawiki —template-body file://mediawikicfn.json —region 'us-east-1’ --parameters ParameterKey= KeyName ,ParameterValue=$KeyName ParameterKey= DBName,ParameterValue=$DBName ParameterKey= DBUser,ParameterValue=$DBUser ParameterKey=DBPassword,ParameterValue=$DBPassword  ParameterKey= DBAllocatedStorage,ParameterValue=$DBAllocatedStorage ParameterKey=DBInstanceClass,ParameterValue=$DBInstanceClass ParameterKey= MultiAZDatabase,ParameterValue=$MultiAZDatabase ParameterKey= WebServerCapacity,ParameterValue=$WebServerCapacity ParameterKey=InstanceType,ParameterValue=$InstanceType ParameterKey= SSHLocation,ParameterValue=$SSHLocation

Kindly provide the required parameter values while running this from AWS cli command line interface.

use Application load balancer end point in the browser to access the Application UI.



3.	Kindly setup a AWS cli on the Jenkins server in order to create the stack from Jenkins Pipeline build. This can also be done without configuring aws cli on Jenkins server with “awscloudformation” plugin.

4. Kindly create a Pipeline build in Jenkins and browse the Jenkins file as SCM from the git repo. 
5. please use a parameterized build and craete the paramters mentioned in the jenkins file
6.	In order to run the build from Jenkins server with AWS cli we need to add roles to Jenkins Ec2 for the services creating from cloudformation template (ex. AWS s3,RDS)



Application scaling : 
Cloudformation template is setup with AutoScaling configuration kindly provide the parameter values with required application instances count and multi AZ RDS deployment value true or false.










![image](https://user-images.githubusercontent.com/32525224/127636460-79428afb-43c1-4f17-9348-59a593af12c8.png)
