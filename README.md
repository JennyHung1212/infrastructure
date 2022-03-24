# infrastructure

## AWS CLI

```bash
# set up profile and region for aws cli
export AWS_PROFILE=dev
export AWS_REGION=us-east-1
```

## Create Stack

```bash
# create a vpc with default cidr
aws cloudformation create-stack --stack-name vpc --template-body file://CloudFormation/vpc_param.yml
```

```bash
# create a vpc with default subnets
aws cloudformation create-stack --stack-name vpc --template-body file://CloudFormation/vpc_subnet.yml
```

```bash
# create a vpc with three public subnets spread across
# two Availability Zones, and an internet gateway, with a default
# route on the public subnets
aws cloudformation create-stack --stack-name <stackName> --template-body file://CloudFormation/vpc_subnets.yml
```

```bash
# create a vpc with custom KeyName
aws cloudformation create-stack --stack-name <stackName> --template-body file://CloudFormation/vpc.yml --parameters ParameterKey=AMI,ParameterValue="ami-0241883f5c6e474a7" ParameterKey=EC2KeyName,ParameterValue="aws-demo-ec2
```

## Update Stack

```bash
# update a vpc with provided cidr
aws cloudformation update-stack --stack-name vpc --template-body file://CloudFormation/vpc_param.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.1.1.0/24"
```

```bash
# add output values
aws cloudformation update-stack --stack-name vpc --template-body file://CloudFormation/vpc_output.yml --parameters ParameterKey=VpcCidrBlock,ParameterValue="10.1.1.0/24"
```

```bash
# pass in ami as param
aws cloudformation update-stack --stack-name vpc-dev --template-body file://CloudFormation/vpc.yml --parameters ParameterKey=AMI,ParameterValue="ami-0439554132109f852"
```

```bash
# update stack with IAM
aws cloudformation update-stack --stack-name vpc-dev --template-body file://CloudFormation/vpc.yml --capabilities CAPABILITY_NAMED_IAM
```

## Delete Stack

```bash
aws cloudformation delete-stack --stack-name <stackName>
```
