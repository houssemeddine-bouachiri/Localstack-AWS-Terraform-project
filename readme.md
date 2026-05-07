# LocalStack AWS & Terraform Emulation Project

![AWS](https://img.shields.io/badge/AWS-FF9900?logoColor=white&style=flat)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=white&style=flat)
![License](https://img.shields.io/badge/License-MIT-yellow)

This project demonstrates how to use **LocalStack** to emulate AWS services locally, combined with **Terraform** for Infrastructure as Code (IaC). It allows you to develop, test, and iterate on AWS resources without needing a real AWS account or incurring cloud costs.

---
## docs

https://docs.localstack.cloud/integrations/

## AWS Cli docs

https://docs.aws.amazon.com/cli/latest/reference/

---

https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html

---


## Installation/Starting Localstack (Option 1)

```
python -m pip install localstack==0.9.0
localstack start
```

## Running localstack on Docker (Option 2)

```
docker run --rm -it -p 4566:4566 -p 4571:4571 localstack/localstack
```

## Using AWS CLI

### AWSLocal wrapper (Option #1)

```
pip install awslocal-cli
awslocal s3api create-bucket --bucket my-bucket --region us-east-1
awslocal s3api list-buckets --region us-east-1
```

### AWS CLI pointing to endpoint (Option #2)

```
aws --endpoint-url=http://localhost:4566 s3api create-bucket --bucket my-bucket --region us-east-1
aws --endpoint-url=http://localhost:4566 s3api list-buckets
```

## More commands

```
aws --endpoint-url=http://localhost:4566 ec2 describe-instances --query 'Reservations[].Instances[].[InstanceId,InstanceType,PublicIpAddress,Tags[?Key==`Name`]| [0].Value]' --output table --region us-east-1
```

```
aws iam list-users
aws configure
aws s3 ls
aws s3 mb s3://nameofthebucket
aws s3 help
aws lambda list-functions
aws ec2 start-instances --instance-ids i-xxxxxxxxxxxxxxxxx
```
