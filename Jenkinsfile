pipeline {
    agent any  
    stages {
        stage(‘create stack') {
              steps {
                sh “aws cloudformation create-stack —stack-name mediawiki —template-body file://mediawikicfn.json —region 'us-east-1’ --parameters  ParameterKey= VpcId,ParameterValue=$VpcId ParameterKey=Subnet ,ParameterValue=$Subnet ParameterKey=KeyName,ParameterValue=$KeyName ParameterKey=DBName,ParameterValue=$DBName ParameterKey=DBUser,ParameterValue=$DBUser ParameterKey=DBPassword,ParameterValue=$DBPassword  ParameterKey=DBAllocatedStorage,ParameterValue=$DBAllocatedStorage ParameterKey=DBInstanceClass,ParameterValue=$DBInstanceClass ParameterKey=MultiAZDatabase,ParameterValue=$MultiAZDatabase ParameterKey= WebServerCapacity,ParameterValue=$WebServerCapacity ParameterKey=InstanceType,ParameterValue=$InstanceType ParameterKey= SSHLocation,ParameterValue=$SSHLocation"
            }
        }
        
    }
}

