# tg-properties-aws-module-skeleton

This repository contains bare minimum code necessary to generate the properties configuration(variables, and git tags) for deploying `s3-bucket` to aws cloud platform.

This repository is intended to be used by developers wanting to write terragrunt configurations to deploy the terraform modules to `aws cloud platform`.

The terragrunt configurations(once fully generated) provide s3 bucket where remote state will be stored by terraform, provide configuration, and DRY terragrunt code to deploy the terraform modules.

# How to use this repository

1. Clone this repository on local workstation.
2. Make changes to `skeleton.yaml` file specific to your project/configurations.
3. Run make target `make configure`
4. Run make target `make terragrunt/properties/generate`

Steps above should create terragrunt configurations that will be used in conjuction with configurations provided via `tg-aws-module-skeleton` repository (which provides terragrunt configurations).

# skeleton.yaml schema and content

This is sample schema of the `skeleton.yaml` file

```
envs:
  - <<environment name>>:
      regions:
        - <<region_1>>:
            instances:
              - "<<instance number>>"
      git_tag: <<git tag of the terraform repository>>
```

`skeleton.yaml`(located at the root of the repository) is example file that generates proprties files and empty `terraform.tfvars` for `dev`, `qa`, `uat`, `prod` environments, one instance each ("000") in `us-east-2` region. `terraform.tfvars` should be filled in by developers with appropriate variables necessary to deploy the terraform code.