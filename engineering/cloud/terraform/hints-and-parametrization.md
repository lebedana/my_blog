# Hints and Parametrization

Parametrize using modules and input variables 

{% embed url="https://www.terraform.io/docs/modules/usage.html\#multiple-instances-of-a-module" %}

{% embed url="https://github.com/terraform-providers/terraform-provider-oci/issues/290" %}

### Loops and count 

Dynamic blocks \(from [https://www.hashicorp.com/blog/hashicorp-terraform-0-12-preview-for-and-for-each/](https://www.hashicorp.com/blog/hashicorp-terraform-0-12-preview-for-and-for-each/)\):

```text
# Configuration for Terraform v0.12

variable "subnets" {
  default = [
    {
      name   = "a"
      number = 1
    },
    {
      name   = "b"
      number = 2
    },
    {
      name   = "c"
      number = 3
    },
  ]
}

locals {
  base_cidr_block = "10.0.0.0/16"
}

resource "azurerm_virtual_network" "example" {
  name                = "example-network"
  resource_group_name = azurerm_resource_group.test.name
  address_space       = [local.base_cidr_block]
  location            = "West US"

  dynamic "subnet" {
    for_each = [for s in subnets: {
      name   = s.name
      prefix = cidrsubnet(local.base_cidr_block, 4, s.number)
    }]

    content {
      name           = subnet.value.name
      address_prefix = subnet.value.prefix
    }
  }
}
```

#### Flatten 

{% embed url="https://www.terraform.io/docs/configuration/functions/flatten.html" %}



#### Count

From \[terraform book\]\([https://terraformbook.com/TheTerraformBook\_sample.pdf](https://terraformbook.com/TheTerraformBook_sample.pdf)\):

Listing 3.66: Looking up the count index 

`resource "aws_instance" "web" { . . .   
  private_ip = var.instance_ips[count.index] . . .   
  count = length(var.instance_ips)   
}`

### Conditions

Listing 3.75: Using ternary with count

`count = var.environment == "production" ? 4 : 2`

