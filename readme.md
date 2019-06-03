## This reposistory is created with learning purposes for Terraform, focusing on Terraform meta-parameters and especially on `count` meta parameter.

## Purpose :

- The repository provides simple introduction to Terraform meta-parameters and demonstrating the usage of `count` meta parameter.

## How to install terraform : 

- The information about installing terraform can be found on the HashiCorp website 
[here](https://learn.hashicorp.com/terraform/getting-started/install.html)

## What is Terraform State:

- Terraform uses a file to store the information about the infrastructure that has been provisioned, this file is called `state file`, it is called by default : `terraform.tfstate`. Terraform uses this file in order to plan, create and maintain resources, it is essential for normal operation of Terraform.
- Terraform state file is by default stored locally under the name `terraform.tfstate` but this might create problem when more than one person is working on the infrastructure. Lets suppose that two people are working on the same project, one of them runs `terraform apply` and creates `aws_instance`. When the second person who works on the same project but on his/her computer runs `terraform apply` , Terraform is going to try to update or create resources that have been already provisioned. This problem is address by using `remote state` storage, the two people share same `state` file. The storage might be S3 bucket for example. In order to tell Terraform to use remote state storage, `terraform` keyword should be used. Example : 
  ```
  terraform {
    backend "s3" {
      bucket = "BUCKET_NAME"
      key    = "path/to/my/key"
      region = "REGION"
    }
  }
  ```
- Last thing but not least thing to consider is security. The `state file` might contain some sensitive information, for example private keys. Having the `state file` at remote location should be considered encrypting the storage itself, since the `state file` is store in plain text (JSON). 

