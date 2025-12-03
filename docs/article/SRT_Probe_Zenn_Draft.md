# SRTプロトコルの通信テストが超簡単に！「SRT Probe」の使い方入門

## はじめに

最近、映像伝送の現場で標準になりつつある **SRT (Secure Reliable Transport)** プロトコル。
低遅延で安定した伝送ができる素晴らしいプロトコルですが、「繋がらない」「パケットロスが出ているかも？」といったトラブルシューティングや、ネットワーク環境の事前テストをする際、手軽に使えるツールが少なくて困ったことはありませんか？

今回は、そんな時に便利なWindows用ツール **「SRT Probe」** を紹介します。
映像を送る機能はありませんが、**「SRTで繋がるか」「回線品質はどうか（RTT、パケットロス、スループット）」** をサクッと確認することに特化したツールです。

## SRT Probe とは？

SRT Probeは、SRTプロトコルの接続テストとパフォーマンス測定を行うためのツールです。

*   **リアルタイム統計**: RTT（往復遅延時間）、スループット、パケットロス率をグラフで可視化
*   **3つのモード対応**: Caller, Listener, Rendezvous の全モードに対応
*   **シンプル**: 映像の入出力機能がないため、動作が軽く、設定もシンプル

## インストール方法

Windows 10/11 に対応しています。以下のいずれかの方法でインストールできます。

### 1. Microsoft Store からインストール（推奨）

Microsoft Storeからワンクリックでインストールでき、自動更新にも対応しています。

[Microsoft Storeで「SRT Probe」をダウンロード](https://apps.microsoft.com/detail/9NLQLPL2SBZ1?hl=ja&gl=JP&ocid=pdpshare)

### 2. GitHub からインストーラーをダウンロード

GitHubのリリースページからインストーラー（exeファイル）をダウンロードすることも可能です。

[GitHub Releases ページ](https://github.com/videosupporter/srt-probe/releases)

## 使い方：1台のPCで接続テストをしてみよう

SRT Probeの便利な点は、**1台のPCで複数起動できる**ことです。
これを利用して、自分自身に接続（ローカルループバックテスト）を行い、ツールの使い方や動作を確認してみましょう。

### 手順1: アプリを2つ起動する

インストールした「SRT Probe」を **2回** 起動してください。画面上にウィンドウが2つ並ぶように配置します。
片方を「受信側（サーバー）」、もう片方を「送信側（クライアント）」として使います。

### 手順2: 受信側（Receiver）の設定

まず、片方のウィンドウ（右側など）を設定します。

1.  **Test Mode**: `Receiver (listener)` を選択
2.  **Listen Port**: `9000` （デフォルトのまま）
3.  **Start Test** ボタンをクリック

これで、相手からの接続を待つ状態（Listening）になりました。Statusは「Listening...」になります。

### 手順3: 送信側（Sender）の設定

もう片方のウィンドウ（左側など）を設定します。

1.  **Test Mode**: `Sender (caller)` を選択
2.  **Destination IP**: `127.0.0.1` と入力
    *   ※ `127.0.0.1` は「自分自身」を指す特別なIPアドレスです。
3.  **Destination Port**: `9000` （受信側と同じポート）
4.  **Start Test** ボタンをクリック

### 手順4: 接続確認

設定が正しければ、一瞬で接続が確立され、Statusが **「Connected」** に変わります。

*   **RTT**: ローカル接続なので `0ms` ～ `1ms` 程度が表示されます。
*   **Throughput**: データが流れている速度が表示されます。
*   **Packet Loss**: 安定していれば `0%` のはずです。

グラフが動き出し、リアルタイムに通信状況が確認できれば成功です！

## 実際の現場での活用

今回は1台のPCでテストしましたが、実際の現場では以下のように使えます。

*   **PC A（送信拠点）**: Senderモードで、PC BのグローバルIPを指定
*   **PC B（受信拠点）**: Listenerモードで待機（ポート開放が必要）

映像伝送の本番前にこのツールでテストを行うことで、「回線に問題があるのか」「エンコーダー/デコーダーの設定に問題があるのか」の切り分けが非常にスムーズになります。

## おわりに

SRT Probeはオープンソースで開発されています。
機能要望やバグ報告はGitHub Issuesまでお寄せください。

*   **GitHubリポジトリ**: [https://github.com/videosupporter/srt-probe](https://github.com/videosupporter/srt-probe)
*   **ドキュメント**: [https://videosupporter.github.io/srt-probe/](https://videosupporter.github.io/srt-probe/)
