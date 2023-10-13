
from: https://discuss.hashicorp.com/t/terraform-outputs-with-count-index/32555

built in functions to help with generating output values:

one function
```
output "route53_private_prod" 
{ 
    value = one(aws_route53_zone.private[*].zone_id) 
}
```

 "\**" splat operator (I think) (https://www.terraform.io/docs/language/expressions/splat.html)

array of values into flat list. 'one' function makes sure single value and returns null otherwise


### import resources
`terraform import module.<module-name>.<resource-type>.<resource-name> <ID>`

for example: with import an apim instance

```
terraform import -var="subscription_id=<sub-id>" -var="environment=dev" -var-file="path/to/terraform.tfvars" -var-file="path/to/environment/main.tfvars" module.supplychain_apimanagement.azurerm_api_management.apim /subscriptions/<sub-id>/resourceGroups/<resource-group-name>/providers/Microsoft.ApiManagement/service/<apim-service-name> 
```

