﻿---
title: アーカイブ サーバーと監視サーバーの移行
TOCTitle: アーカイブ サーバーと監視サーバーの移行
ms:assetid: 77831579-df45-4697-b8c5-207b74a07a40
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ205015(v=OCS.15)
ms:contentKeyID: 48272569
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# アーカイブ サーバーと監視サーバーの移行

 

_**トピックの最終更新日:** 2012-10-02_

アーカイブ サーバーと監視サーバーを Lync Server 2010 環境に展開している場合、これらのサーバーは、フロントエンド プールを移行してからでないと Lync Server 2013 環境に展開できません。ただし、組織にアーカイブ機能と監視機能が欠かせない場合は、移行前にアーカイブと監視を Lync Server 2013 パイロット プールに追加して、移行プロセス中もアーカイブ機能と監視機能を使用できるように対処する必要があります。

移行プロセスで、アーカイブ機能と監視機能が必要な場合は、以下の点を考慮してください。

  - アーカイブ データと監視データは、Lync Server 2013 の展開に移動されません。レガシ環境を使用停止にする前にバックアップしたデータは、Lync Server 2010 環境でのアクティビティの履歴になります。

  - Lync Server 2010 バージョンのアーカイブ サーバーと監視サーバーは、Lync Server 2010 フロントエンド プールにのみ関連付けることができます。Lync Server 2013 では、アーカイブと監視はサーバーの役割ではなく、Lync Server 2013 フロントエンド プールに統合されたサービスになっています。

  - レガシ展開と Lync Server 2013 の展開が共存している間は、Lync Server 2010 バージョンのアーカイブ サーバーと監視サーバーは、Lync Server 2010 プールに所属するユーザーのデータを収集します。Lync Server 2013 のアーカイブと監視は、Lync Server 2013 プールに所属するユーザーのデータを収集します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>移行フェーズの間も、レガシ エッジ サーバーと新しい Lync Server 2013 パイロット プールを使用していると、Lync Server 2010 バージョンのアーカイブ サーバーは引き続き、Lync Server 2010 プールに所属するユーザーのデータを収集し、Lync Server 2013 のアーカイブは、Lync Server 2013 プールに所属するユーザーのデータを収集します。</td>
    </tr>
    </tbody>
    </table>


  - サードパーティのアーカイブおよび監視ソリューションを Lync Server 2013 のアーカイブおよび監視で使用する場合は、そのサードパーティ ソリューションと Lync Server 2013 を統合するタイミングと統合方法についてベンダーに問い合わせてください。

