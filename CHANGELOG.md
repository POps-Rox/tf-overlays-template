# v2.0.0 - 2026-05-11

### Changed

- **BREAKING**: Bumped `azurerm` provider to `~> 4.20` (was `~> 3.116`) in root and both `examples/*/example_new_rg/versions.tf`.
- **BREAKING**: Bumped Terraform `required_version` to `>= 1.10` (was `>= 1.9`).
- Declared `azapi ~> 2.0` and kept `popsrox POps-Rox/azutils ~> 1.0` in `required_providers` for fleet alignment.
- `azurerm_subnet.snet_ep`: replaced deprecated `private_endpoint_network_policies_enabled = true` with `private_endpoint_network_policies = "Enabled"` (4.x rename: bool argument → string enum).
- Examples: refreshed `versions.tf` to match the fleet baseline and pruned stale `output "echo_text"` references that pointed at a non-existent `module.echo` (latent on `main`; replaced with a placeholder comment).
- Added `VERSION` file at `2.0.0`.

### Migration notes

- Consumers must set `ARM_SUBSCRIPTION_ID` (or `provider "azurerm" { subscription_id = ... }`) — azurerm 4.x makes this mandatory.
- Transitive sibling overlays (`terraform-az-overlays-azregionslookup`, `-resourcegroup`) still pin `azurerm ~> 3.116` on `main`. Local validation used the codemod-doc workaround (`terraform get` + in-place patch of `.terraform/modules/**/versions.tf`) to confirm HCL correctness. CI will pass cleanly once those sibling overlays publish 4.x-compatible releases.

# v1.1.0 - 2026-03-26

Changed
- Bumped minimum Terraform version from `>= 1.3` to `>= 1.9` (breaking for callers running Terraform < 1.9)
- Bumped azurerm provider constraint from `~> 3.22` to `~> 3.116`

# v1.0.0 - <date>

Added
- Add Something you added
