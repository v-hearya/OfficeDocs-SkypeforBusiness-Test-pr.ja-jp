﻿---
title: Lync Server 2013 クライアントの展開
TOCTitle: Lync Server 2013 クライアントの展開
ms:assetid: 508e5dfa-588b-4289-81ce-2043c2d79e04
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204883(v=OCS.15)
ms:contentKeyID: 48272064
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 クライアントの展開

 

_**トピックの最終更新日:** 2012-10-19_

Lync Server 2013 にユーザーを移行した後で、次の操作を行います。

1.  新しい Lync Server 2013 サーバーでクライアント バージョン フィルターを使用して、最新の更新プログラムがインストールされているクライアントだけがサインインできるようにします。

2.  必要に応じて、クライアントのブートストラップに必要なグループ ポリシー設定を構成します。詳細については、「展開」のドキュメントの「[Lync Server 2013 でのクライアント ブートストラップ ポリシーの構成](lync-server-2013-configuring-client-bootstrapping-policies.md)」を参照してください。これらの設定の構成は、既存のクライアント ブートストラップ ポリシーを変更する場合、または新しいクライアント ブートストラップ ポリシーを設定する場合にのみ必要です。クライアント ブートストラップ ポリシーを構成する予定がない場合や、従来のクライアント ブートストラップ ポリシーをそのまま有効にしておく場合は、何もする必要はありません。

3.  Lync Server 2013 コントロール パネル、Lync Server 2013 管理シェル、またはこの両方を使用して、特定のユーザーまたはユーザー グループの他のユーザー ポリシーとクライアント ポリシーを構成します。詳細については、「計画」のドキュメントの「[Lync 2013 の新しい設定と変更された設定](lync-server-2013-new-and-changed-settings-for-lync-2013.md)」を参照してください。

4.  最新バージョンの Lync Server 2013 クライアントを、最新の累積的な更新プログラムと共に展開します。詳細については、「展開」のドキュメントの「[Lync Server 2013 でのクライアントおよびデバイスの展開](lync-server-2013-deploying-clients-and-devices.md)」を参照してください。

5.  (省略可能) 組織で Lync Server 2013 の拡張プレゼンス プライバシー モードが必要な場合は、移行の完了後に、クライアント バージョン ポリシー ルールを定義して、以前のバージョンのクライアントがサインインできないようにします。その後、拡張プレゼンスのプライバシー モードを有効にします。
    

    > [!IMPORTANT]
    > Lync 2013 拡張プレゼンス プライバシー モードは、所定のサーバー プールのすべてのユーザーに最新のクライアント バージョンをインストールするまでは有効にしないでください。

