﻿---
title: 'Lync Server 2013: モビリティの技術要件'
TOCTitle: モビリティの技術要件
ms:assetid: 831be681-4de0-4e42-b04f-8879ca4dcd23
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Hh690030(v=OCS.15)
ms:contentKeyID: 48272736
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのモビリティの技術要件

 

_**トピックの最終更新日:** 2016-12-08_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

モバイル ユーザーは、特別な計画を必要とするさまざまなモバイル アプリケーション シナリオに直面します。たとえば、あるユーザーが職場から離れている間に 3G ネットワーク経由の接続によってモバイル アプリケーションの使用を開始し、職場に到着したときに社内の Wi-Fi ネットワークに切り替え、職場のビルから離れるときに再度 3G に切り替えることが考えられます。このようなネットワークの移行をサポートし、一貫したユーザー エクスペリエンスを確保するように、環境を計画する必要があります。このセクションでは、モバイル アプリケーションおよびモビリティ リソースの自動検出をサポートするために整える必要のあるインフラストラクチャ要件について説明します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>モバイル アプリケーションは、他の Lync Server 2013 サービスにも接続できますが、モバイル アプリケーションのすべての Web 要求を同じ外部 Web 完全修飾ドメイン名前 (FQDN) に送信するというこの要件は Lync Server 2013 Mobility Service にのみ適用されます。他のモビリティ サービスでは、この構成は必要ありません。</td>
</tr>
</tbody>
</table>


ハードウェア ロード バランサーでの Cookie アフィニティの必要性は大きく低下しており、Lync Server 2013 で提供される Lync Mobile を使用している場合は伝送制御プロトコル (TCP) アフィニティを代わりに使用します。Cookie アフィニティは引き続き使用できますが、Web サービスでは必要なくなりました。


> [!IMPORTANT]
> Mobility Service のすべてのトラフィックは、送信元が内部または外部のどちらであっても、リバース プロキシを通過します。単一のリバース プロキシ、またはリバース プロキシのファームの場合、あるいはリバース プロキシ機能を提供するデバイスの場合、内部トラフィックがインターフェイスを出てすぐに同じインターフェイスに入ろうとすると問題が発生する可能性があります。これは、しばしば、TCP パケット スプーフィング、または単にスプーフィングとも呼ばれる、セキュリティ ルール違反を引き起こします。<EM>ヘアピン</EM> (単一パケットまたは一連のパケットが出てすぐに戻ること) は、Mobility が機能するためには許容する必要があります。この問題に対する 1 つの解決策は、ファイアウォールから切り離されたリバース プロキシを使用することです (セキュリティ上、スプーフィング防止ルールは、ファイアウォールに常に適用される必要があります)。ヘアピンは、ファイアウォール外部インターフェイスではなくリバース プロキシの外部インターフェイスで発生する可能性があります。ファイアウォールでスプーフィングを検出して、リバース プロキシでのルールを緩めることで、モビリティが必要とするヘアピンを結果的に可能にできます。<BR>可能な限り、(ファイアウォールではなく) ドメイン ネーム システム (DNS) ホストまたは CNAME レコードを使用してヘアピン動作に対するリバース プロキシを定義します。



Lync Server 2013 は、Lync 2010 Mobile および Lync 2013 モバイル クライアントのモビリティ サービスをサポートします。両方のクライアントともモビリティ エントリ ポイントを探す目的で Lync Server 2013 自動検出サービスを使用しますが、どのモビリティ サービスを使用するかという点で異なります。Lync 2010 Mobile は、Lync Server 2010 の累積した更新プログラム (2011 年 11 月) で導入された、*Mcx* と呼ばれる Mobility Service を使用します。Lync 2013 モバイル クライアントは、モビリティ サービス プロバイダーとして、統合コミュニケーション Web API (*UCWA*) を使用します。

## 内部および外部の DNS 構成

Mcx (Lync Server 2010 の累積した更新プログラム (2011 年 11 月) で導入) と UCWA (Lync Server 2013 の累積した更新プログラム (2013 年 2 月) で導入) の両方のモビリティ サービスとも、同じ方法で DNS を使用します。

