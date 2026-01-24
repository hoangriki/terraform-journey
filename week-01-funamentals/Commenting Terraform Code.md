Lab: Commenting Terraform Code

To make our code easier to understand for others who might want to contribute we may want to add a comment to explain what a resource or a particular code block is doing. The Terraform language supports three different syntaxes for comments:

# begins a single-line comment, ending at the end of the line.

// also begins a single-line comment, as an alternative to #.

/* and */ are start and end delimiters for a comment that might span over multiple lines.

    Task 1: Add Single Line Comment to Terraform Configuration
    Task 2: Add Multi-Line Comment to Terraform Configuration

Task 1: Add Single Line Comment to Terraform Configuration

Update your main.tf to include a single line comment at the top of your file.

# IaC Buildout for Terraform Associate Exam

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}

Run a terraform plan to validate that adding a single line comment has no effect on the configuration and thus will return a No Change plan.

terraform plan

No changes. Infrastructure is up-to-date.

    Note: There is no harm in running a terraform plan after adding any items into a Terraform configuration file. In fact it can be quite useful to run to validate that your configuration changes will not have any impact on your deployments.

Task 2: Add Multi-Line Comment to Terraform Configuration

Update your main.tf to include a single line comment at the top of your file.

/*
Name: IaC Buildout for Terraform Associate Exam
Description: AWS Infrastructure Buildout
Contributors: Bryan and Gabe
*/

# Configure the AWS Provider
provider "aws" {
  region = "us-east-1"
}

Run a terraform plan to validate that adding a single line comment has no effect on the configuration and thus will return a No Change plan.

terraform plan

No changes. Infrastructure is up-to-date.

The # single-line comment style is the default comment style and should be used in most cases. Automatic configuration formatting tools may automatically transform // comments into # comments, since the double-slash style is not idiomatic.
Reference

Terraform HCL Comments
