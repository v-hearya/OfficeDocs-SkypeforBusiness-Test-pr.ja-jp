﻿---
title: 'Lync Server 2013: ディレクターに必要なコンポーネント'
TOCTitle: ディレクターに必要なコンポーネント
ms:assetid: 15c7c8d4-b93f-4386-b2d1-d76dab8f801e
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398228(v=OCS.15)
ms:contentKeyID: 48271371
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のディレクターに必要なコンポーネント

 

_**トピックの最終更新日:** 2012-09-08_

ディレクターの作成と構成に必要な唯一のコンポーネントは、ディレクター サーバーの役割を展開することです。これは トポロジ ビルダーを使用して行い、ディレクター プール ノードで単一コンピューターのプールまたは複数コンピューターのプールを定義します。ディレクターまたは ディレクター プールを定義した後は、ディレクターになるコンピューターで Lync Server 展開ウィザードを実行します。ディレクター プールの場合は、プールのメンバーになるコンピューターで Lync Server 展開ウィザードを実行します。

## トポロジ

単一の ディレクター サーバーまたは ディレクター プールを実装できます。ディレクターは、常に独立したサーバーまたはプールであり、Lync Server 2013 内の別のサーバーの役割と併置することはありません。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ディレクターを展開しない場合は、フロント エンド サーバーまたは フロント エンド プールが ディレクターの役割を担います。</td>
</tr>
</tbody>
</table>


ディレクター プールでは負荷分散を行う必要があります。これには次のどちらかの方法を使用します。

  - Web サービスおよびドメイン ネーム システム (DNS) の負荷分散用のロード バランサー機器を他の種類のトラフィックに使用するトポロジを作成する。
    
    [拡張ディレクター プール - Lync Server 2013 の DNS 負荷分散とロード バランサー機器](lync-server-2013-scaled-director-pool-dns-load-balancing-and-hardware-load-balancer.md)

  - ディレクター プールに必要な負荷分散にロード バランサー機器を使用するトポロジを作成する。
    
    [拡張ディレクター プール - Lync Server 2013 のハードウェア負荷分散](lync-server-2013-scaled-director-pool-hardware-load-balancer.md)
