﻿---
title: Lync Server 2013 大規模会議サポート FAQ
TOCTitle: Lync Server 2013 大規模会議サポート FAQ
ms:assetid: 34b4fb6a-e35c-47e8-8ab1-f8331741fed2
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204804(v=OCS.15)
ms:contentKeyID: 48271710
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 大規模会議サポート FAQ

 

_**トピックの最終更新日:** 2012-10-22_

以下のセクションは、大規模な会議の作成と実行について、よく尋ねられる質問とその回答です。

## Q: 大規模な会議には、最大何名のユーザーが参加できますか?

Lync Server ユーザー モデルは、共有プールでは 250 ユーザー、大規模な会議専用のプールでは 1000 ユーザーの制限を指定しています。しかし、これらの数字は、当社でテストしたユーザーの数のみ、また、当社のテストで使用した特定のハードウェアを使用した場合のみを示しています。テストに基づいて、当社が推奨する最大サイズはこの制限になります。しかし、1 つまたは複数の会議ポリシーを構成することにより、ユーザーの組織で会議に参加できる参加者の実際の数を制御できます (これは、Lync Server 管理シェルの Windows PowerShell コマンドレット、または Lync Server コントロール パネルを使用して構成します)。会議ポリシーで指定できる数は、32 ビットの整数 (1 ～ 4,294,967,295 の範囲) ですが、推奨値は 2 名以上から 250 名以下の範囲です。既定値は 250 です。

## Q: 大規模な会議専用のプールで持つことができる会議またはその他のワークロードの最大数はいくつですか?

最大 1000 名の参加者がいる大規模な会議では、最良のユーザー エクスペリエンスを保証できるよう、大規模な会議専用のプールで、一度に 1 つの大規模な会議ホスティングのみを推奨します。また大規模な会議の進行中、そのプールで、その他すべてのワークロードを実行しないことを推奨します。

## Q: 大規模な会議の開催者は、その大規模な会議専用のプールに所属する必要がありますか?

いいえ。その専用プールで大規模な会議のスケジュール設定を管理する専任スタッフ以外のすべてのユーザーを所属させないことを推奨します。これにより、その他のリアルタイム通信トラフィックが、プールでホストされる大規模な会議に問題を起こすことを防げます。専用プールで大規模な会議をスケジュール設定する場合は、大規模な会議スケジュール設定スタッフのユーザー アカウントを使用する必要があります。会議の開催者 (大規模な会議を要求するユーザー) のユーザー アカウントを、大規模な会議の発表者として追加する必要があります。

## Q:大規模な会議ではどのようなメディア モダリティを使用できますか?

最大 1000 ユーザーの大規模な会議では、オーディオ、ビデオ、PowerPoint 共有、ホワイトボード、およびプレゼンス ポーリングを含めることができます。

## Q: 大規模な会議でグループインスタント メッセージング (IM) を使用できますか?

はい。しかし、多数のインスタント メッセージが (特に、多数の会議の参加者によって) 送信されたとき、IM ウィンドウですばやくテキストをスクロールする際に問題が発生し、ユーザー エクスペリエンスに悪影響を及ぼすことがあります。また、最大 1000 ユーザーが大量のインスタント メッセージを送信すると、サーバーに大きな負荷がかかり、パフォーマンスに悪影響を及ぼすことがあります。通常、IM は質疑応答 (Q および A) でのみ必要になります。

## ユーザーは、電話からダイヤルインすることにより、大規模な会議に参加できますか?

はい。Lync Server 2013 プールが適切に展開され、ダイヤルイン会議が有効にされている場合は、ユーザーはダイヤルインによって大規模な会議に参加できます。当社のテストでは、1000 ユーザーのうち 15% が 10 分間にわたって大規模な会議に参加できることが示されています。

## Q: 仮想トポロジで大規模な会議をホストできますか?

当社は、仮想トポロジでの大規模な会議はテストしていません。このことから、当社は大規模な会議の専用プールをホストする目的で仮想マシンを使用することはサポートしません。
