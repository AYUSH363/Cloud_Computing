# Terraform

## 1. Install Homebrew (if not installed)
~~~bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
~~~
## 2. Install Terraform using Homebrew
~~~bash
brew tap hashicorp/tap
brew install hashicorp/tap/terraform
~~~
## 3. Verify Terraform Installation
~~~bash
terraform -version
~~~
# AWS CLI Installation  
## 1. Install AWS CLI using Homebrew
~~~bash
brew install awscli
~~~
## 2. Verify AWS CLI Installation
   ~~~bash
   aws --version
~~~
# AWS Setup
## 1. Configure AWS Credentials
~~~bash
aws configure
~~~
It will prompt you to enter:

AWS Access Key ID
AWS Secret Access Key
Default region (e.g., us-east-1, ap-south-1)
Output format (default: json)
<img width="790" alt="Screenshot 2025-03-24 at 12 30 01 AM" src="https://github.com/user-attachments/assets/67519ca3-f5f0-4897-9d95-99be0d90da40" />


# Creating and Deploying an EC2 Instance Using Terraform
## 1. Create a new directory for your Terraform project
~~~bash
mkdir terraform-ec2 && cd terraform-ec2
~~~
## 2. Create the Terraform configuration file
~~~bash
nano main.tf
~~~

Paste the following content:
~~~bash
provider "aws" {
  profile = "default"
  region  = "ap-south-1"
}

resource "aws_instance" "my_instance" {
  ami           = "ami-0cbf43fd299e3a464"
  instance_type = "t2.micro"

  tags = {
    Name = "MacTerraformInstance"
  }
}
~~~
Save and exit.

# Initializing and Applying Terraform

## 1. Initialize Terraform
~~~bash
terraform init

~~~
<img width="598" alt="Screenshot 2025-03-23 at 11 51 29 PM" src="https://github.com/user-attachments/assets/00238693-fe6d-4b62-a84e-52f9f3b991fe" />


## 2. Check Execution Plan
~~~bash
terraform plan
~~~

## 3. Deploy the EC2 Instance
~~~bash
terraform apply -auto-approve

~~~
<img width="790" alt="Screenshot 2025-03-24 at 12 11 04 AM" src="https://github.com/user-attachments/assets/82fd5c26-9da2-40a9-88c4-763d146cf6cd" />

