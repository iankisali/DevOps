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