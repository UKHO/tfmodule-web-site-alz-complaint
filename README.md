# tfmodule-web-site-alz-complaint

**Purpose:**
Produce an internal Terraform module for deploying Azure Web Apps with optional deployment slots, compliant with our corporate ALZ constraints.

Based on https://github.com/Azure/terraform-azurerm-avm-res-web-site

**Scope / Deliverables:**

* Terraform module using `azurerm` provider
* Supports deploying:

  * Web App (Linux or Windows, based on variable)
  * Optional set of slots (`0..N`)
* Inputs:

  * `os_type` (enum: `linux`/`windows`)
  * `site_config` object (pass-through to `azurerm_linux_web_app`/`azurerm_windows_web_app`)
  * Naming inputs (module must not enforce naming, only validate)
  * App Service Plan reference created
* Behaviours:

  * Slot names not constrained; user defines arbitrary slot names
  * Unlimited slots within reason
* Outputs:

  * Web App resource ID
  * Slot resource IDs
  * Hostnames