自動検出を使用する場合、モバイル デバイスは、DNS を使用してリソースを見つけます。DNS の参照時に、内部 DNS レコード (lyncdiscoverinternal.*\<internal domain name\>*) に関連付けられた FQDN への接続が最初に試みられます。内部 DNS レコードを使用して接続できない場合は、外部 DNS レコード (lyncdiscover.*\<sipdomain\>*) を使用して接続が試みられます。ネットワークの内部にあるモバイル デバイスは自動検出サービスの内部 URL に接続し、ネットワークの外部にあるモバイル デバイスは自動検出サービスの外部 URL に接続します。外部自動検出要求はリバース プロキシを経由します。Lync Server 2013 自動検出サービスは、Mobility Service (Mcx と UCWA) の URL を含め、ユーザーのホーム プール用のすべての Web サービス URL を返します。ただし、Mobility Service の内部 URL と Mobility Service の外部 URL は共に Web サービスの外部 FQDN に関連付けられます。したがって、モバイル デバイスがネットワークの内部または外部のどちらにあるかどうかに関係なく、デバイスは、常に、リバース プロキシ経由で Lync Server 2013 Mobility Service に外部から接続します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>展開が内部および外部で使用するための複数の異なる名前空間で構成されている可能性があることを理解することが重要です。SIP ドメイン名が、内部展開のドメイン名と異なる場合があります。たとえば、SIP ドメイン名が <strong>contoso.com</strong> で、内部展開が <strong>contoso.net</strong> であるような場合です。Lync Server にログインするユーザーは、<strong>john@contoso.com</strong> のような SIP ドメイン名を使用します。外部 Web サービス (トポロジ ビルダーで [<strong>外部 Web サービス</strong>] と定義されているもの) に対応するときは、ドメイン名と SIP ドメイン名は DNS で定義されているものと一致します。内部 Web サービス (トポロジ ビルダーで [<strong>内部 Web サービス</strong>] と定義されているもの) に対応するときは、内部 Web サービスの既定の名前はフロント エンド サーバー、フロント エンド プール、ディレクター、またはディレクター プールの FQDN です。内部 Web サービス名は上書きできます。内部 Web サービスには (SIP ドメイン名ではなく) 内部ドメイン名を使用し、DNS ホスト A (または、IPv6 の場合は AAAA) レコードを定義して上書きされる名前を反映する必要があります。たとえば、既定の内部 Web サービスの FQDN が <strong>pool01.contoso.net</strong> であるものとします。上書きされる内部 Web サービスの FQDN は <strong>webpool.contoso.net</strong> です。このように Web サービスを定義すると、(サービスを使用するユーザーのローカル性ではなく) サービスの内部および外部のローカル性が守られます。<br />
ただし、Web サービスはトポロジ ビルダーで定義され、内部 Web サービス名は上書きできるので、結果の Web サービス名、それを検証する証明書、そしてそれを定義する DNS レコードが整合している場合は送信される必要があります、SIP ドメイン名も含めて、任意のドメイン名で内部 Web サービスを定義できます。最終的に、名前の IP アドレスへの解決は、DNS ホスト レコードと一貫した名前空間によって決まります。<br />
このトピックと例では、内部ドメイン名を使用してトポロジと DNS 定義を示します。</td>
</tr>
</tbody>
</table>


次の図に、内部および外部 DNS 構成を使用したときに、Mobility Service および自動検出サービスのモバイル アプリケーション Web 要求のフローを示します。

**AutoDiscover を使用するモビリティ サービス フロー**

![モビリティ要求のフロー](images/Hh690030.cdb96424-96f2-4abf-88d7-1d32d1010ffd(OCS.15).jpg "モビリティ要求のフロー")

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>この図は、一般的な Web サービスを示します。Mobility という名前を付けられた仮想ディレクトリが、Mcx か UCWA、またはその両方のモビリティ サービスを示します。Lync Server 2013 の累積した更新プログラム (2013 年 2 月) を適用していないときには、内部および外部 Web サービスで、仮想ディレクトリ Ucwa が定義されている場合と定義されていない場合がありえます。仮想ディレクトリ Autodiscover があり、また仮想ディレクトリ Mcx がある場合があります。<br />
展開したモビリティ サービス テクノロジにかかわらず、Autodiscover とサービスの検出は、同じ方法で機能します。</td>
</tr>
</tbody>
</table>


