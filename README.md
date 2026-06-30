# Terraform AWS Static Website

This project demonstrates how to provision and deploy a static website on AWS using Terraform. Instead of manually creating AWS resources through the AWS Management Console, the infrastructure is defined as code, making deployments repeatable, consistent, and version-controlled.

---

## Technologies

* Terraform
* AWS S3
* AWS IAM
* AWS CLI
* Git
* GitHub

---

## Project Structure

```text
terraform-aws-static-website
├── website
│   ├── index.html
│   └── style.css
├── screenshots
├── provider.tf
├── variables.tf
├── main.tf
├── outputs.tf
├── terraform.tfvars
├── .gitignore
└── README.md
```

---

## Infrastructure

This project provisions:

* Amazon S3 Bucket
* Static Website Hosting
* Public Access Configuration
* Bucket Policy
* Website File Upload (HTML & CSS)
* Terraform Outputs

---

## Terraform Workflow

### Project Structure

![Project Structure](screenshots/01-project-structure.png)

---

### Configure AWS Provider and Variables

![Provider and Variables](screenshots/02-provider-and-variables.png)

The AWS provider and reusable variables were configured before creating any infrastructure.

---

### Initialize Terraform

```bash
terraform init
```

![Terraform Init](screenshots/03-terraform-init-success.png)

---

### Create the S3 Bucket Resource

![First Resource](screenshots/04-first-resource.png)

The first Terraform resource provisions an Amazon S3 bucket that will host the website.

---

### Configure Static Website Hosting

![Static Website Configuration](screenshots/05-static-website-configuration.png)

The bucket is configured to serve static website content.

---

### Configure Public Access

![Public Access](screenshots/06-public-access-block.png)

Public access settings were updated to allow website hosting.

---

### Create the Bucket Policy

![Bucket Policy](screenshots/07-bucket-policy.png)

A bucket policy grants public read access to the website files.

---

### Upload Website Files

![S3 Objects](screenshots/08-s3-objects.png)

Terraform uploads the HTML and CSS files directly into Amazon S3.

---

### Website Source Files

![Website Files](screenshots/09-website-files.png)

The website consists of a simple HTML page styled with CSS.

---

### Configure Terraform Outputs

![Outputs](screenshots/10-outputs.png)

Outputs return useful deployment information such as the bucket name and website URL.

---

### Validate the Configuration

```bash
terraform validate
```

![Terraform Validate](screenshots/11-terraform-validate.png)

Terraform confirmed that the configuration was valid.

---

### Troubleshoot AWS Credentials

![Credential Error](screenshots/12-terraform-plan-credential-error.png)

During the first deployment attempt, Terraform could not authenticate because the AWS CLI credentials were invalid. After updating the AWS CLI configuration, Terraform was able to communicate with AWS successfully.

---

### Verify AWS CLI Connection

```bash
aws sts get-caller-identity
```

![AWS CLI Connected](screenshots/13-aws-cli-connected.png)

This command verified that the AWS CLI was correctly authenticated.

---

### Review the Deployment Plan

```bash
terraform plan
```

![Terraform Plan](screenshots/14-terraform-plan.png)

Terraform displayed the execution plan showing the resources that would be created.

---

### Resolve IAM Permissions

![IAM Permission Error](screenshots/15-terraform-apply-access-denied.png)

The initial deployment failed because the IAM user did not have permission to create an S3 bucket. After the required permissions were added, the deployment completed successfully.

---

### Deploy the Infrastructure

```bash
terraform apply
```

![Terraform Apply](screenshots/16-terraform-apply-success.png)

Terraform successfully provisioned the AWS infrastructure.

---

### Live Website

![Live Website](screenshots/17-website-live.png)

The website was successfully deployed and accessible through the S3 static website endpoint.

---

### Terraform Outputs

```bash
terraform output
```

![Terraform Outputs](screenshots/18-terraform-outputs.png)

Terraform displayed the deployment outputs, including the bucket name and website URL.

---

## What I Learned

* Provisioning AWS infrastructure using Terraform
* Creating and configuring Amazon S3 buckets
* Hosting static websites with Amazon S3
* Managing infrastructure with Infrastructure as Code (IaC)
* Using Terraform variables and outputs
* Configuring AWS CLI credentials
* Troubleshooting IAM permission issues
* Deploying cloud infrastructure in a repeatable way

---

## Future Improvements

* Add CloudFront for content delivery
* Configure a custom domain with Route 53
* Enable HTTPS using AWS Certificate Manager
* Store Terraform state remotely in an S3 backend
* Automate deployments with GitHub Actions
