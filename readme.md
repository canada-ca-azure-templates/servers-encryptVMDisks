# Template Name

## Introduction

This template is used to [decrypt disks](<https://docs.microsoft.com/en-us/azure/security/azure-security-disk-encryption-windows>) on an existeing VM.

## Security Controls

The following security controls can be met through configuration of this template:

* None.

## Dependancies

The following items are assumed to exist already in the deployment:

* [Resource Group](<https://github.com/canada-ca-azure-templates/resourcegroups>)
* [KeyVault](<https://github.com/canada-ca-azure-templates/keyvaults>)
* [Server(s)](<https://github.com/canada-ca-azure-templates/servers>)

## Parameter format

```JSON
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "vmArray": {
            "value": [
                {
                    "vmResourceGroup": "AzPwS01-Infra-Temp-RG",
                    "vmName": "testencrypt",
                    "keyVaultResourceGroup": "AzPwS01-Infra-Temp-RG",
                    "keyVaultName": "AzPwS01-TST-Encr-KV"
                }
            ]
        }
    }
}
```

## Parameter Values

### Main Template

|Name        |Type   |Required |Value                               |
|------------|-------|---------|------------------------------------|
|containerSasToken |string |No      |A SaS token for the private blob storage |
|vmArray |array |Yes      |Array of [vm Object](###vm-object) to remove encryption from|

### vm object

|Name        |Type   |Required |Value                               |
|------------|-------|---------|------------------------------------|
|vmResourceGroup |string |Yes      |The resource group name the vm is in |
|vmName |string |Yes      |The name of the vm to remove the disk encryption from |
|keyVaultResourceGroup |string |Yes      |The resource group name of the keyvault |
|keyVaultName |string |Yes      |The name of the keyvault where the encryption keys are stored |

## History

|Date       |Release| Change                |
|-----------|-------|-----------------------|
|2019-02-07 |       |Intial versions|
|2019-05-08 |       |Updated documentation|
|20190522   |[20190522](https://github.com/canada-ca-azure-templates/vnet-peering/tree/20190522)|Updated tests and moved to new github repo|