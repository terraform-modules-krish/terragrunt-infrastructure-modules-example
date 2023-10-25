***WARNING: THIS REPO IS AN AUTO-GENERATED COPY.*** *This repo has been copied from [Gruntwork’s](https://gruntwork.io/) GitHub repositories so that you can consume it from your company’s own internal Git repositories. This copy is automatically created and updated by the `repo-copier` CLI tool. If you need to make changes to this repo, you should make the changes in a separate fork, and NOT make changes directly in this repo, as otherwise, the `repo-copier` will overwrite your changes! Please see the `repo-copier` [documentation](https://github.com/terraform-modules-krish/repo-copier) for more information on how the code is copied, how cross-references are updated, how the changelog is handled, etc.*

***

_You may find it valuable to view the following resources in the original repo. If these links give you a 404, visit https://app.gruntwork.io to gain access or email support@gruntwork.io if you need assistance._

[Home Page](https://github.com/gruntwork-io/terragrunt-infrastructure-modules-example/) |
[Pull Requests](https://github.com/gruntwork-io/terragrunt-infrastructure-modules-example/pulls) |
[Issues](https://github.com/gruntwork-io/terragrunt-infrastructure-modules-example/issues) |
[Releases and Assets](https://github.com/gruntwork-io/terragrunt-infrastructure-modules-example/releases)

_Alternatively, you can view a copied version of the resources listed above._

[Pull Requests](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/master/.github/PULL_REQUESTS.md) |
[Issues](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/master/.github/ISSUES.md) |
[ChangeLog](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/master/.github/CHANGELOG.md)

***

[![Maintained by Gruntwork.io](https://img.shields.io/badge/maintained%20by-gruntwork.io-%235849a6.svg)](https://gruntwork.io/?ref=repo_terragrunt-infra-modules-example)

# Example infrastructure-modules for Terragrunt

This repo, along with the [terragrunt-infrastructure-live-example 
repo](https://github.com/terraform-modules-krish/terragrunt-infrastructure-live-example), show an example file/folder structure
you can use with [Terragrunt](https://github.com/terraform-modules-krish/terragrunt) to keep your 
[Terraform](https://www.terraform.io) code DRY. For background information, check out the [Keep your Terraform code
DRY](https://github.com/terraform-modules-krish/terragrunt#keep-your-terraform-code-dry) section of the Terragrunt documentation.

This repo contains the following example code:

* [asg-elb-service](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/v0.1.0/asg-elb-service): An example of how to deploy an Auto Scaling Group (ASG) with an Elastic Load 
  Balancer (ELB) in front of it. We run a dirt-simple "web server" on top of the ASG that always returns "Hello, World".

* [mysql](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/v0.1.0/mysql): An example of how to deploy MySQL on top of Amazon's Relational Database Service (RDS).  

Note: This code is solely for demonstration purposes. This is not production-ready code, so use at your own risk. If 
you are interested in battle-tested, production-ready Terraform code, check out [Gruntwork](http://www.gruntwork.io/).





## How do you use these modules?

To use a module, create a  `terragrunt.hcl` file that specifies the module you want to use as well as values for the
input variables of that module:

```hcl
# Use Terragrunt to download the module code
terraform {
  source = "git::git@github.com:gruntwork-io/terragrunt-infrastructure-modules-example.git//path/to/module?ref=v0.0.1"
}

# Fill in the variables for that module
inputs = {
  foo = "bar"
  baz = 3
}
```

(*Note: the double slash (`//`) in the `source` URL is intentional and required. It's part of Terraform's Git syntax 
for [module sources](https://www.terraform.io/docs/modules/sources.html).*)

You then run [Terragrunt](https://github.com/terraform-modules-krish/terragrunt), and it will download the source code specified 
in the `source` URL into a temporary folder, copy your `terragrunt.hcl` file into that folder, and run your Terraform 
command in that folder: 

```
> terragrunt apply
[terragrunt] Reading Terragrunt config file at terragrunt.hcl
[terragrunt] Downloading Terraform configurations from git::git@github.com:gruntwork-io/terragrunt-infrastructure-modules-example.git//path/to/module?ref=v0.0.1
[terragrunt] Copying files from . into .terragrunt-cache
[terragrunt] Running command: terraform apply
[...]
```

Check out the [terragrunt-infrastructure-live-example 
repo](https://github.com/terraform-modules-krish/terragrunt-infrastructure-live-example) for examples and the [Keep your Terraform 
code DRY documentation](https://github.com/terraform-modules-krish/terragrunt#keep-your-terraform-code-dry) for more info.





## How do you change a module?


### Local changes

Here is how to test out changes to a module locally:

1. `git clone` this repo.
1. Update the code as necessary.
1. Go into the folder where you have the `terragrunt.hcl` file that uses a module from this repo (preferably for a 
   dev or staging environment!).
1. Run `terragrunt plan --terragrunt-source <LOCAL_PATH>`, where `LOCAL_PATH` is the path to your local checkout of
   the module code. 
1. If the plan looks good, run `terragrunt apply --terragrunt-source <LOCAL_PATH>`.   

Using the `--terragrunt-source` parameter (or `TERRAGRUNT_SOURCE` environment variable) allows you to do rapid, 
iterative, make-a-change-and-rerun development.


### Releasing a new version

When you're done testing the changes locally, here is how you release a new version:

1. Update the code as necessary.
1. Commit your changes to Git: `git commit -m "commit message"`.
1. Add a new Git tag using one of the following options:
    1. Using GitHub: Go to the [releases page](https://github.com/terraform-modules-krish/terragrunt-infrastructure-modules-example/blob/v0.1.0/releases) and click "Draft a new release".
    1. Using Git:

    ```
    git tag -a v0.0.2 -m "tag message"
    git push --follow-tags
    ```
1. Now you can use the new Git tag (e.g. `v0.0.2`) in the `ref` attribute of the `source` URL in `terragrunt.hcl`.
1. Run `terragrunt plan`.
1. If the plan looks good, run `terragrunt apply`.
