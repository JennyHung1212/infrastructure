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
aws cloudformation update-stack --stack-name vpc-dev-3 --template-body file://CloudFormation/vpc.yml --parameters ParameterKey=AMI,ParameterValue="ami-093c9a5e49c75ae89"
```

## Delete Stack

```bash
aws cloudformation delete-stack --stack-name <stackName>
```
