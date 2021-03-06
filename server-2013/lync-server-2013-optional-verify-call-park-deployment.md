﻿---
title: 'Lync Server 2013: (オプション) コール パーク展開の確認'
TOCTitle: (オプション) コール パーク展開の確認
ms:assetid: fcfe0962-1a9c-4cbd-847c-fed40e3b1480
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg413076(v=OCS.15)
ms:contentKeyID: 48274200
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (オプション) Lync Server 2013 でのコール パーク展開の確認

 

_**トピックの最終更新日:** 2012-09-11_

コール パークをインストールして、構成したら、構成を検証して通話を保留する操作と通話を取る操作が予想どおりに機能するかどうかを確認する必要があります。少なくとも、以下を確認してください。

  - コール パークを有効にしているユーザーに電話をかけて、そのユーザーに電話を保留してもらいます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>このテストの開始直前に音声ポリシーで コール パークを有効にした場合は、通話を保留するユーザーが Lync Server からサインアウトした後再びサインインして、転送通話リストで コール パーク オプションを表示できるようにする必要があります。</td>
    </tr>
    </tbody>
    </table>


  - オービット番号をダイヤルして、電話を取ります。

  - 別の通話を保留して、保留した通話がタイムアウトするようにして、リングバックは取らないようにします。タイムアウトした通話が **OnTimeoutURI** で指定されているフォールバック宛先に正しくルーティングされていることを確認します。

