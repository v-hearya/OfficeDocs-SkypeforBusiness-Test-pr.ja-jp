﻿---
title: 'Lync Server 2013: XMPP パートナー構成の作成または編集'
TOCTitle: XMPP パートナー構成の作成または編集
ms:assetid: 362dbe5e-8ee9-4aba-8c26-5907312b4a60
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ552447(v=OCS.15)
ms:contentKeyID: 49115211
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 での XMPP パートナー構成の作成または編集

 

_**トピックの最終更新日:** 2016-12-08_

Microsoft Lync Server 2013 は エッジ サーバーで Extensible Messaging and Presence Protocol (XMPP) プロキシ、フロント エンド サーバーまたは フロント エンド プールで XMPP ゲートウェイを統合します。その他の XMPP 展開から接続を可能にするには、Lync Server コントロール パネルで XMPP を構成する必要があります。XMPP ドメインベースで設定を構成します。新しいパートナー関連付けを作成するには、以下の操作を実行します。

## 新しいフェデレーション パートナーを作成、または既存の構成を編集するには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**フェデレーションと外部アクセス**\] をクリックし、\[**XMPP フェデレーション パートナー**\] をクリックします。

4.  新しい較正を作成するには、\[**新規作成**\] をクリックします。

5.  既存の構成を編集するには、構成を選択して \[**編集**\] をクリックします。

6.  \[**XMPP フェデレーション パートナー**\] の構成を作成、または編集するには、以下の設定を定義します。

7.  \[**プライマリ ドメイン**\] (必須)。プライマリ ドメインは、XMPP パートナーの基本ドメインです。たとえば、XMPP パートナーのドメイン名として **fabrikam.com** と入力します。この項目は必須です。

8.  \[**説明**\]。説明は、この特定の構成を識別するメモやその他の情報です。この項目は省略可能です。

9.  \[**追加のドメイン**\]。追加のドメインは XMPP パートナーのドメインの一部で、許可された XMPP 通信の一部として含める必要があります。たとえば、プライマリ ドメインが **fabrikam.com** の場合、XMPP を使用して通信する fabrikam.com の下のその他すべてのドメインを示します。たとえば、fabrikam.com のメイン XMPP ドメインの下に、企業 XMPP ドメイン用に **corp.fabrikam.com**、情報テクノロジ XMPP ドメイン用に **it.fabrikam.com** と入力します。

10. \[**パートナーの種類**\]。**パートナーの種類**は必須の設定で、ドロップダウン メニューで 3 つの選択肢から選択できます。以下のいずれかを選択して、どの連絡先を追加できるかを説明して適用する必要があります。選択肢は以下のとおりです。
    
      - \[**フェデレーション**\]。**フェデレーション**というパートナーの種類は、Lync Server または Office Communications Server 2007 R2 パートナー展開間の信頼できる接続です。
    
      - \[**公開確認済み**\]。**公開確認済み**というパートナーは、ユーザーの連絡先のリストに、プロバイダーによって確認された展開の一部である連絡先が追加される場合です。招待は Lync ユーザーから送信できます。また、Lync ユーザーは、パートナー連絡先からの招待を承諾できます。
    
      - \[**公開未確認**\]。**公開未確認**という関係は、2 つの展開の間に、確立された、確認可能な状態がないことを意味します。Lync ユーザーは、Lync ユーザーを連絡先に追加できるように、その連絡先について、未確認の連絡先を招待する必要があります。たとえば、Google トークは、Lync Server に関して、公開の確認された XMPP サービスではありません。Lync ユーザーから明示的な招待が送信されてこない限り、Google トーク ユーザーは、連絡先として Lync ユーザーを追加できません。

