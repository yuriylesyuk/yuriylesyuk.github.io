
# AWS Tips and Tricks


## AWS SSM: Session Management 
```
export ID=<vm-id>

aws ssm start-session --target $ID --document-name AWS-StartPortForwardingSession --parameters '{"portNumber":["22"],"localPortNumber":["2222"]}' &
aws ssm start-session --target $ID --document-name AWS-StartPortForwardingSession --parameters '{"portNumber":["4440"],"localPortNumber":["4440"]}' &
```

## add to aws profiles and completer at Windows with git bash/cygwin

``` sh
cygpath "$(which aws_completer)"  -d
complete -C /c/PROGRA~1/Amazon/AWSCLIV2/aws_completer aws
```

## profile management

```
aws sts getcalleridentity

aws configure sso

# for git bash at windows
winpty aws configure sso

aws sts get-caller-identity --profile sso-sb-util

aws sts get-access-key-info --access-key-id

aws sts get-session-token

aws sts assume-role --role-arn arn:aws:iam::423623838223:role/Vault-KMS --role-session-name vault-kms-session

aws sso login --profile sso-sb-util

aws ec2 describe-instances
aws ec2 describe-instances --profile sso-sb-util

# profile management
aws configure list
aws configure list --profile sso-sb-util
aws configure list-profiles
aws configure export-credentials
aws configure export-credentials --profile sso-sb-util
aws configure export-credentials --profile sso-sb-util --format env
source <(aws configure export-credentials --profile sso-sb-util --format env)
```
