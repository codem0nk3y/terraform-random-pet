# terraform-random-pet
Create a random pet in HashiCorp Terraform.

This configuration uses the `terraform_remote_state` datasource and native functions in Terraform to output a randomized pet name, of a length determined by a separate Terraform Cloud workspace configured to use https://github.com/vaficionado/terraform-random-integer as its source. The pet names will also be separated by a randomly generated separator string determined by a separate Terraform Cloud workspace using https://github.com/vaficionado/terraform-random-separator as its source.

To adjust the length of the integer, adjust the `min` and `max` values in https://github.com/vaficionado/terraform-random-integer/blob/master/main.tf

To adjust the separator configuration (length, character types, etc) adjust the `special`, `upper`, `lower`, and `number` values in https://github.com/vaficionado/terraform-random-separator/blob/master/main.tf

The function returns a single output of `pet` and requires three workspace variables to be configured as follows:
* `organization` : the name of the Terraform Cloud organization where the workspaces are configured
* `separator-workspace` : the name of the Terraform Cloud workspace where the `separator` output can be obtained (typically linked to https://github.com/vaficionado/terraform-random-separator)
* `length-workspace` : the name of the Terraform Cloud workspace where the `integer` output can be obtained (typically linked to https://github.com/vaficionado/terraform-random-integer)

For more information on how to link this configuration to a Terraform Cloud workspace, see this blog post:
https://www.hashicorp.com/blog/using-terraform-cloud-and-version-control-systems/

