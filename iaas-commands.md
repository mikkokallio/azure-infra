# VM in availability set

1. First, launch Azure Cloud Shell, choosing Powershell.

2. Create a new rg as `$rg`.

`PS> $location = "North Europe"
`PS> $rg = New-AzResourceGroup -Name exercise1-rg -Location $location`

3. Create a new availability set as `$set`.
```
$set = New-AzAvailabilitySet `
   -Location $location `
   -Name "availabilitySet1" `
   -ResourceGroupName $rg.ResourceGroupName `
   -Sku aligned `
   -PlatformFaultDomainCount 2 `
   -PlatformUpdateDomainCount 2
```

4. Create a configurable virtual machine object.

$vm = New-AzVMConfig `
>> -VMName "Server" `
>> -VMSize "Standard_B1s" `
>> -AvailabilitySetId $set.id
>> 

5. Create new VM from the VM object.
$

6. View the newly created VM.

`PS> Get-AzVM`

Finally, remove the rg and all resources within.

`PS> Remove-AzResourceGroup -Name "exercise1-rg"`

Check that it no longer exists.

`PS> Get-AzResourceGroup`
