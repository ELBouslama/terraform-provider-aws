---
subcategory: "Location"
layout: "aws"
page_title: "AWS: aws_location_map"
description: |-
    Retrieve information about a Location Service Map.
---


<!-- Please do not edit this file, it is generated. -->
# Data Source: aws_location_map

Retrieve information about a Location Service Map.

## Example Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.data_aws_location_map import DataAwsLocationMap
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        DataAwsLocationMap(self, "example",
            map_name="example"
        )
```

## Argument Reference

* `map_name` - (Required) Name of the map resource.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `configuration` - List of configurations that specify the map tile style selected from a partner data provider.
    * `style` - The map style selected from an available data provider.
* `create_time` - Timestamp for when the map resource was created in ISO 8601 format.
* `description` - Optional description for the map resource.
* `map_arn` - ARN for the map resource.
* `tags` - Key-value map of resource tags for the map.
* `update_time` - Timestamp for when the map resource was last updated in ISO 8601 format.

<!-- cache-key: cdktf-0.20.0 input-0b7e671677f6b40d5b7e281bcc7a2f6d4c9948b32cc48282e4c534b54ca5d4c4 -->