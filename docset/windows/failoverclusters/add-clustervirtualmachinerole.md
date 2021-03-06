---
ms.mktglfcycl: manage
ms.sitesec: library
ms.author: v-anbarr
author: andreabarr
description: Use this topic to help manage Windows and Windows Server technologies with Windows PowerShell.
external help file: Microsoft.FailoverClusters.PowerShell.dll-Help.xml
keywords: powershell, cmdlet
manager: jasgro
ms.date: 12/20/2016
ms.prod: w10
ms.technology: powershell-windows
ms.topic: reference
online version: 
schema: 2.0.0
title: Add-ClusterVirtualMachineRole
ms.reviewer:
ms.assetid: 5DDCD4DC-06F9-4340-96F4-463847BD8426
---

# Add-ClusterVirtualMachineRole

## SYNOPSIS
Creates a clustered virtual machine, that is, a virtual machine that can be failed over if necessary to a different server in the failover cluster.

## SYNTAX

```
Add-ClusterVirtualMachineRole [-Name <String>] [[-VMName] <String>] [-VirtualMachine <String>] [-VMId <Guid>]
 [-InputObject <PSObject>] [-Cluster <String>] [<CommonParameters>]
```

## DESCRIPTION
The **Add-ClusterVirtualMachineRole** cmdlet creates a clustered virtual machine, that is, a virtual machine that can be failed over if necessary to a different server in the failover cluster.

By creating clustered virtual machines, you can consolidate multiple servers on one physical server without causing that server to become a single point of failure.
Instead, if that server, or cluster node, fails or requires scheduled maintenance, then another node begins to run the virtual machines instead through a process known as failover.
The virtual hard disk (VHD) file for the clustered virtual machine must be on the clustered disk used by that virtual machine.

Note: This cmdlet cannot be run remotely without Credential Security Service Provider (CredSSP) authentication on the server computer.

## EXAMPLES

### Example 1
```
PS C:\> Add-ClusterVirtualMachineRole -VirtualMachine VM1
Name                       OwnerNode                            State 
----                       ---------                            ----- 
Virtual Machine            node1                              Offline
```

This example configures VM1 as a clustered virtual machine, and assigns a default name.

### Example 2
```
PS C:\> Add-ClusterVirtualMachineRole -VirtualMachine VM1 -Name "MainServer1"
Name                       OwnerNode                            State 
----                       ---------                            ----- 
MainServer1                 node1                              Offline
```

This example configures VM1 as a clustered virtual machine, and assigns the name MainServer1.

### Example 3
```
PS C:\> Get-VM -Name *print* | Add-ClusterVirtualMachineRole
Report file location: C:\Windows\cluster\Reports\Highly Available Virtual Machine 0ce88dce-eb6b-4c17-a512-d13bdbe5fcba on2011.11.28 At 15.37.33.mht 
 
Name                                    OwnerNode                               State 
----                                    ---------                               ----- 
print-VM1                               node1                                   Online
```

This example queries for virtual machines matching the wildcard characters *print* and configures them as clustered virtual machines.

## PARAMETERS

### -Cluster
Specifies the name of the cluster on which to run this cmdlet.
If the input for this parameter is `.` or it is omitted, then the cmdlet runs on the local cluster.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies the cluster on which to create the highly available virtual machine.

```yaml
Type: PSObject
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Specifies the name of the highly available virtual machine to create.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId
Specifies the virtual machine identifier (ID).

```yaml
Type: Guid
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName
Specifies the name of the virtual machine to make highly available.
Use either the **VirtualMachine** parameter or the **VMName** parameter to specify the name of the virtual machine.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VirtualMachine
Specifies the name of the virtual machine to make highly available.
Use either the **VirtualMachine** parameter or the **VMName** parameter to specify the name of the virtual machine.

```yaml
Type: String
Parameter Sets: (All)
Aliases: VM

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.FailoverClusters.PowerShell.Cluster

## OUTPUTS

### Microsoft.FailoverClusters.PowerShell.ClusterGroup

## NOTES

## RELATED LINKS

[Move-ClusterVirtualMachineRole](./Move-ClusterVirtualMachineRole.md)

[Update-ClusterVirtualMachineConfiguration](./Update-ClusterVirtualMachineConfiguration.md)

[Get-VM](../Hyper-V/Get-VM.md)

