---

layout: "fastly"
page_title: "Fastly: fastly_tls_private_key"
sidebar_current: "docs-fastly-datasource-tls_private_key"
description: |-
  Get information on a TLS Private Key.
---

# fastly_tls_private_key

Use this data source to get information on a TLS Private Key uploaded to Fastly.

~> **Warning:** The data source's filters are applied using an **AND** boolean operator, so depending on the combination
 of filters, they may become mutually exclusive. The exception to this is `id` which must not be specified in combination
 with any of the others.

~> **Note:** If more or less than a single match is returned by the search, Terraform will fail. Ensure that your search
 is specific enough to return a single key.

## Example Usage

```hcl
data "fastly_tls_private_key" "demo" {
  name = "demo-private-key"
}

output "private_key_needs_replacing" {
  value = data.fastly_tls_private_key.demo.replace
}
```
<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- **created_at** (String) Timestamp (GMT) when the private key was created.
- **id** (String) Fastly private key ID. Conflicts with all the other filters
- **key_length** (Number) The key length used to generate the private key.
- **key_type** (String) The algorithm used to generate the private key. Must be RSA.
- **name** (String) The human-readable name assigned to the private key when uploaded.
- **public_key_sha1** (String) A hash of the associated public key, useful for safely identifying it.

### Read-Only

- **replace** (Boolean) Whether Fastly recommends replacing this private key.