社内ネットワークの内側と外側からのモバイル ユーザーをサポートするには、内部と外部の Web FQDN について、いくつかの前提条件が満たされる必要があります。また、実装するように選択した機能に応じて、他の要件を満たすことが必要になる場合もあります。

  - 新しい DNS、CNAME、または A (ホスト、IPv6 の場合は AAAA) レコード - 自動検出用。

  - 新しいファイアウォール ルール - Wi-Fi ネットワーク経由でプッシュ通知をサポートする場合。

  - 内部サーバー証明書およびリバース プロキシ証明書のサブジェクトの別名 - 自動検出用。

  - フロント エンド サーバーのハードウェア ロード バランサー構成の変更 - ソース アフィニティのため。

Mobility Service と自動検出サービスをサポートするには、トポロジで以下の要件を満たす必要があります。

  - フロント エンド プールの内部 Web FQDN は、フロント エンド プールの外部 Web FQDN と区別する必要があります。

  - 内部 Web FQDN は、社内ネットワークにのみ解決し、社内ネットワークの内側からのみアクセスできる必要があります。

  - 外部 Web FQDN は、インターネットにのみ解決し、インターネットからのみアクセスできる必要があります。

  - 社内ネットワークの内側にいるユーザーの場合、Mobility Service の URL は、外部 Web FQDN にアドレス指定される必要があります。この要件は Mobility Service 向けであり、この URL にのみ適用されます。

  - 社内ネットワークの外側にいるユーザーの場合、要求は、フロント エンド プールまたは ディレクターの外部 Web FQDN に送信される必要があります。

自動検出をサポートする場合、SIP ドメインごとに以下の DNS レコードを作成する必要があります。

  - 組織のネットワーク内から接続するモバイル ユーザーをサポートするための内部 DNS レコード。

  - インターネットから接続するモバイル ユーザーをサポートするための外部 (パブリック) DNS レコード。

内部の自動検出 URL にネットワークの外側からアドレス指定できないようにする必要があります。外部の自動検出 URL にネットワーク内からアドレス指定できないようにする必要があります。ただし、外部 URL に対するこの要件を満たすことができなくても、モバイル クライアントはおそらく機能的に影響を受けません。内部 URL が常に最初に試みられるためです。

DNS レコードは、CNAME レコードまたは A (ホスト、IPv6 の場合 AAAA) レコードとすることができます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>モバイル デバイスのクライアントでは、異なるドメインからの複数の SSL (Secure Sockets Layer) 証明書がサポートされません。つまり、HTTPS では、異なるドメインへの CNAME のリダイレクトがサポートされません。たとえば、director.contoso.net のアドレスにリダイレクトされる lyncdiscover.contoso.com の DNS CNAME レコードは、HTTPS ではサポートされません。このようなトポロジでは、CNAME のリダイレクトが HTTP で解決されるように、モバイル デバイスのクライアントは、最初の要求に対して HTTP を使用する必要があります。その後、以降の要求については HTTPS を使用します。このシナリオをサポートするには、ポート 80 (HTTP) の Web 公開ルールを使用して、リバース プロキシを構成する必要があります。詳細については、「<a href="lync-server-2013-configuring-the-reverse-proxy-for-mobility.md">Lync Server 2013 での、モビリティに合わせたリバース プロキシの構成</a>」の「ポート 80 の Web 公開ルールを作成するには」を参照してください。<br />
HTTPS では、同じドメインへの CNAME のリダイレクトはサポートされます。この場合、リダイレクト先のドメインの証明書で元のドメインがカバーされます。</td>
</tr>
</tbody>
</table>


シナリオで必要な DNS レコードの詳細については、「[Lync Server 2013 での DNS 概要 - 自動検出](lync-server-2013-dns-summary-autodiscover.md)」を参照してください。

## ポートとファイアウォールの要件

