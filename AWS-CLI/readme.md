# Amazon Web Services - Command Line Interface (AWS-CLI)

AWS CLI is a powerful command line tool. Commands fro every AWS services and resources can be accessed via CLI

Configure AWS CLI to connect to AWS account:

- `aws configure`

This command generated two files in `~/.aws/` directory i.e config and credentials files

## Command structure
- `aws <command> <subcommand> [options & parameters]`
- *command*: aws service i.e ec2, ecr, iam
- *subcommand*: operations i.e run-instances(ec2), create-security-groups(ec2), add-user-to-group(iam)

## List all available security-group ids

- `aws ec2 describe-security-groups`

## Create new security group
- `aws ec2 describe-vpcs`
- `aws ec2 create-security-group --group-name my-sg-cli --description "my SG created via cli" --vpc-id vpc-0ad4aaf3`
- `aws ec2 describe-security-groups --group-ids sg-09d72bd1d`

## this will give output of created my-sg with its id, so we can do:
- `aws ec2 describe-security-groups --group-ids sg-903004f8`

## add firewall rule to the group for port 22
- `aws ec2 authorize-security-group-ingress --group-id sg-903004f8 --protocol tcp --port 22 --cidr203.0.113.0/24`
- `aws ec2 describe-security-groups --group-ids sg-903004f8`

## Use an existing key-value pair or if you want, create and use a new key-pair. 'KeyMaterial' gives us an unencrypted PEM encoded RSA private key.
- `aws ec2 create-key-pair --key-name MyKeyPair --query 'KeyMaterial' --output text > MyKeyPair.pem`

## describing subnets
- `aws ec2 describe-subnets`
- `subnet-01e0ae6`

## Starting instance with obtained info
- `aws ec2 run-instances --image-id ami-0ea7dc624e77a15d5 --count 1 --instance-type t2.micro --key-name MyKpCli --security-group-ids sg-09d72bd1d0 --subnet-id subnet-01e0ae66341`
- `aws ec2 describe-instances`

# Queries and Filters
## Describing instance using queries and filters
- `aws ec2 describe-instances --filters "Name=instance-type,Values=t2.small" --query "Reservations[].Instances[].InstanceId"`

## Creating group
- `aws iam create-group --group-name MyGroupCLI`

## Creating user
- `aws iam create-user --user-name MyUserCli`

## Adding user to a group
- `aws iam add-user-to-group --user-name MyUserCli --group-name MyGroupCli`

- `aws iam get-group --group-name MyGroupCli`

## Listing Policies as text

- `aws iam list-policies --query 'Policies[?PolicyName==`AmazonEC2FullAccess`].{ARN:Arn}' --output text`

## Attaching EC2FullAccessc to group and listing group policies

- `aws iam attach-group-policy --group-name MyGroupCli --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess`

- `aws iam list-attached-group-policies --group-name MyGroupCli`

## Creating and getting login profile for user

- `aws iam create-login-profile --user-name MyUserCli --password Mypwd456 --password-reset-required`

- `aws iam get-user --user-name MyUserCli`

## Attaching IAMUserChangePass to group

- `aws iam attach-group-policy --group-name MyGroupCli --policy-arn arn:aws:iam::aws:policy/IAMUserChangePassword`

## Creating and configuring access keys for user

- `aws iam create-access-key --user-name MyUserCli`

- `aws configure set aws_access_key_id <keyid>`