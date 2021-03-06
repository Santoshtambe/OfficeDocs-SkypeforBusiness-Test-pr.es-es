﻿---
title: Test-CsTopology
TOCTitle: Test-CsTopology
ms:assetid: 06ffa245-f1c7-46b7-9be6-5b291deda5c1
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Gg398127(v=OCS.15)
ms:contentKeyID: 48274325
ms.date: 01/07/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsTopology

 

_**Última modificación del tema:** 2015-03-09_

Verifies service activation and group permissions for your installation of Lync Server. Este cmdlet se presentó en Lync Server 2010.

## Sintaxis

    Test-CsTopology [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-Service <String>]

## Examples

## EXAMPLE 1

Example 1 validates the entire Lync Server topology.

    Test-CsTopology

## EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Report parameter is included to specify the location (C:\\Logs\\Topology.xml) where the output file should be written.

    Test-CsTopology -Report "C:\Logs\Topology.xml"

## EXAMPLE 3

In Example 3, the **Test-CsTopology** cmdlet is used to validate a single service: Registrar:atl-cs-001.litwareinc.com.

    Test-CsTopology -Service "Registrar:atl-cs-001.litwareinc.com"

## Detailed Description

The **Test-CsTopology** cmdlet provides a way for you to verify that Lync Server is functioning correctly at a global level. By default, the cmdlet checks your entire Lync Server infrastructure, verifying that the required services are running and that the appropriate permissions have been set for these services and for the universal security groups created when you install Lync Server.

In addition to verifying the validity of Lync Server as a whole, the **Test-CsTopology** cmdlet also lets you check the validity of a specific service. For example, this command checks the state of the A/V Conferencing Server on the pool atl-cs-001.litwareinc.com:

Test-CsTopology –Service "ConferencingServer:atl-cs-001.litwareinc.com".

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsTopology"}

## Parámetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the <strong>Test-CsTopology</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Servicios de dominio de Active Directory, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\Topology.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Service</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, the <strong>Test-CsTopology</strong> cmdlet limits its validation checks to the specified service. (Note that you can only specify one service at a time when using the Service parameter.) Services should be specified using the appropriate service ID; for example, this syntax refers to the Registrar service on the atl-cs-001.litwareinc.com pool: -Service &quot;Registrar:atl-cs-001.litwareinc.com&quot;.</p>
<p>If this parameter is not included then the entire topology will be validated.</p></td>
</tr>
</tbody>
</table>


## Input Types

None. The **Test-CsTopology** cmdlet does not accept pipelined input.

## Return Types

The **Test-CsTopology** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

## Vea también

#### Otros recursos

[Enable-CsTopology](enable-cstopology.md)  
[Get-CsTopology](get-cstopology.md)  
[Publish-CsTopology](publish-cstopology.md)

