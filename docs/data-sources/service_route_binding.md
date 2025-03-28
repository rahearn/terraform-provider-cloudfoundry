---
page_title: "cloudfoundry_service_route_binding Data Source - terraform-provider-cloudfoundry"
subcategory: ""
description: |-
  Gets information on a Service Route Binding.
---

# cloudfoundry_service_route_binding (Data Source)

Gets information on a Service Route Binding.

## Example Usage

```terraform
data "cloudfoundry_service_route_binding" "rb" {
  id = "ab65cad9-73fa-4dd4-9c09-87f89b2e77ec"
}

output "binding" {
  value = data.cloudfoundry_service_route_binding.rb
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `id` (String) The GUID of the service route binding

### Optional

- `annotations` (Map of String) The annotations associated with Cloud Foundry resources. Add as described [here](https://docs.cloudfoundry.org/adminguide/metadata.html#-view-metadata-for-an-object).
- `labels` (Map of String) The labels associated with Cloud Foundry resources. Add as described [here](https://docs.cloudfoundry.org/adminguide/metadata.html#-view-metadata-for-an-object).

### Read-Only

- `created_at` (String) The date and time when the resource was created in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.
- `last_operation` (Attributes) The details of the last operation performed on the resource (see [below for nested schema](#nestedatt--last_operation))
- `route` (String) The GUID of the route to be bound
- `route_service_url` (String) The URL for the route service.
- `service_instance` (String) The service instance that the route is bound to
- `updated_at` (String) The date and time when the resource was updated in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.

<a id="nestedatt--last_operation"></a>
### Nested Schema for `last_operation`

Read-Only:

- `created_at` (String) The time at which the last operation was created
- `description` (String) A description of the last operation
- `state` (String) The state of the last operation
- `type` (String) The type of the last operation
- `updated_at` (String) The time at which the last operation was updated