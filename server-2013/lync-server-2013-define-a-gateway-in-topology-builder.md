﻿---
title: 'Lync Server 2013: トポロジ ビルダーを使用したゲートウェイの定義'
TOCTitle: トポロジ ビルダーを使用したゲートウェイの定義
ms:assetid: 456e5a96-d9f6-42a6-862c-a69464391628
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg425945(v=OCS.15)
ms:contentKeyID: 48271942
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での、トポロジ ビルダーを使用したゲートウェイの定義

 

_**トピックの最終更新日:** 2012-10-04_

このステップに従い、エンタープライズ VoIP が有効なユーザーに公衆交換電話網 (PSTN) への接続を提供するために、トポロジ ビルダーを使用して、仲介サーバーを関連付けることができる*ピア*を定義します。仲介サーバーへのピアには、PSTN ゲートウェイ、IP-PBX、または SIP トランクを構成することで接続するインターネット テレフォニー サービス プロバイダー (ITSP) のセッション ボーダー コントローラー (SBC) が使用できます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>このトピックでは、「展開」ドキュメントの「<a href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Lync Server 2013 でフロントエンド プールまたは Standard Edition サーバーを定義および構成する</a>」および「<a href="lync-server-2013-publish-the-topology.md">Lync Server 2013 でトポロジを公開する</a>」で説明されているように、少なくとも 1 つの中央サイトで少なくとも 1 つの内部 フロント エンド プールまたは Standard Edition サーバーを、併置またはスタンドアロンの 仲介サーバーとともにセットアップしていることを前提としています。また、インフラストラクチャが「<a href="lync-server-2013-software-prerequisites-for-enterprise-voice.md">Lync Server 2013 のエンタープライズ VoIP のソフトウェア前提条件</a>」および「<a href="lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md">Lync Server 2013 のエンタープライズ VoIP のセキュリティおよび構成の前提条件</a>」で説明されている前提条件を満たしているかどうかを確認済みであることも前提としています。</td>
</tr>
</tbody>
</table>


## 仲介サーバーのピアを定義するには

1.  トポロジ ビルダーを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server トポロジ ビルダー**\] の順にクリックします。

2.  Lync Server 2013、サイト名、共有コンポーネントで \[**PSTN ゲートウェイ**\] ノードを右クリックし、\[**新規 PSTN ゲートウェイ**\] をクリックします。
    
    ![トポロジ ビルダー (Lync Server 2013)](images/Gg425945.d898c3c1-8798-4b74-8f02-b994ef3db4c1(OCS.15).png "トポロジ ビルダー (Lync Server 2013)")

3.  \[**新規 IP/PSTN ゲートウェイの定義**\] で、ピアの完全修飾ドメイン名 (FQDN) または IP アドレスを入力して、\[**次へ**\] をクリックします。
    
    ![IP/PSTN ゲートウェイ](images/Gg425945.8017ba5e-41bc-48d4-97d9-fd306cd322b8(OCS.15).png "IP/PSTN ゲートウェイ")
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>トランスポートの種類としてトランスポート層セキュリティ (TLS) を指定する場合、仲介サーバーのピアの IP アドレスの代わりに、FQDN を指定する必要があります。</td>
    </tr>
    </tbody>
    </table>


4.  新しい PSTN ゲートウェイの IP アドレスのリッスン モード (IPv4 または IPv6) を定義し、\[**次へ**\] をクリックします。
    
    ![IP アドレス](images/Gg425945.c7fc0d12-adc8-45a7-aca1-b376e1d2fcec(OCS.15).png "IP アドレス")

5.  PSTN ゲートウェイのルート トランクを定義します。*トランク*は、仲介サーバーと、タプルによって一意に識別されるゲートウェイとの間の論理接続です。
    
    { 仲介サーバー FQDN、仲介サーバー リッスン ポート (TLS または TCP) : ゲートウェイ IP および FQDN、ゲートウェイ リッスン ポート}
    
      - トポロジ ビルダーで PSTN ゲートウェイを定義するときは、PSTN ゲートウェイがトポロジに正常に追加されるように、ルート トランクを定義する必要があります。
    
      - ルート トランクは、関連する PSTN ゲートウェイが削除されるまで削除できません。
    
    ![ゲートウェイの定義: ルート トランク](images/Gg425945.3b030757-eb35-4616-bb6b-74ee67507e3d(OCS.15).png "ゲートウェイの定義: ルート トランク")

6.  \[**IP/PSTN ゲートウェイのリッスン ポート**\] には、PSTN ゲートウェイのルート トランクに関連付けられる 仲介サーバーからの SIP メッセージ用にゲートウェイ、PBX、または SBC が使用するリッスン ポートを入力します (PSTN ゲートウェイ、PBX または SBC の場合、伝送制御プロトコル (TCP) の既定ポートは 5066、トランスポート層セキュリティ (TLS) の既定ポートは 5067 です。ブランチ サイトの 存続可能ブランチ アプライアンスの場合、TCP の既定ポートは 5081、TLS の既定ポートは 5082 です)。

7.  \[**SIP 転送プロトコル**\] でピアが使用する転送タイプをクリックし、\[**OK**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>セキュリティ上の理由により、TLS を使用可能な 仲介サーバーのピアを展開することを強くお勧めします。</td>
    </tr>
    </tbody>
    </table>


8.  \[**関連付けられた 仲介サーバー**\] で、仲介サーバー プールを選択して、このルート トランクをこの PSTN ゲートウェイと関連付けます。

9.  \[**関連付けられた 仲介サーバー ポート**\] で、ゲートウェイからの SIP メッセージ用に 仲介サーバーが使用するリッスン ポートを入力します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Lync Server 2013 で複数のトランクがサポートされている場合、複数の PSTN ゲートウェイとの通信に使用される 仲介サーバーに複数の SIP シグナリング ポートを定義できます。トランクを定義するとき、[<strong>関連付けられた 仲介サーバー ポート</strong>] は、仲介サーバーが許可する各プロトコルに応じたリッスン ポートの範囲内で指定する必要があります。このポート範囲は、Lync Server 2013 と仲介プールで定義されます。該当する 仲介サーバー プールを右クリックして、[<strong>プロパティの編集</strong>] を選択します。[<strong>リッスン ポート</strong>] フィールドでポート範囲を指定します。</td>
    </tr>
    </tbody>
    </table>


10. \[**完了**\] をクリックします。


> [!IMPORTANT]
> このステップを終了する前に、定義されたピアが実行中で、指定した FQDN または IP アドレスを使用していることを確認してください。



次に、「展開」のドキュメントの「[Lync Server 2013 でトポロジを公開する](lync-server-2013-publish-the-topology.md)」セクションにある手順に従って、ピアをトポロジに追加します。Lync Server を実行するサーバーのファイルのインストールにデータを使用できるように、トポロジ ビルダーでトポロジを作成または変更する度にトポロジを公開する必要があります。

## 関連項目

#### タスク

[Lync Server 2013 でのトポロジ ビルダーによるトランクの変更](lync-server-2013-modify-a-trunk-in-topology-builder.md)
