﻿---
title: Windows 7 または Windows 8 で実行しているクライアントのサービス品質 (QoS) ポリシーの構成
TOCTitle: Windows 7 または Windows 8 で実行しているクライアントのサービス品質 (QoS) ポリシーの構成
ms:assetid: efff2b98-b3fb-4183-a4f0-329a9105ce2c
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ205371(v=OCS.15)
ms:contentKeyID: 48274066
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows 7 または Windows 8 で実行しているクライアントのサービス品質 (QoS) ポリシーの構成

 

_**トピックの最終更新日:** 2016-03-29_

Lync クライアントが使用するポート範囲の指定に加えて、クライアント コンピューターに適用される個別のサービス品質ポリシーも作成する必要があります (会議サーバー、アプリケーション サーバー、および仲介サーバー用に作成したサービス品質ポリシーは、クライアント コンピューターに適用しないでください)。この情報は、Lync 2013 クライアント、および Windows 7 と Windows 8 のいずれかを実行しているコンピューターのみに適用されます。

次の例では、このポート範囲のセットを使用して、音声ポリシーとビデオ ポリシーを作成します。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>クライアント トラフィックの種類</th>
<th>開始ポート</th>
<th>ポート範囲</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>音声</p></td>
<td><p>50020</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>ビデオ</p></td>
<td><p>58000</p></td>
<td><p>20</p></td>
</tr>
<tr class="odd">
<td><p>アプリケーション共有</p></td>
<td><p>42000</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>ファイル送信</p></td>
<td><p>42020</p></td>
<td><p>20</p></td>
</tr>
</tbody>
</table>


