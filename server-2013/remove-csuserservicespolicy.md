﻿---
title: Remove-CsUserServicesPolicy
TOCTitle: Remove-CsUserServicesPolicy
ms:assetid: 025f9a94-ff44-4e06-8b14-721f8fd9924f
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204629(v=OCS.15)
ms:contentKeyID: 48271075
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsUserServicesPolicy

 

_**トピックの最終更新日:** 2015-03-09_

Deletes an existing User Services policy. User Services policies determine whether or not a user's contacts are stored in Lync Server 2013 or in the Unified Contact Store. The Unified Contact Store provides a way for users to maintain a single set of contacts that can be accessed using Lync 2013, Microsoft Outlook, and/or Microsoft Outlook Web Access. このコマンドレットは Lync Server 2013 で導入されました。

## 構文

    Remove-CsUserServicesPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## Examples

## Example 1

The command shown in Example 1 deletes the per-user User Services policy RedmondUserServicesPolicy.

    Remove-CsUserServicesPolicy -Identity "RedmondUserServicesPolicy"

## Example 2

Example 2 deletes all the User Services policies configured at the site scope. To do this, the command first uses the **Get-CsUserServicesPolicy** cmdlet and the Filter value to return a collection of all the policies configured at the site scope; that's accomplished by using the filter value "site:\*". The resulting collection is then piped to the **Remove-CsUserServicesPolicy** cmdlet, which deletes each policy in the collection.

    Get-CsUserServicesPolicy -Filter "site:*" | Remove-CsUserServicesPolicy

## Example 3

In Example 3, all the User Services policies that allow the use of the Unified Contact Store are deleted. To carry out this task, the command first calls the **Get-CsUserServicesPolicy** cmdlet without any parameters in order to return a collection of all the User Services policies configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the UcsAllowed property is equal to (-eq) True ($True). Those policies are then piped to, and removed by, the **Remove-CsUserServicesPolicy** cmdlet.

    Get-CsUserServicesPolicy | Where-Object {$_.UcsAllowed -eq $True} | Remove-CsUserServicesPolicy

## Detailed Description

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Microsoft Exchange Server 2013 instead of in Lync Server; in turn that allows the user to access the same set of contacts in Outlook and Outlook Web Access as well as in Lync 2013. (Alternatively, you can continue to store contacts in Lync Server 2013. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Lync 2013.)

In order to take advantage of the unified contact store you must (among other things) assign the user a user services policy that enables the use of the unified contact store. User service policies (which can be configured at the global, site, or the per-user scope) contain only a single property: UcsAllowed. When this property is set to True then (assuming all the other prerequisites have been met) the next time a user logs on to Lync Server 2013 his or her contacts will automatically be migrated to the unified contact store.

If this property is set to False this automatic migration will not take place. However, simply setting UcsAllowed will not cause a user's contacts to be moved from the unified contact store back to Lync Server. In order to do that, you must first assign the user a user services policy that does not allow the use of the unified contact store. After that, you must then use the **Invoke-UcsRollback** cmdlet to "manually" migrate the contacts from the unified contact store back to Lync Server.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell コマンドライン インターフェイス prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserServicesPolicy"}

**Lync Server コントロール パネル:** The functions carried out by the R**emove-CsUserServicesPolicy** cmdlet are not available in the Lync Server コントロール パネル.

## パラメーター


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
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the policy to be deleted. To remove a policy configured at the site scope, use syntax similar to this:</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>To remove a policy configured at the service scope, use syntax similar to this:</p>
<p>-Identity &quot;UserServer:atl-cs-001.litwareinc.com&quot;</p>
<p>The User Server service is the only service that can host a user services policy.</p>
<p>Policies can also be removed at the per-user scope. To remove per-user policies, use syntax similar to this:</p>
<p>-Identity &quot;RedmondUserServicesPolicy&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Removes the user services policy assigned to the specified Skype for Business Online tenant. When removing a policy assigned to a tenant, you must also include the Identity parameter along with the parameter value &quot;global&quot;:</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot; –Identity &quot;global&quot;</p></td>
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

The **Remove-CsUserServicesPolicy** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.

## Return Types

None. Instead, the **Remove-CsUserServicesPolicy** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserServices.UserServicesPolicy object.

## 関連項目

#### その他のリソース

[Get-CsUserServicesPolicy](get-csuserservicespolicy.md)  
[Grant-CsUserServicesPolicy](grant-csuserservicespolicy.md)  
[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

