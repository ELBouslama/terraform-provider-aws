---
subcategory: "CloudWatch Logs"
layout: "aws"
page_title: "AWS: aws_cloudwatch_log_metric_filter"
description: |-
  Provides a CloudWatch Log Metric Filter resource.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_cloudwatch_log_metric_filter

Provides a CloudWatch Log Metric Filter resource.

## Example Usage

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
/*
 * Provider bindings are generated by running `cdktf get`.
 * See https://cdk.tf/provider-generation for more details.
 */
import { CloudwatchLogGroup } from "./.gen/providers/aws/cloudwatch-log-group";
import { CloudwatchLogMetricFilter } from "./.gen/providers/aws/cloudwatch-log-metric-filter";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
    const dada = new CloudwatchLogGroup(this, "dada", {
      name: "MyApp/access.log",
    });
    new CloudwatchLogMetricFilter(this, "yada", {
      logGroupName: dada.name,
      metricTransformation: {
        name: "EventCount",
        namespace: "YourNamespace",
        value: "1",
      },
      name: "MyAppAccessCount",
      pattern: "",
    });
  }
}

```

## Argument Reference

This resource supports the following arguments:

* `name` - (Required) A name for the metric filter.
* `pattern` - (Required) A valid [CloudWatch Logs filter pattern](https://docs.aws.amazon.com/AmazonCloudWatch/latest/DeveloperGuide/FilterAndPatternSyntax.html)
  for extracting metric data out of ingested log events.
* `logGroupName` - (Required) The name of the log group to associate the metric filter with.
* `metricTransformation` - (Required) A block defining collection of information needed to define how metric data gets emitted. See below.

The `metricTransformation` block supports the following arguments:

* `name` - (Required) The name of the CloudWatch metric to which the monitored log information should be published (e.g., `ErrorCount`)
* `namespace` - (Required) The destination namespace of the CloudWatch metric.
* `value` - (Required) What to publish to the metric. For example, if you're counting the occurrences of a particular term like "Error", the value will be "1" for each occurrence. If you're counting the bytes transferred the published value will be the value in the log event.
* `defaultValue` - (Optional) The value to emit when a filter pattern does not match a log event. Conflicts with `dimensions`.
* `dimensions` - (Optional) Map of fields to use as dimensions for the metric. Up to 3 dimensions are allowed. Conflicts with `defaultValue`.
* `unit` - (Optional) The unit to assign to the metric. If you omit this, the unit is set as `None`.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The name of the metric filter.

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import CloudWatch Log Metric Filter using the `log_group_name:name`. For example:

```typescript
// DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
import { Construct } from "constructs";
import { TerraformStack } from "cdktf";
class MyConvertedCode extends TerraformStack {
  constructor(scope: Construct, name: string) {
    super(scope, name);
  }
}

```

Using `terraform import`, import CloudWatch Log Metric Filter using the `log_group_name:name`. For example:

```console
% terraform import aws_cloudwatch_log_metric_filter.test /aws/lambda/function:test
```

<!-- cache-key: cdktf-0.20.0 input-c3539b00aea6703f03f30c699d9e6682c77afa8c2025da9bd2bce0e294523841 -->