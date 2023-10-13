---
tags:
  - azure
---

# Some Azure Notes

Module name for powershell commandlets `install-module Az`. TIL Powershell on Mac `brew install --cask powershell-preview` and then use `pwsh` shell

https://github.com/Azure/azure-functions-core-tools

disabling functions in a functionApp
```Powershell
$ResourceGroup = 'Resource-Group-Name'
$env = 'env-name'

#FunctionApps in a resource group
$names = Get-AzFunctionApp -ResourceGroupName $resourceGroup | Where {$_.Name.EndsWith("-$env-func")} | selec-object -expandProperty Name

#Functions within a FunctionApp
$functions = $names | foreach-object { Get-AzResource -ResourceGroupName $resourceGroup -ResourceType 'Microsoft.Web/sites/functions' -ResourceName $_ -ApiVersion '2021-01-15' }

#disable all functions, could also filter this list to specific functions
$disableFunc = $functions | % { ConvertFrom-StringData -StringData $_.Name -Delimiter '/' }
# Pipe the objects array to Update-AzFunctionAppSetting
$disableFunc | %{ Update-AzFunctionAppSetting -Name $_.Name -ResourceGroupName $ResourceGroup -AppSetting @{ "AzureWebJobs.$($_.Value).Disabled" = "true" } }

#or, in code, use [Disable("some-variable-name")] and then use Update-AzFunctionAppSetting to set 'some-variable-name'
# setting a variable in app settings
$disableFunc | %{ Update-AzFunctionAppSetting -Name $_.Name -ResourceGroupName $ResourceGroup -AppSetting @{ "some-variable-name" = "true" } }

```



## Some azure docker bits and pieces
```
az login --use-device-code
az acr login --name myregistry
```

Use this az-cli command to set container settings for azure functionapp deployed via docker container `az functionapp config container set ...`


## something to watch for Azure functions as at 18 JUL 2022
https://www.c-sharpcorner.com/article/do-you-know-azure-function-have-function-filters/

Function filters, `IFunctionInvocationFilter` and `IFunctionExceptionFilter`, are available but in preview.


## app insights
### query json with a record, use dot notation eg
```
exceptions | where customDimensions.OriginalFormat contains "some text"
```


Managed Identity stuff
https://learn.microsoft.com/en-us/azure/azure-functions/functions-reference?tabs=blob#local-development-with-identity-based-connections