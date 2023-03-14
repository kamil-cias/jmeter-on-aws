# Distributed load testing on AWS with JMeter.
### The authors of the project
- [Kamil Ciaś, <kamil.cias@goto.systems>](https://github.com/kamil-cias)
___

[Log in via Project GO AWS SSO](https://projectgo.awsapps.com/start)

## How to use terraform with Project GO AWS SSO
Use terraform with aws sso in five steps:
- create an ***~/.aws/credentials*** file
```bash
mkdir /home/$USER/.aws
vim /home/$USER/.aws/credentials
```
- [log in via Project GO AWS SSO to the selected project - "Command line or developer access"](https://projectgo.awsapps.com/start)
- select option 2: "Add profile to AWS credentials file"
- paste the contents into the ***~/.aws/credentials*** file and save

next add the **ssoProfile** variable by taking it from the ***~/.aws/credentials*** file
```bash
grep -E '^\[' ~/.aws/credentials | sed 's/^.//;s/.$//'
```
```bash
# AWS SSO profile - variables.tf
variable "ssoProfile" {
	default = "952412373608_AdministratorAccess"
}
```
- use in the project directory
**Initial terraform**
```bash
terraform init
```
**Create terraform plan**
```bash
terraform plan
```
**Confirmation of changes**
```bash
terraform apply
```
**and finally, when we don't need infrastructure**
```bash
terraform destroy
```

> The *.tfstate and *.tfstate.backup file will be stored on AWS S3.