11. ストリーム ネゴシエーションとセキュリティ方式についてのメモ - トランスポート層セキュリティ (TLS) と簡易認証およびセキュリティ層 (SASL):
    
    **XMPP Standards Foundation** (XSF) と **インターネット技術標準化委員会** (IETF) は、TLS クライアント証明書、TLS サーバー証明書、および SASL メカニズムの使用と管理についての一連の規則と標準規格を定義しています。TLS と SASL の使用は、XMPP ストリームをセキュリティ保護するうえで必要な過程です。XMPP 標準規格ドキュメント **XEP-0178** では、以下のように記されています。「特に XMPP サービスが TLS でネゴシエーションが必須であると示されているとき、PKIX 証明書と SASL 外部メカニズムの使用での推奨プロトコル フローを指定します。」この XSF ドキュメントでの PKIX とは、公開キー基盤 (PKI) のことです。
    
    XMPP 要件についての詳細は、XSF ドキュメント XEP-0178 を参照してください。詳細は、「XEP-0178: Best Practices for Use of SASL EXTERNAL with Certificates」を参照してください。<http://xmpp.org/extensions/xep-0178.html>
    
    IETF ドキュメント「Extensible Messaging and Presence Protocol (XMPP): Core」の Section 5.0、STARTTLS Negotiation を参照してください。<http://tools.ietf.org/html/rfc6120>
    
      - \[**TLS ネゴシエーション**\]。TLS ネゴシエーション ルールを定義します。XMPP サービスでは、TLS を必須にするか、TLS を任意にするか、または TLS をサポートしないと定義できます。\[任意\] を選択すると、ネゴシエーションを必須とする決定についての要件は XMPP サービスに委ねられます。有効ではない構成および既知のエラーである構成を含め、SASL、TLS、およびダイヤルバックのネゴシエーションに関して選択可能なすべての設定と詳細を表示するには、「[Lync Server 2013 の XMPP フェデレーション パートナーのネゴシエーション設定](lync-server-2013-negotiation-settings-for-xmpp-federated-partners.md)」を参照してください。
        
          - \[**必須**\]。この XMPP サービスで TLS ネゴシエーションを必須にします。
        
          - \[**任意**\]。この XMPP サービスでは、TLS にはネゴシエーションが必須であることを示します。
        
          - \[**サポートなし** \]。この XMPP サービスでは TLS をサポートしません。
    
      - \[**SASL ネゴシエーション**\]。SASL ネゴシエーション ルールを定義します。XMPP サービスでは、SASL を必須にするか、SASL を任意にするか、または SASL をサポートしないと定義できます。\[任意\] を選択すると、ネゴシエーションを必須とする決定についての要件はパートナー XMPP サービスに委ねられます。
        

        > [!WARNING]
        > SASL は TLS を必要とします。SASL を使用するには、TLS を必須とするかオプションにする必要があります。SASL を必須またはオプションと定義するすべての構成は、TLS サポートを持っている必要があります。変更を保存する目的で [<STRONG>コミット</STRONG>] をクリックしたとき、TLS を必須またはオプションに設定していなかった場合は、SASL には TLS サポートが必要という警告が表示され、変更は保存されません。エラーを解決するには、TLS を [<STRONG>必須</STRONG>] または [<STRONG>オプション</STRONG>] に設定します。SASL の使用がオプションで、TLS ネゴシエーションのサポートができない場合は、SASL ネゴシエーションを [<STRONG>サポートなし</STRONG>] に設定する必要があります。サービスが中断しないように、TLS と SASL で適切なネゴシエーション ストリームがなにか、XMPP サービスに確認してください。

        
          - \[**必須**\]。この XMPP サービスで SASL ネゴシエーションを必須にします。
        
          - \[**任意**\]。この XMPP サービスでは、SASL にはネゴシエーションが必須であることを示します。
        
          - \[**サポートなし**\]。この XMPP サービスでは SASL をサポートしません。
    
      - \[**ダイヤルバック ネゴシエーション**\]。ダイヤルバック ネゴシエーションは、XSF によって、ドキュメント「**XEP-220: Server Dialback** (<http://xmpp.org/extensions/xep-0220.html>)」で定義されています。サーバー ダイヤルバック過程は、ドメイン ネーム システム (DNS) と権限のあるサーバーを使用して、要求が有効な XMPP パートナーから来たことを確認します。これを行う目的で、発信元サーバーは、生成されたダイヤルバック キーを持つ特定の種類のメッセージを作成し、DNS で受信先サーバーを参照します。発信元サーバーは、キーを、XML ストリームで DNS ルックアップの結果、つまり、受信先サーバーに送信します。受信先サーバーは、XML ストリームでキーを受信したとき、発信元サーバーには応答せず、既知の権限のあるサーバーにキーを送信します。権限のあるサーバーは、キーが有効か無効かを確認します。無効の場合、受信先サーバーは発信元サーバーに応答しません。キーが有効の場合、受信先サーバーは、発信元サーバーに、ID とキーが有効であることと、会話を開始できることを知らせます。
        
        **ダイヤルバック ネゴシエーション**には 2 つの有効な状態があります。
        
          - \[**True**\]。要求が発信元サーバーから受信されたとき、XMPP サーバーはダイヤルバック ネゴシエーションを使用するように構成されます。
        
          - \[**False**\]。要求が発信元サーバーから受信された場合、XMPP サーバーはダイヤルバック ネゴシエーションを使用するように構成されず、要求は無視されます。
