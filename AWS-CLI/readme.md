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