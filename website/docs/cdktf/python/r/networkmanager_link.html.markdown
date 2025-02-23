---
subcategory: "Network Manager"
layout: "aws"
page_title: "AWS: aws_networkmanager_link"
description: |-
  Creates a link for a site.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_networkmanager_link

Creates a link for a site.

## Example Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import Token, TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.networkmanager_link import NetworkmanagerLink
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        NetworkmanagerLink(self, "example",
            bandwidth=NetworkmanagerLinkBandwidth(
                download_speed=50,
                upload_speed=10
            ),
            global_network_id=Token.as_string(aws_networkmanager_global_network_example.id),
            provider_name="MegaCorp",
            site_id=Token.as_string(aws_networkmanager_site_example.id)
        )
```

## Argument Reference

This resource supports the following arguments:

* `bandwidth` - (Required) The upload speed and download speed in Mbps. Documented below.
* `description` - (Optional) A description of the link.
* `global_network_id` - (Required) The ID of the global network.
* `provider_name` - (Optional) The provider of the link.
* `site_id` - (Required) The ID of the site.
* `tags` - (Optional) Key-value tags for the link. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.
* `type` - (Optional) The type of the link.

The `bandwidth` object supports the following:

* `download_speed` - (Optional) Download speed in Mbps.
* `upload_speed` - (Optional) Upload speed in Mbps.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `arn` - Link Amazon Resource Name (ARN).
* `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import `aws_networkmanager_link` using the link ARN. For example:

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
```

Using `terraform import`, import `aws_networkmanager_link` using the link ARN. For example:

```console
% terraform import aws_networkmanager_link.example arn:aws:networkmanager::123456789012:link/global-network-0d47f6t230mz46dy4/link-444555aaabbb11223
```

<!-- cache-key: cdktf-0.20.0 input-b3264437514e087e6c9a780921c3cabb87dacb7cfc4e78ab6211866e572c1219 -->