Windows 7 または Windows 8 のコンピューター用に品質サービスの音声ポリシーを作成するには、まずグループ ポリシー管理がインストールされているコンピューターにログオンします。グループ ポリシー管理を開き (\[**スタート**\] をクリックし、\[**管理ツール**\] をポイントし、\[**グループ ポリシーの管理**\] をクリックして、次の手順に従います。

1.  グループ ポリシーの管理で、新しいポリシーのを作成するコンテナーを見つけます。たとえば、クライアント コンピューターすべてが Clients という名前の OU にある場合、新しいポリシーは Client OU に作成します。

2.  適切なコンテナーを右クリックし、\[**このドメインに GPO を作成し、このコンテナにリンクする**\] をクリックします。

3.  \[**新しい GPO**\] ダイアログ ボックスで、新しいグループ ポリシー オブジェクトの名前を \[**名前**\] ボックスに入力し (たとえば「**Lync Audio**」)、\[**OK**\] をクリックします。

4.  新しく作成したポリシーを右クリックし、\[**編集**\] をクリックします。

5.  グループ ポリシー管理エディターで \[**コンピューターの構成**\]、\[**ポリシー**\]、\[**Windows の設定**\] の順に展開し、\[**ポリシー ベースの QoS**\] を右クリックし、\[**新規ポリシーの作成**\] をクリックします。

6.  \[**ポリシー ベースの QoS**\] ダイアログ ボックスの開始ページで、新しいポリシーの名前を \[**名前**\] ボックスに入力します (たとえば「**Lync Audio**」)。\[**DSCP 値を指定する**\] を選択し、値を「**46**」に設定します。\[**出力方向のスロットル率を指定する**\] はオフのままで、\[**次へ**\] をクリックします。

7.  次のページで、\[**すべてのアプリケーション**\] が選択されていることを確認し、\[**次へ**\] をクリックします。この設定はネットワークに対し、特定のアプリケーションが作成したパケットのみではなく、DSCP マーキングが 46 のパケットをすべて見つけるよう指示します。

8.  3 ページ目で、\[**すべての発信元 IP アドレス**\] と \[**すべての宛先 IP アドレス**\] の両方が選択されていることを確認し、\[**次へ**\] をクリックします。この 2 つの設定によって、どのコンピューター (IP アドレス) がパケットを送信したか、およびどのコンピューター (IP アドレス) がパケットを受信するかにかかわらず、パケットが管理されるようになります。

9.  4 ページ目で、\[**この QoS ポリシーを適用するプロトコルを選択してください**\] ドロップダウン リストから \[**TCP と UDP**\] を選択します。TCP (伝送制御プロトコル) と UDP (ユーザー データグラム プロトコル) の 2 つは、Lync Server とそのクライアント アプリケーションで最もよく使用されているネットワーク プロトコルです。

10. \[**発信元ポート番号を指定してください**\] という見出しの下にある \[**次の発信元ポート番号か範囲**\] を選択します。付随するテキスト ボックスに、音声送信用に予約されたポート範囲を入力します。たとえば、50020 から 50039 までのポートを音声トラフィック用に予約した場合は、「**50020:50039**」という形式でポート範囲を入力します。\[**完了**\] をクリックします。

音声用の QoS ポリシーを作成した後で、2 番目にビデオ用のポリシーを作成する必要があります。ビデオ用のポリシーを作成するには、音声ポリシーを作成したときと基本的には同じ手順に従い、次の点を変えます。

  - 異なる (かつ一意の) ポリシー名を使用します (たとえば「**Lync Video**」)。

  - DSCP の値を 46 ではなく「**34**」に設定します。(前に説明したとおり、DSCP の値に 34 を使用する必要はありません。ただ、音声に使用したのとは異なる DSCP の値を割り当てる必要があります。)

  - ビデオ トラフィック用に構成しておいたポート範囲を使用します。たとえば、58000 から 58019 までのポートをビデオ用に予約した場合は、ポート範囲を「**58000:58019**」に設定します。

アプリケーション共有トラフィックを管理するポリシーを作成する場合は、次の点を変えます。

  - 異なる (かつ一意の) ポリシー名を使用します (たとえば「**Lync Server Application Sharing**」)。

  - DSCP の値を 46 ではなく「**24**」に設定します。(この値も 24 にする必要はありません。ただ、音声とビデオに使用した DSCP の値とは別にする必要があります。)

  - ビデオ トラフィック用に構成しておいたポート範囲を使用します。たとえば、42000 から 42019 までのポートをアプリケーション共有用に予約した場合は、ポート範囲を「**42000:42019**」に設定します。

ファイル転送ポリシーは次のようにします。

  - 異なる (かつ一意の) ポリシー名を使用します (たとえば「**Lync Server File Transfers**」)。

  - DSCP の値を「**14**」に設定します。(この値も 14 にする必要はありません。ただ、一意の DSCP にする必要があります。)

  - アプリケーション用に構成しておいたポート範囲を使用します。たとえば、42020 から 42039 までのポートをアプリケーション共有用に予約した場合は、ポート範囲を「**42020:42039**」に設定します。

新しく作成したポリシーは、クライアント コンピューター上でグループ ポリシーが更新されるまで有効になりません。グループ ポリシーは定期的に自動更新を行いますが、グループ ポリシーの更新が必要な各コンピューター上で次のコマンドを実行することにより、強制的に即時更新できます。

    Gpudate.exe /force

このコマンドは、管理者の資格情報で実行されていれば、どのコマンド ウィンドウからでも実行できます。コマンド ウィンドウを管理者の資格情報で実行するには、\[**スタート**\]をクリックして、\[**コマンド プロンプト**\] を右クリックし、\[**管理者として実行**\] をクリックします。

なお、これらのポリシーが対象とするのはクライアント コンピューターです。Lync Server を実行しているサーバーには適用しないでください。

ネットワーク パケットを適切な DSCP の値でマークするには、次の手順に従い、各コンピューター上で新規のレジストリ エントリを作成する必要もあります。

1.  \[**スタート**\] ボタンをクリックし、\[**ファイル名を指定して実行**\] をクリックします。

2.  \[**ファイル名を指定して実行**\] ダイアログ ボックスで、「**regedit**」と入力し、Enter キーを押します。

3.  レジストリ エディターで、\[**HKEY\_LOCAL\_MACHINE**\]、\[**SYSTEM**\]、\[**CurrentControlSet**\]、\[**services**\]、\[**Tcpip**\] の順に展開します。

4.  \[**Tcpip**\] を右クリックし、\[**新規**\] をポイントして、\[**キー**\] をクリックします。新しいレジストリ キーを作成した後で、「**QoS**」と入力し、Enter キーを押してキーの名前を変更します。

5.  \[**QoS**\] を右クリックし、\[**新規**\] をポイントして、\[**文字列値**\] をクリックします。新しいレジストリ値を作成した後で、「**Do not use NLA**」と入力し、Enter キーを押して値の名前を変更します。

6.  \[**Do no use NLA**\] をダブルクリックします。\[**文字列の編集**\] ダイアログ ボックスで、\[**値のデータ**\] ボックスに「**1**」と入力し、\[**OK**\] をクリックします。

7.  レジストリ エディターを閉じ、コンピューターを再起動します。

## 複数のネットワーク アダプターがあるコンピューター上での品質サービスの構成

複数のネットワーク アダプターを持つコンピューターがある場合、DSCP 値が、構成した値ではなく 0x00 と表示される場合があります。通常、このような表示になるのは、1 つ以上のネットワーク アダプターが Active Directory ドメインにアクセスできないコンピューターです (たとえば、アダプターがプライベート ネットワークに使用されている場合)。そのような場合、ドメインへアクセスできるアダプターには DSCP の値がマークされますが、ドメインへアクセスできないアダプターにはマークされません。

ドメインへアクセスできないアダプターも含めて、コンピューターのネットワーク アダプターすべてに DSCP の値をマークしたい場合は、レジストリに値を追加して構成する必要があります。そのためには、次の手順を実行します。

1.  \[**スタート**\] ボタンをクリックし、\[**ファイル名を指定して実行**\] をクリックします。

2.  \[**ファイル名を指定して実行**\] ダイアログ ボックスで、「**regedit**」と入力し、Enter キーを押します。

3.  レジストリ エディターで、\[**HKEY\_LOCAL\_MACHINE**\]、\[**SYSTEM**\]、\[**CurrentControlSet**\]、\[**services**\]、\[**Tcpip**\] の順に展開します。

4.  「**QoS**」というレジストリ キーがない場合は、 \[**Tcpip**\] 右クリックし、\[**新規**\] をポイントして、\[**キー**\] をクリックします。新しいキーを作成した後で、「**QoS**」と入力し、Enter キーを押してキーの名前を変更します。

5.  \[**QoS**\] を右クリックし、\[**新規**\] をポイントして、\[**文字列値**\] をクリックします。新しいレジストリ値を作成した後で、「**Do not use NLA**」と入力し、Enter キーを押して値の名前を変更します。

6.  \[**Do no use NLA**\] をダブルクリックします。\[**文字列の編集**\] ダイアログ ボックスで、\[**値のデータ**\] ボックスに「**1**」と入力し、\[**OK**\] をクリックします。

変更を有効にするには、新しいレジストリ値を作成して構成した後でコンピューターを再起動する必要があります。
