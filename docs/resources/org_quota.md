---
page_title: "cloudfoundry_org_quota Resource - terraform-provider-cloudfoundry"
subcategory: ""
description: |-
  Provides a Cloud Foundry resource to manage org quota definitions.
---

# cloudfoundry_org_quota (Resource)

Provides a Cloud Foundry resource to manage org quota definitions.

## Example Usage

```terraform
terraform {
  required_providers {
    cloudfoundry = {
      source = "cloudfoundry/cloudfoundry"
    }
  }
}
provider "cloudfoundry" {}

resource "cloudfoundry_org_quota" "org_quota" {
  name                     = "tf-test-do-not-delete"
  allow_paid_service_plans = true
  instance_memory          = 2048
  total_memory             = 51200
  total_app_instances      = 100
  total_routes             = 50
  total_services           = 200
  total_service_keys       = 120
  total_private_domains    = 40
  total_app_tasks          = 10
  total_route_ports        = 5
  total_app_log_rate_limit = 1000
  orgs = [
    "ba10cc63-cc43-46b1-a00c-5f2a0d7d992e",
  ]
}

output "guid" {
  value = resource.cloudfoundry_org_quota.org_quota.id
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `allow_paid_service_plans` (Boolean) Determines whether users can provision instances of non-free service plans. Does not control plan visibility. When false, non-free service plans may be visible in the marketplace but instances can not be provisioned.
- `name` (String) The name you use to identify the quota or plan in Cloud Foundry

### Optional

- `instance_memory` (Number) Maximum memory per application instance.
- `orgs` (Set of String) Set of Org GUIDs to which this org quota would be assigned.
- `total_app_instances` (Number) Maximum app instances allowed.
- `total_app_log_rate_limit` (Number) Maximum log rate allowed for all the started processes and running tasks in bytes/second.
- `total_app_tasks` (Number) Maximum tasks allowed per app.
- `total_memory` (Number) Maximum memory usage allowed.
- `total_private_domains` (Number) Maximum number of private domains allowed to be created within the Org.
- `total_route_ports` (Number) Maximum routes with reserved ports.
- `total_routes` (Number) Maximum routes allowed.
- `total_service_keys` (Number) Maximum service keys allowed.
- `total_services` (Number) Maximum services allowed.

### Read-Only

- `created_at` (String) The date and time when the resource was created in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.
- `id` (String) The GUID of the object.
- `updated_at` (String) The date and time when the resource was updated in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.

## Import

Import is supported using the following syntax:

```terraform
# terraform import cloudfoundry_org_quota.<resource_name> <org_quota_guid>

terraform import cloudfoundry_org_quota.my_org_quota e3cef997-9ba5-4cb4-b25b-c79faa81a33f
```