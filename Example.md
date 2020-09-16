# Akamai Terraform Provider
The Akamai Terraform Provider is used to interact with Akamai and manage solutions for content delivery, security, and performance.

Last updated: July 2020


## Prerequisites

*** 
<br/>
The Akamai Terraform Provider is used to interact with Akamai and manage solutions for content delivery, security, and performance.

* Create an Akamai API Client with the right permissions and valid credentials to authenticate your Akamai Terraform files. Your Akamai API Client will require read-write permissions to either the Property Manager API, DNS API and/or Traffic Management API depending on your use-case for using the Akamai Terraform Provider.

* Either import existing configurations with the Akamai Terraform CLI or start from scratch with code examples. Note: Both Terraform and the Akamai Terraform CLI package come pre-installed in the Akamai Development Environment. Get more details in our installation Instructions.

* Run the terraform init command to load the Akamai Terraform Provider.

* Run the terraform plan or terraform apply command to run your Terraform configuration.

Use the navigation to the left to read about the available resources available in the Akamai Terraform Provider.

## Authenticating Akamai Terraform configurations
***
<br/>
Authentication of Terraform configurations relies on the Akamai EdgeGrid authentication scheme. The Akamai Terraform Provider code acts as a wrapper for our APIs and re-uses the same authentication mechanism. Note: We recommend storing your API credentials in a local .edgerc file.

Your Akamai API Client will require read-write permissions to either the Property Manager API, DNS API and/or Traffic Management API depending on your use-case for using the Akamai Terraform Provider. Note: Without these permissions, your Terraform configurations won’t execute.

The local .edgerc file can be referenced in the top of the Akamai Terraform configuration with edgerc = "~/.edgerc". Note: ~/.edgerc is the location of your file on your local machine. You are able to reference individual sections inside the .edgerc file by referencing papi_section = "default". Note: "default" is the name of the section stored in brackets in your .edgerc file.
## Example Usage

*** 
***
<br/>
<!-- + text + --> # Configure the Akamai Provider
<p> provider "akamai" {
<p> edgerc = "~/.edgerc"
<p> papi_section = "papi"
<p> dns_section = "dns"
<p> gtm_section = "gtm"
}


### Argument Reference
<br/>

The following arguments are supported in the >provider> block:

* [edgerc](https://registry.terraform.io/providers/akamai/akamai/latest/docs#edgerc) - (Optional) The location of the .edgerc file containing credentials. Default: $HOME/.edgerc

* [property_section](https://registry.terraform.io/providers/akamai/akamai/latest/docs#property_section) — (Optional) The credential section to use for the Property Manager API (PAPI). Default: default.
* [dns_section](https://registry.terraform.io/providers/akamai/akamai/latest/docs#dns_section) — (Optional) The credential section to use for the Config DNS API. Default: default.
* [gtm_section](https://registry.terraform.io/providers/akamai/akamai/latest/docs#gtm_section) — (Optional) The credential section to use for the Config GTM API. Default: default.

## Additional Authentication Method - Inline Credentials
Outside of referencing a local .edgerc file, you can specify credentials inline for each service used. Currently the provider supports property (PAPI), dns and gtm services.

To specify credentials inline, use the property or dns block to define credentials.

### Argument Reference
* property — (Optional) Provide credentials for the Property Manager API (papi)
    * host — (Required) The credential hostname
    *  access_token — (Required) The credential access_token
    * client_token — (Required) The credential client_token
    * client_secret — (Required) The credential client_secret
    * max_body — (Optional) The credential max body to sign (in bytes, Default: 131072)