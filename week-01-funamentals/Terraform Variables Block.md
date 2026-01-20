## Lab – Intro to Input Variables Block

### Purpose

Terraform **input variables** allow you to make your configurations **flexible and reusable** by replacing hard-coded values with parameters that can be set at runtime. This is a foundational step toward writing more robust, production-ready Terraform code. :contentReference[oaicite:0]{index=0}

---

## What Are Input Variables?

Input variables behave like **function parameters** in programming: they let you pass values into your Terraform configuration without modifying the source code itself. :contentReference[oaicite:1]{index=1}

A variable is declared using a `variable` block:

```hcl
variable "example_variable" {
  description = "A simple Terraform input variable"
  type        = string
  default     = "default_value"
}
```
description: explains how the variable should be used

type: constrains the kind of data the variable accepts

default: an optional fallback value when none is provided

Why Use Variables?

Using variables:

Removes hard-coded values such as region IDs, instance names, or CIDRs

Makes your code reusable across environments (dev/stage/prod)

Enables parameterization with CLI flags, .tfvars files, or environment variables

Without variables, a change like switching AWS regions would require editing the code itself — which isn’t ideal for automation or collaboration.

_________________________________

Referencing Variables

Once you declare a variable, you reference its value using var.<NAME>:
```
resource "aws_instance" "app" {
  ami           = var.ami_id
  instance_type = var.instance_type
}
```

In this example:

var.ami_id and var.instance_type are values passed into the configuration rather than hard-coded.

Terraform will prompt for required variable values that have no default when running terraform plan or terraform apply.

_________________________________

How Variable Values Are Provided

You can assign variable values in several ways:

1. Via AWS environment variables (e.g., TF_VAR_region)

2. CLI flags (e.g., terraform apply -var="region=us-east-1")

3. .tfvars files (e.g., terraform.tfvars or dev.tfvars)

4. Automatically via *.auto.tfvars patterns

Terraform determines the effective value by a precedence order — CLI input overrides .tfvars, which overrides defaults.

_________________________________

When Variables Are Required

If a variable has:

No default: Terraform will ask you to supply a value

A default: Terraform uses that value unless overridden

This ensures essential configuration values are provided before infrastructure is planned or created.

___________________________________

Key Takeaways

Input variables make Terraform configurations parameterizable and reusable.

Variables are declared in variable blocks and referenced using var.<NAME>.

Terraform supports different ways of supplying values, with clear precedence rules.

Proper use of variables is essential for writing code that can be deployed in multiple environments.
