﻿---
title: 会議の場所に基づくルーティングの要件
TOCTitle: 会議の場所に基づくルーティングの要件
ms:assetid: 766d9286-2c34-4faf-bb3e-f0ca478a70cf
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn362806(v=OCS.15)
ms:contentKeyID: 56270105
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 会議の場所に基づくルーティングの要件

 

_**トピックの最終更新日:** 2016-12-08_

Location-Based Routing Conferencing アプリケーションのインストールと構成に必要な要件は次のとおりです。

  - トポロジのすべてのサーバーとプールに Lync Server 2013 の累積的な更新プログラム 2 を展開する必要があります。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>トポロジの Lync サーバーまたはプールに Lync Server 2013 の累積的な更新プログラム 2 以降がインストールされていない場合、Lync の会議の場所に基づくルーティングの適用を保証することはできません。</td>
</tr>
</tbody>
</table>


  - Lync Server 2013 の場所に基づくルーティングは、Location-Based Routing Conferencing アプリケーションの前提条件です。Lync Server 2013 の場所に基づくルーティングについて詳しくは、「[場所に基づくルーティングの構成](lync-server-2013-configuring-location-based-routing.md)」をご覧ください。

  - Location-Based Routing Conferencing アプリケーションの要件は、Lync Server 2013 の場所に基づくルーティングの要件と同じです。詳しくは、「[場所に基づくルーティングの計画](lync-server-2013-planning-for-location-based-routing.md)」をご覧ください。

## サポートされるサーバー

Location-Based Routing Conferencing アプリケーションでは、トポロジのすべてのフロントエンド プールと Standard Edition Server に Lync Server 2013 の累積的な更新プログラム 2 が展開されている必要があります。Lync Server 2013 の累積的な更新プログラム 2 がトポロジの一部の Lync Server にインストールされていない場合、Lync の会議と取次通話転送に、場所に基づくルーティングの制限を完全に適用することはできません。

次の表は、場所に基づくルーティングをサポートするサーバーの役割とバージョンの組み合わせを示しています。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>フロントエンド プールのバージョン</p></td>
<td><p>仲介サーバーのバージョン</p></td>
<td><p>サポート対象</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 の累積的な更新プログラム 2</p></td>
<td><p>Lync Server 2013 の累積的な更新プログラム 2</p></td>
<td><p>はい</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 の累積的な更新プログラム 2</p></td>
<td><p>Lync Server 2013 の累積的な更新プログラム 1</p></td>
<td><p>いいえ</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 の累積的な更新プログラム 2</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>いいえ</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2013 の累積的な更新プログラム 2</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>いいえ</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 の累積的な更新プログラム 1</p></td>
<td><p>任意</p></td>
<td><p>いいえ</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010</p></td>
<td><p>任意</p></td>
<td><p>いいえ</p></td>
</tr>
<tr class="even">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>任意</p></td>
<td><p>いいえ</p></td>
</tr>
</tbody>
</table>


## サポートされるクライアント

Lync の会議の場所に基づくルーティングをサポートする Lync クライアントは、Lync Server 2013 の場所に基づくルーティングをサポートするクライアントと同じです。詳しくは、「[場所に基づくルーティングに対するクライアントとサーバーのサポート](lync-server-2013-client-and-server-support-for-location-based-routing.md)」をご覧ください。

## 取次通話転送に関する仲介サーバーの要件

Location-Based Routing Conferencing アプリケーションでは、取次通話転送に場所に基づくルーティングの制限を適用するために、スタンドアロンの仲介サーバーを展開することが必要です。

取次通話転送の場所に基づくルーティングを適用するには、仲介サーバーを、場所に基づくルーティングが必要であるネットワーク地域にある、唯一の仲介サーバーのピア (PBX、SIP ゲートウェイなど) に関連付ける必要があります。同じネットワーク地域に追加の仲介サーバーのピアが展開されている場合、その仲介サーバーのピアを別の仲介サーバーに関連付ける必要があります。この要件の詳細は次のようになります。

  - 複数の仲介サーバーのピアごとに 1 台の仲介サーバー 複数のピア (PBX とゲートウェイ) への複数の SIP トランクを使用して構成されている仲介サーバーを経由して、取次通話転送が仲介サーバーのピアにルーティングされるときに、取次通話転送が一部の SIP トランク経由では許可されているが、その他の SIP トランク経由では許可されない場合、取次通話転送は PSTN 料の回避を防ぐためにブロックされます。
    
    たとえば、1 台の仲介サーバーが PSTN ゲートウェイ仲介サーバーのピアと PBX 仲介サーバーのピアを担当している場合、次の動作が観察されます。
    
      - 特定のサイト (サイト 1) の Lync ユーザーが、PSTN エンドポイントを使用した通話を、別のサイト (サイト 2) の Lync ユーザーに取次転送を介して転送しようとすると、その通話は PSTN 料の回避を防ぐために許可されません。
    
      - 特定のサイト (サイト 1) の Lync ユーザーが、同じサイト (サイト 1) の PBX エンドポイントを使用した通話を、別のサイト (サイト 2) の Lync ユーザーに取次転送を介して転送しようとすると、PSTN 料の回避が発生する可能性がない場合であっても、その通話は許可されません。

  - 仲介サーバーのピアごとの個別の仲介サーバー
    
    取次転送の対象が仲介サーバーのピアである場合、その取次転送は、仲介サーバーが担当する 1 台の仲介サーバーのピアに照らし合わせて評価されます。サイトにある他のすべての仲介サーバーのピアに関係なく、PSTN 料の回避が発生する可能性に基づいて、通話は不許可または許可になります。これは、通話は個別の仲介サーバーが担当するためです。
    
    たとえば、独立した仲介サーバーが PSTN ゲートウェイ仲介サーバーのピアと PBX 仲介サーバーのピアを担当している場合、次の動作が観察されます。
    
      - 特定のサイト (サイト 1) の Lync ユーザーが、PSTN エンドポイントを使用した通話を、別のサイト (サイト 2) の Lync ユーザーに取次転送を介して転送しようとすると、その通話は PSTN 料の回避を防ぐために許可されません。
    
      - 特定のサイト (サイト 1) の Lync ユーザーが、同じサイト (サイト 1) の PBX エンドポイントを使用した通話を、別のサイト (サイト 2) の Lync ユーザーに取次転送を介して転送しようとすると、PSTN 料の回避が発生する可能性がないため、その通話は許可されます。

## Location-Based Routing Conferencing アプリケーションではサポートされない機能

次の機能は、Location-Based Routing Conferencing アプリケーションではサポートされません。

  - ダイヤルイン会議。ダイヤルイン会議に場所に基づくルーティングを適用することはできません。会議の開催者が、場所に基づくルーティングが有効である Lync ユーザーであっても、特定の会議に対するダイヤルイン要求は場所に基づくルーティングにより制限されません。

  - 場所に基づくルーティングの制限を適用する必要がある地域では、会議アクセス番号をプロビジョンニングしないことをお勧めします。
