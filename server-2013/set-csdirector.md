﻿---
title: Set-CsDirector
TOCTitle: Set-CsDirector
ms:assetid: 74eb6f17-812f-47df-84ee-fa6e42990f2e
ms:mtpsurl: https://technet.microsoft.com/es-es/library/Gg398565(v=OCS.15)
ms:contentKeyID: 48275677
ms.date: 01/07/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDirector

 

_**Última modificación del tema:** 2015-03-09_

Modifies the properties of one or more Directors. Directors can be used to authenticate user requests, but do not host user accounts. Este cmdlet se presentó en Lync Server 2010.

## Sintaxis

    Set-CsDirector [-Identity <XdsGlobalRelativeIdentity>] [-ArchivingServer <String>] [-Confirm [<SwitchParameter>]] [-EdgeServer <String>] [-Force <SwitchParameter>] [-MirrorMonitoringDatabase <String>] [-MonitoringDatabase <String>] [-MonitoringServer <String>] [-SipHealthPort <UInt16>] [-SipPort <UInt16>] [-SipServerTcpPort <UInt16>] [-WebPort <UInt16>] [-WebServer <String>] [-WhatIf [<SwitchParameter>]]

## Examples

## EXAMPLE 1

The command shown in Example 1 changes the Servidor de archivado associated with the Director Director:atl-cs-001.litwareinc.com. In this example, the Servidor de archivado is switched to ArchivingServer:dublin-cs-001.litwareinc.com.

    Set-CsDirector -Identity "Director:atl-cs-001.litwareinc.com" -ArchivingServer "ArchivingServer:dublin-cs-001.litwareinc.com"

## EXAMPLE 2

Example 2 changes the SIP port for all the Directors currently in use in the organization. To do this, the command first uses the **Get-CsService** cmdlet and the Director parameter to return a collection of all the Directors in the organization. That collection is then piped to the **ForEach-Object**. In turn, the **ForEach-Object** cmdlet runs the **Set-CsDirector** cmdlet against each site in the collection, changing the value of the SipPort property to 5072.

    Get-CsService -Director | ForEach-Object {Set-CsDirector -Identity $_.Identity -SipPort 5072}

## Detailed Description

The Director authenticates users and responds to user requests without actually hosting user accounts. Directors are typically used for organizations that allow external access to the network through Edge Servers. In that scenario, Directors not only help alleviate the strain on Front End Servers (by handling authentication requests), but also help shield the internal network from denial-of-service attacks and other malicious traffic. Directors are also useful any time multiple Front End Servers are deployed in a central site. In that case, Directors receive all user requests and then channel those requests to the appropriate server pool. This, again, helps to ease the burden placed on the Front End Servers.

The **Set-CsDirector** cmdlet enables you to modify the property values for any of the Directors currently in use in your organization. This includes changing such things as the Servidor de archivado or Servidor perimetral associated with the Director, or changing the port used for sending and receiving SIP traffic.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsDirector** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDirector"}

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
<td><p><em>ArchivingServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Servidor de archivado to be associated with the Director. For example: -ArchivingServer &quot;ArchivingServer:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Se le pedirá confirmación antes de ejecutar el comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EdgeServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Servidor perimetral to be associated with the Director. For example: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Service location of the Director to be modified. For example: -Identity &quot;Director:atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;Director:&quot; when specifying a Director. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>MirrorMonitoringDatabase</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the mirror monitoring database to be associated with the Director.</p></td>
</tr>
<tr class="odd">
<td><p><em>MonitoringDatabase</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the monitoring database to be associated with the Director.</p></td>
</tr>
<tr class="even">
<td><p><em>MonitoringServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Servidor de supervisión to be associated with the Director. For example: -MonitoringServer &quot;MonitoringServer:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipHealthPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for monitoring server health.</p></td>
</tr>
<tr class="even">
<td><p><em>SipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for Session Initiation Protocol (SIP) traffic.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipServerTcpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP listening port. The default value is 5060.</p></td>
</tr>
<tr class="even">
<td><p><em>WebPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for communicating with Servicios web.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Servicios web location of the server to be associated with the Director. For example: -WebServer &quot;WebServer:atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describe qué sucedería si se ejecutara el comando sin ejecutarlo realmente.</p></td>
</tr>
</tbody>
</table>


## Input Types

None. The **Set-CsDirector** cmdlet does not accept pipelined input.

## Return Types

The **Set-CsDirector** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayDirector object.

## Vea también

#### Otros recursos

[Get-CsService](get-csservice.md)

