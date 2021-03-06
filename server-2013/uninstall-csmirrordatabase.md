﻿---
title: Uninstall-CsMirrorDatabase
TOCTitle: Uninstall-CsMirrorDatabase
ms:assetid: a5b14259-6cf6-46b5-ae8d-3b5e4428dfaf
ms:mtpsurl: https://technet.microsoft.com/es-es/library/JJ205159(v=OCS.15)
ms:contentKeyID: 48276269
ms.date: 01/07/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Uninstall-CsMirrorDatabase

 

_**Última modificación del tema:** 2015-03-09_

Uninstalls a Shell de administración de Lync Server 2013 mirror database. A database mirror enables you to simultaneously maintain two copies of a database, each copy residing on a different server. Este cmdlet se presentó en Lync Server 2013.

## Sintaxis

    Uninstall-CsMirrorDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] [-Confirm [<SwitchParameter>]] [-DropExistingDatabasesOnMirror <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## Examples

## Example 1

The command shown in Example 1 uninstalls the user database from the SQL Server instance RTC on the computer atl-mirror-001.litwareinc.com. Because the DropExistingDatabaseOnMirror parameter was included, the command will also delete the actual User database mirror.

    Uninstall-CsMirrorDatabase -SqlServerFqdn "atl-mirror-001.litwareinc.com" -SqlInstanceName "RTC" -DatabaseType "User" -DropExistingDatabasesOnMirror

## Detailed Description

Mirror databases enable you to simultaneously maintain two copies of a database: when data is written to Database A, a copy of that data is also written to its mirror database. This provides the ability to instantly replace Database A should that database become unavailable: you can “failover” to the mirror database with minimal disruption to your users and with minimal data loss.

Mirror databases can be installed and configured by using the [Install-CsMirrorDatabase](install-csmirrordatabase.md) cmdlet. If you ever need to remove a mirror database, you can do so by using the **Uninstall-CsMirrorDatabase** cmdlet.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Interfaz de la línea de comandos Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Uninstall-CsMirrorDatabase"}

Panel de control de Lync Server: The functions carried out by the **Uninstall-CsMirrorDatabase** cmdlet are not available in the Panel de control de Lync Server.

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
<td><p><em>DatabaseType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>Type of mirror database to be installed. Allowed values are:</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Edge</p>
<p>Lyss</p>
<p>Monitoring</p>
<p>PersistentChat</p>
<p>PersistentChatCompliance</p>
<p>Provision</p>
<p>Registrar</p>
<p>User</p></td>
</tr>
<tr class="even">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of the computer containing the database is to be uninstalled. For example:</p>
<p>-SqlServerFqdn atl-sql-001.litwareinc.com</p>
<p>This should be the FQDN of the primary SQL Server computer.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DropExistingDatabasesOnMirror</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, deletes any existing copies of the mirrored databases from the mirror server.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -</p>
<p>Report &quot;C:\Logs\UnInstallDatabaseMirror.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the database instance where the database is to be installed. A database instance is simply a set of running processes that provides access to database files. If this parameter is omitted, the <strong>Uninstall-CsMirrorDatabase</strong> cmdlet will use the default SQL Server instance.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


## Input Types

None. The **Uninstall-CsMirrorDatabase** cmdlet does not accept pipelined input.

## Return Types

None.

## Vea también

#### Otros recursos

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)

