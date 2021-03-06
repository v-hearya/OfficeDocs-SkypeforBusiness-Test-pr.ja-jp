﻿---
title: 場所ポリシーの削除
TOCTitle: 場所ポリシーの削除
ms:assetid: 8ca9ba10-f45f-435a-b39c-519d251e9085
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ688125(v=OCS.15)
ms:contentKeyID: 49887039
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 場所ポリシーの削除

 

_**トピックの最終更新日:** 2012-10-10_

Lync Server 2013 では、場所のポリシーを使用して、Enhanced 9-1-1 (E9-1-1) 機能とユーザーまたは連絡先の場所の設定に関連する設定を適用します。場所のポリシーには、ユーザーを E9-1-1 に対して有効にするかどうか、および有効にする場合、緊急電話の動作を指定します。たとえば、場所のポリシーを使用して、緊急電話 (たとえば、米国の場合、911) を構成する番号、社内セキュリティに自動的に通知するかどうか、および通話をルーティングする方法を定義できます。

場所のポリシーは、Lync Server 2013 コントロール パネルの \[**ネットワーク構成**\] グループから構成できます。また、このポリシーは、Lync Server コントロール パネルで、表示、作成、変更、または削除できます。場所のポリシーを削除するには次の手順を使用します。場所のポリシーの作成または変更の詳細については、「[場所ポリシーの作成または変更](lync-server-2013-creating-or-modifying-a-location-policy.md)」を参照してください。

## 場所のポリシーを削除するには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**ネットワーク構成**\] をクリックし、\[**場所のポリシー**\] をクリックします。

4.  \[**場所のポリシー**\] ページで、削除する場所のポリシーを選択します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>1 つ以上の場所のポリシーを一度に削除できます。 これを実行するには、Ctrl キーを押しながら、複数のポリシーを選択します。 また、すべてのポリシーを選択するには、[<strong>編集</strong>] メニューの [<strong>すべて選択</strong>] をクリックします。</td>
    </tr>
    </tbody>
    </table>


5.  \[**編集**\] メニューの \[**削除**\] をクリックします。

6.  \[**OK**\] をクリックします。
    

    > [!IMPORTANT]
    > グローバルの場所のポリシーを削除することはできません。 グローバルのポリシーの削除を試みると、警告メッセージが表示され、ポリシーはそのポリシーの既定値にリセットされます。



## 関連項目

#### タスク

[場所ポリシーの作成または変更](lync-server-2013-creating-or-modifying-a-location-policy.md)  
[場所ポリシー情報の表示](lync-server-2013-viewing-location-policy-information.md)

