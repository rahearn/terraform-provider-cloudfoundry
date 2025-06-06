---
page_title: "cloudfoundry_route Resource - terraform-provider-cloudfoundry"
subcategory: ""
description: |-
  Provides a Cloud Foundry resource for managing Cloud Foundry application routes.
---

# cloudfoundry_route (Resource)

Provides a Cloud Foundry resource for managing Cloud Foundry application routes.

## Example Usage

```terraform
resource "cloudfoundry_route" "bruh" {
  space  = "795a961c-6360-479a-9666-fff9cb906aad"
  domain = "440e24e5-ee11-41d9-a996-2ed0a1e2deea"
  host   = "testing123"
  path   = "/cart"
  destinations = [
    {
      app_id = "24a711f2-148b-4d48-b37a-90a66d6e842f"

    },
    {
      app_id           = "15a74002-cf3a-4bf2-b76f-fe96867c46ee"
      app_process_type = "web"
      port             = 36001
    },

  ]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `domain` (String) The domain guid associated to the route.
- `space` (String) The space guid associated to the route.

### Optional

- `annotations` (Map of String) The annotations associated with Cloud Foundry resources. Add as described [here](https://docs.cloudfoundry.org/adminguide/metadata.html#-view-metadata-for-an-object).
- `destinations` (Attributes Set) A destination represents the relationship between a route and a resource that can serve traffic. (see [below for nested schema](#nestedatt--destinations))
- `host` (String) The hostname for the route; not compatible with routes specifying the tcp protocol; must be either a wildcard (*) or be under 63 characters long and only contain letters, numbers, dashes (-) or underscores(_)
- `labels` (Map of String) The labels associated with Cloud Foundry resources. Add as described [here](https://docs.cloudfoundry.org/adminguide/metadata.html#-view-metadata-for-an-object).
- `path` (String) The path for the route; not compatible with routes specifying the tcp protocol; must be under 128 characters long and not contain question marks (?), begin with a slash (/) and not be exactly a slash (/).
- `port` (Number) The port that the route listens on. Only compatible with routes specifying the tcp protocol

### Read-Only

- `created_at` (String) The date and time when the resource was created in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.
- `id` (String) The GUID of the object.
- `protocol` (String) The protocol supported by the route, based on the route's domain configuration.
- `updated_at` (String) The date and time when the resource was updated in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) format.
- `url` (String) The URL for the route.

<a id="nestedatt--destinations"></a>
### Nested Schema for `destinations`

Optional:

- `app_id` (String) The GUID of the app to route traffic to.
- `app_process_type` (String) Type of the process belonging to the app to route traffic to.
- `port` (Number) Port on the destination process to route traffic to.
- `protocol` (String) Protocol to use for this destination.
- `weight` (Number) Percentage of traffic which will be routed to this destination.

Read-Only:

- `id` (String) The GUID of the object.

## Import

Import is supported using the following syntax:

```terraform
# terraform import cloudfoundry_route.<resource_name> <route_guid>

terraform import cloudfoundry_route.my_route 283f59d2-d660-45fb-9d96-b3e1aa92cfc7
```