また、プッシュ通知をサポートし、Apple モバイル デバイスで Wi-Fi ネットワーク経由のプッシュ通知を受信する場合、社内の Wi-Fi ネットワークのポート 5223 も開く必要があります。ポート 5223 は、送信 TCP ポートであり、Apple Push Notification Service (APNS) で使用されます。モバイル デバイスが接続を開始します。詳細については、[http://support.apple.com/kb/TS1629](http://support.apple.com/kb/ts1629?viewlocale=ja_jp)」を参照してください。


> [!WARNING]
> Lync 2013 モバイル クライアントを使用している Apple デバイスではプッシュ通知は不要です。



ユーザーが存続可能ブランチ アプライアンス (SBA) に所属している場合、次のポートが必要です。

  - UcwaSipExternalListeningPort: ポート 5088 が必要です。

  - UcwaSipPrimaryListeningPort: ポート 5089 が必要です。

Autodiscover のポートについてのその他の詳細とガイダンス、およびプロトコルの要件については、「[Lync Server 2013 でのポートの概要 - 自動検出](lync-server-2013-port-summary-autodiscover.md)」を参照してください。

## 証明書の要件

Lync モバイル クライアントに対して自動検出をサポートする場合、証明書のサブジェクトの別名リストを変更し、モバイル クライアントからのセキュリティで保護された接続をサポートする必要があります。新しい証明書の要求と割り当てを行って、自動検出サービスを実行する フロント エンド サーバーおよび ディレクターごとに、このセクションで説明されているサブジェクトの別名エントリを追加する必要があります。この方法として、リバース プロキシ用の証明書のサブジェクトの別名リストも変更することをお勧めします。組織内のすべての SIP ドメインに対してサブジェクトの別名エントリを追加する必要があります。

通常、内部の証明機関を使用した証明書の再発行は簡単なプロセスですが、サブジェクトの複数の別名エントリを、リバース プロキシで使用されるパブリック証明書に追加するには、高い費用がかかる可能性があります。多くの SIP ドメインがある場合 (サブジェクトの別名を追加する処理が非常に高価になります)、初期の自動検出サービス要求を、HTTPS を使用してポート 443 (既定の構成) で送信する代わりに、HTTP を使用してポート 80 で送信するようにリバース プロキシを構成できます。その後、要求は、ディレクターまたは フロント エンド プールのポート 8080 にリダイレクトされます。初期の自動検出サービス要求をポート 80 で発行すると、要求で HTTPS ではなく HTTP が使用されるため、リバース プロキシの証明書を変更する必要はありません。ただし、この方法はサポートされますが、お勧めできません。

## インターネット インフォメーション サービス (IIS) の要件

モビリティでは IIS 7.5、IIS 8.0、または IIS 8.5 の使用をお勧めします。Mobility Service インストーラーは、パフォーマンスを向上するようにいくつかのフラグを ASP.NET に設定します。既定では、IIS 7.5 は Windows Server 2008 R2 にインストールされ、IIS 8.0 は Windows Server 2012 に、IIS 8.5 は Windows Server 2012 R2 にインストールされます。Mobility Service インストーラーによって ASP.NET 設定が自動的に変更されます。

## ハードウェア ロード バランサーの要件

フロント エンド プールをサポートするハードウェア ロード バランサーで、Web サービスのトラフィックに対して使用される外部 Web サービス仮想 IP (VIP) を、ソース用に構成する必要があります。ソース アフィニティによって、1 つのクライアントから複数の接続があっても、接続は 1 つのサーバーに送信されてセッション状態が維持されます。アフィニティの要件の詳細については、「[Lync Server 2013 での負荷分散の要件](lync-server-2013-load-balancing-requirements.md)」を参照してください。

Lync モバイル クライアントを内部の Wi-Fi ネットワークのみでサポートすることを計画している場合、外部 Web サービスの VIP に関する説明のとおりに、ソース アフィニティ用に内部 Web サービスの VIP を構成する必要があります。この場合、ハードウェア ロード バランサーで内部 Web サービスの VIP に対する source\_addr (または TCP) アフィニティを使用する必要があります。詳細については、「[Lync Server 2013 での負荷分散の要件](lync-server-2013-load-balancing-requirements.md)」を参照してください。

## リバース プロキシの要件

Lync モバイル クライアントに対して自動検出をサポートする場合、以下のように現在の公開ルールを更新する必要があります。

  - リバース プロキシ証明書のサブジェクトの別名リストを更新し、初期の自動検出サービス要求に対して HTTPS を使用するように決定した場合、lyncdiscover.*\<sipdomain\>* 用の Web 公開ルールを更新する必要があります。通常、これは フロント エンド プールでの外部 Web サービス URL に対する公開ルールと組み合わされます。

  - リバース プロキシ証明書のサブジェクトの別名リストを更新しなくてもよいように初期の自動検出サービス要求に対して HTTP を使用するように決定した場合、まだ存在していないときにはポート HTTP/TCP 80 用の新しい Web 公開ルールを作成する必要があります。HTTP/TCP 80 用のルールが存在する場合は、lyncdiscover.*\<sipdomain\>* エントリを含むようにそのルールを更新できます。
