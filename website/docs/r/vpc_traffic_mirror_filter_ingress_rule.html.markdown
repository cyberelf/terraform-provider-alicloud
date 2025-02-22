---
subcategory: "VPC"
layout: "alicloud"
page_title: "Alicloud: alicloud_vpc_traffic_mirror_filter_ingress_rule"
sidebar_current: "docs-alicloud-resource-vpc-traffic-mirror-filter-ingress-rule"
description: |-
  Provides a Alicloud VPC Traffic Mirror Filter Ingress Rule resource.
---

# alicloud\_vpc\_traffic\_mirror\_filter\_ingress\_rule

Provides a VPC Traffic Mirror Filter Ingress Rule resource.

For information about VPC Traffic Mirror Filter Ingress Rule and how to use it, see [What is Traffic Mirror Filter Ingress Rule](https://www.alibabacloud.com/help/doc-detail/261357.htm).

-> **NOTE:** Available in v1.141.0+.

## Example Usage

Basic Usage

```terraform
resource "alicloud_vpc_traffic_mirror_filter" "example" {
  traffic_mirror_filter_name = "example_value"
}

resource "alicloud_vpc_traffic_mirror_filter_ingress_rule" "example" {
  traffic_mirror_filter_id = alicloud_vpc_traffic_mirror_filter.example.id
  priority                 = "1"
  rule_action              = "accept"
  protocol                 = "UDP"
  destination_cidr_block   = "10.0.0.0/24"
  source_cidr_block        = "10.0.0.0/24"
  destination_port_range   = "1/120"
  source_port_range        = "1/120"
}

```

## Argument Reference

The following arguments are supported:

* `dry_run` - (Optional) Whether to pre-check this request only. Default to: `false`
* `destination_cidr_block` - (Optional) The destination CIDR block of the inbound traffic.
* `destination_port_range` - (Optional) The destination CIDR block of the inbound traffic. Valid values: `1` to `65535`. Separate the first port and last port with a forward slash (/), for example, `1/200` or `80/80`. A value of `-1/-1` indicates that all ports are available. Therefore, do not set the value to `-1/-1`. **NOTE:** When `protocol` is `ICMP`, this parameter is invalid.
* `priority` - (Optional) The priority of the inbound rule. A smaller value indicates a higher priority. The maximum value is `10`, which indicates that you can configure at most 10 inbound rules for a filter.
* `protocol` - (Optional) The transport protocol used by inbound traffic that needs to be mirrored. Valid values: `ALL`, `ICMP`, `TCP`, `UDP`.
* `rule_action` - (Optional) The collection policy of the inbound rule. Valid values: `accept` or `drop`. `accept`: collects network traffic. `drop`: does not collect network traffic.
* `source_cidr_block` - (Optional) The source CIDR block of the inbound traffic.
* `source_port_range` - (Optional) The source port range of the inbound traffic. Valid values: `1` to `65535`. Separate the first port and last port with a forward slash (/), for example, `1/200` or `80/80`. A value of `-1/-1` indicates that all ports are available. Therefore, do not set the value to `-1/-1`. **NOTE:** When `protocol` is `ICMP`, this parameter is invalid.
* `traffic_mirror_filter_id` - (Optional) The ID of the filter.

## Attributes Reference

The following attributes are exported:

* `id` - The ID of the rule. The value formats as `<traffic_mirror_filter_id>:<traffic_mirror_filter_ingress_rule_id>`.
* `status` - The state of the inbound rule. Valid values:`Creating`, `Created`, `Modifying` and `Deleting`.
* `traffic_mirror_filter_ingress_rule_id` - The ID of the inbound rule.

### Timeouts

The `timeouts` block allows you to specify [timeouts](https://www.terraform.io/docs/configuration-0-11/resources.html#timeouts) for certain actions:

* `create` - (Defaults to 1 mins) Used when create the Traffic Mirror Filter Ingress Rule.
* `update` - (Defaults to 1 mins) Used when update the Traffic Mirror Filter Ingress Rule.

## Import

VPC Traffic Mirror Filter Ingress Rule can be imported using the id, e.g.

```shell
$ terraform import alicloud_vpc_traffic_mirror_filter_ingress_rule.example <traffic_mirror_filter_id>:<traffic_mirror_filter_ingress_rule_id>
```
