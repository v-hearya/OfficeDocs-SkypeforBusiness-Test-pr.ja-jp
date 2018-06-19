﻿---
title: 'Lync Server 2013: コール パークで使用されるコンポーネント'
TOCTitle: コール パークで使用されるコンポーネント
ms:assetid: c7ffbee3-0ce1-48c0-bb56-af098b41d6d6
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398824(v=OCS.15)
ms:contentKeyID: 48273565
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のコール パークで使用されるコンポーネント

 

_**トピックの最終更新日:** 2012-09-13_

コール パーク アプリケーションは、エンタープライズ VoIP を展開すると自動的にインストールされます。 コール パークを有効にするには、音声ポリシーを構成します。 コール パーク アプリケーションをサポートする Lync Server 2013 コンポーネントは次のとおりです。

  - **アプリケーション サービス**    アプリケーション サービスは、 コール パーク アプリケーションなどの統合コミュニケーション アプリケーションを展開、ホスト、および管理するためのプラットフォームです。 アプリケーション サービスは、 フロント エンド プールのすべてのフロントエンド サーバー、およびすべての Standard Edition サーバーに自動的にインストールされます。

  - **コール パーク アプリケーション**    コール パーク アプリケーションは、 アプリケーション サービスがホストする統合通信アプリケーションの 1 つです。エンタープライズ VoIP を展開するときに自動的に組み込まれます。 コール パークは、通話を保留および取得し、通話保留オービットを管理します。

  - **保留音ファイル**   保留音が有効な場合には、通話の保留中に保留音ファイルが再生されます。既定の保留音ファイルは、 コール パーク アプリケーションのインストール時に組み込まれます。

  - **ファイル ストア**    コール パーク アプリケーションは、ファイル ストアを使用してカスタム オーディオ ファイルを保持します。

  - **Lync Server コントロール パネル**    Lync Server コントロール パネルを使用して、通話保留オービット テーブルを構成し、ユーザーの コール パークを有効にすることができます。

  - **Lync Server 管理シェル**   すべての コール パーク アプリケーションの構成は、 Lync Server 管理シェルのコマンドレットを使用して実行できます。
