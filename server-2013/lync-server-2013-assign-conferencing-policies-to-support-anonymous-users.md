﻿---
title: 'Lync Server 2013: 匿名ユーザー サポートのための会議ポリシーの割り当て'
TOCTitle: 匿名ユーザー サポートのための会議ポリシーの割り当て
ms:assetid: 662de022-1111-40f7-bad4-f2b686f30973
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg521007(v=OCS.15)
ms:contentKeyID: 48272348
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での匿名ユーザー サポートのための会議ポリシーの割り当て

 

_**トピックの最終更新日:** 2012-10-19_

既定では、どのユーザーも匿名ユーザーを会議に招待することはできません。匿名ユーザーをサポートするよう会議ポリシーを構成し、この会議ポリシーを特定のユーザーに適用することで、匿名ユーザーを招待できるユーザーを制御します。匿名ユーザーをサポートするように会議ポリシーを構成する方法の詳細は、「[Lync Server 2013 での会議ポリシーの作成または変更](lync-server-2013-create-or-modify-a-conferencing-policy.md)」および「[Lync Server 2013 へのフェデレーションおよび外部アクセスの管理](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md)」を参照してください。

このセクションの手順を使用して、既に作成した会議ポリシーを、1 人以上のユーザーまたは 1 つ以上のユーザー グループに適用します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ユーザーが匿名ユーザーを招待できるようにするポリシーを構成して適用するほかに、組織の匿名ユーザーのサポートを有効にする必要もあります。詳細については、「<a href="lync-server-2013-configure-policies-to-control-public-user-access.md">Lync Server 2013 でのパブリック ユーザー アクセスを制御するポリシーの構成</a>」を参照してください。</td>
</tr>
</tbody>
</table>


## 会議への匿名参加に対するユーザー ポリシーを構成するには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**会議**\] をクリックし、次のどちらかの操作を行います。
    
    1.  新しいユーザー ポリシーを作成するには、\[**新規作成**\] をクリックし、\[**ユーザー ポリシー**\] をクリックします。 \[**名前**\] ボックスに、ユーザー ポリシーの範囲を示す一意の名前を作成します (匿名ユーザーとの通信を有効にするユーザー ポリシーの場合は **EnableAnonymous** など)。
    
    2.  既存のユーザー ポリシーを編集する場合は、表の一覧にある適切なポリシーをクリックして \[**編集**\] をクリックし、\[**詳細の表示**\] をクリックします。

4.  \[**会議ポリシー**\] ダイアログ ボックスの \[**参加者に匿名ユーザーの招待を許可する**\] チェック ボックスをオンにします。

5.  \[**確定**\] をクリックします。

6.  左側のナビゲーション バーで \[**ユーザー**\] をクリックし、構成するユーザー アカウントを検索します。

7.  検索結果一覧の表でユーザー アカウントをクリックし、\[**編集**\] をクリックして、\[**詳細の表示**\] をクリックします。

8.  \[**Lync Server ユーザーの編集**\] の \[**会議ポリシー**\] で、このユーザーに適用する匿名ユーザー アクセス構成を含むユーザー ポリシーを選択します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>[<strong>&lt;自動&gt;</strong>] 設定では既定のサーバー インストールの設定が適用され、サーバーにより自動的に適用されます。</td>
    </tr>
    </tbody>
    </table>


ユーザーが匿名ユーザーを会議に招待できるようにするには、組織で匿名ユーザーのサポートも有効にしておく必要があります。詳細については、「展開」または「操作」のドキュメントの「[Lync Server 2013 でのパブリック ユーザー アクセスを制御するポリシーの構成](lync-server-2013-configure-policies-to-control-public-user-access.md)」を参照してください。
