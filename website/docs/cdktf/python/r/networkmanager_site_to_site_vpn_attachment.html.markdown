---
subcategory: "Network Manager"
layout: "aws"
page_title: "AWS: aws_networkmanager_site_to_site_vpn_attachment"
description: |-
  Terraform resource for managing an AWS Network Manager SiteToSiteAttachment.
---


<!-- Please do not edit this file, it is generated. -->
# Resource: aws_networkmanager_site_to_site_vpn_attachment

Terraform resource for managing an AWS Network Manager SiteToSiteAttachment.

## Example Usage

### Basic Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import Token, TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.networkmanager_site_to_site_vpn_attachment import NetworkmanagerSiteToSiteVpnAttachment
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        NetworkmanagerSiteToSiteVpnAttachment(self, "example",
            core_network_id=Token.as_string(awscc_networkmanager_core_network_example.id),
            vpn_connection_arn=Token.as_string(aws_vpn_connection_example.arn)
        )
```

### Full Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import Token, Fn, TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.customer_gateway import CustomerGateway
from imports.aws.data_aws_networkmanager_core_network_policy_document import DataAwsNetworkmanagerCoreNetworkPolicyDocument
from imports.aws.networkmanager_attachment_accepter import NetworkmanagerAttachmentAccepter
from imports.aws.networkmanager_global_network import NetworkmanagerGlobalNetwork
from imports.aws.networkmanager_site_to_site_vpn_attachment import NetworkmanagerSiteToSiteVpnAttachment
from imports.aws.vpn_connection import VpnConnection
from imports.awscc.networkmanager_core_network import NetworkmanagerCoreNetwork
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
        # The following providers are missing schema information and might need manual adjustments to synthesize correctly: awscc.
        #     For a more precise conversion please use the --provider flag in convert.
        test = CustomerGateway(self, "test",
            bgp_asn=Token.as_string(65000),
            ip_address="172.0.0.1",
            type="ipsec.1"
        )
        aws_networkmanager_global_network_test = NetworkmanagerGlobalNetwork(self, "test_1",
            tags={
                "Name": "test"
            }
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        aws_networkmanager_global_network_test.override_logical_id("test")
        aws_vpn_connection_test = VpnConnection(self, "test_2",
            customer_gateway_id=test.id,
            tags={
                "Name": "test"
            },
            type="ipsec.1"
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        aws_vpn_connection_test.override_logical_id("test")
        data_aws_networkmanager_core_network_policy_document_test =
        DataAwsNetworkmanagerCoreNetworkPolicyDocument(self, "test_3",
            attachment_policies=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentAttachmentPolicies(
                action=DataAwsNetworkmanagerCoreNetworkPolicyDocumentAttachmentPoliciesAction(
                    association_method="constant",
                    segment="shared"
                ),
                condition_logic="or",
                conditions=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentAttachmentPoliciesConditions(
                    key="segment",
                    operator="equals",
                    type="tag-value",
                    value="shared"
                )
                ],
                rule_number=1
            )
            ],
            core_network_configuration=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentCoreNetworkConfiguration(
                asn_ranges=["64512-64555"],
                edge_locations=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentCoreNetworkConfigurationEdgeLocations(
                    asn=Token.as_string(64512),
                    location=Token.as_string(current.name)
                )
                ],
                vpn_ecmp_support=False
            )
            ],
            segment_actions=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentSegmentActions(
                action="share",
                mode="attachment-route",
                segment="shared",
                share_with=["*"]
            )
            ],
            segments=[DataAwsNetworkmanagerCoreNetworkPolicyDocumentSegments(
                description="SegmentForSharedServices",
                name="shared",
                require_attachment_acceptance=True
            )
            ]
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        data_aws_networkmanager_core_network_policy_document_test.override_logical_id("test")
        awscc_networkmanager_core_network_test = NetworkmanagerCoreNetwork(self, "test_4",
            global_network_id=aws_networkmanager_global_network_test.id,
            policy_document=Fn.jsonencode(
                Fn.jsondecode(
                    Token.as_string(data_aws_networkmanager_core_network_policy_document_test.json)))
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        awscc_networkmanager_core_network_test.override_logical_id("test")
        aws_networkmanager_site_to_site_vpn_attachment_test =
        NetworkmanagerSiteToSiteVpnAttachment(self, "test_5",
            core_network_id=Token.as_string(awscc_networkmanager_core_network_test.id),
            tags={
                "segment": "shared"
            },
            vpn_connection_arn=Token.as_string(aws_vpn_connection_test.arn)
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        aws_networkmanager_site_to_site_vpn_attachment_test.override_logical_id("test")
        aws_networkmanager_attachment_accepter_test =
        NetworkmanagerAttachmentAccepter(self, "test_6",
            attachment_id=Token.as_string(aws_networkmanager_site_to_site_vpn_attachment_test.id),
            attachment_type=Token.as_string(aws_networkmanager_site_to_site_vpn_attachment_test.attachment_type)
        )
        # This allows the Terraform resource name to match the original name. You can remove the call if you don't need them to match.
        aws_networkmanager_attachment_accepter_test.override_logical_id("test")
```

## Argument Reference

The following arguments are required:

- `core_network_id` - (Required) The ID of a core network for the VPN attachment.
- `vpn_connection_arn` - (Required) The ARN of the site-to-site VPN connection.

The following arguments are optional:

- `tags` - (Optional) Key-value tags for the attachment. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

- `arn` - The ARN of the attachment.
- `attachment_policy_rule_number` - The policy rule number associated with the attachment.
- `attachment_type` - The type of attachment.
- `core_network_arn` - The ARN of a core network.
- `core_network_id` - The ID of a core network
- `edge_location` - The Region where the edge is located.
- `id` - The ID of the attachment.
- `owner_account_id` - The ID of the attachment account owner.
- `resource_arn` - The attachment resource ARN.
- `segment_name` - The name of the segment attachment.
- `state` - The state of the attachment.
- `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).

## Import

In Terraform v1.5.0 and later, use an [`import` block](https://developer.hashicorp.com/terraform/language/import) to import `aws_networkmanager_site_to_site_vpn_attachment` using the attachment ID. For example:

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import TerraformStack
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name):
        super().__init__(scope, name)
```

Using `terraform import`, import `aws_networkmanager_site_to_site_vpn_attachment` using the attachment ID. For example:

```console
% terraform import aws_networkmanager_site_to_site_vpn_attachment.example attachment-0f8fa60d2238d1bd8
```

<!-- cache-key: cdktf-0.20.0 input-e2c1657a1e8faf479a1e17a640451438473d4f57d01efa086cfe70b6d3e5057f -->