# UAD Console Bridge for EUCON ユーザーガイド

[简体中文](USER_GUIDE.zh-CN.md) ・ [English](USER_GUIDE.en.md) ・ [ホーム](../README.md)

## このアプリについて

UAD Console の Apollo DSP ミキサーを、独立した EUCON アプリケーションとして公開します。チャンネルフェーダー、パン、Mute、Solo、センド、入力プリアンプ、ロード済みプラグイン、コントロールルームを操作し、サーフェスへ名称、実値、レベル、状態を表示します。

オーディオ処理は Apollo DSP と UAD Console が行います。本アプリはリアルタイムの操作とフィードバックを担当し、Console やオーディオドライバーを置き換えません。

![UAD Console Bridge の概要画面](images/overview.png)

## 動作条件

- 64 ビット版 Windows 11。
- Apollo と UAD Console が正常に動作していること。先に Console でインターフェースとメーターを確認してください。
- Avid EuControl / EUCON Workstation 2026.4 が正常に動作していること。
- EuControl に接続された互換サーフェス、または Avid Control を実行するタブレット。

## インストール

1. [Releases](https://github.com/lindelea/uad-console-bridge-eucon/releases/latest) から、ファイル名が `Setup-x64.exe` で終わるインストーラーをダウンロードします。
2. 以前に起動したポータブル版を終了し、インストーラーの案内に従います。
3. スタートメニューから **UAD Console Bridge for EUCON** を起動します。

現在は有料の Windows コード署名証明書がないため、「不明な発行元」と表示される場合があります。本リポジトリからのみ入手し、必要に応じて公開されている SHA-256 値を確認してください。

## 初回接続

1. UAD Console を起動し、Apollo がオンラインであることを確認します。
2. EuControl を起動し、サーフェスがオンラインであることを確認します。
3. 本アプリを起動します。概要にインターフェース、サンプルレート、チャンネルが表示され、EUCON が Ready になれば操作できます。
4. 設定で必要なコントロール範囲を選び、保存します。UAD ドライバー再インストール後に Apollo が新しい機器として認識された場合は、範囲をもう一度適用するだけで、本アプリの再インストールは不要です。
5. `Ctrl+Alt+Shift+U` を押すと本アプリが前面に出て、EuControl の現在アプリになります。認識後にバックグラウンドへ戻すかは設定で選べます。

![コントロール範囲の設定](images/control.png)

既定キーは重複しません。Windows EUCON は `Ctrl+Alt+Shift+W`、UAD EUCON は `Ctrl+Alt+Shift+U`、Mackie Control は `Ctrl+Alt+Shift+M` です。EuControl の Soft Key に **Windows EUCON** と **UAD EUCON** コマンドを割り当てることもできます。

UAD Mixer Engine や EUCON サービスの起動が遅い場合も待機して自動再接続するため、サインイン時の厳密な起動順は不要です。

## チャンネル操作

- フェーダー：チャンネルレベルをリアルタイム送信し、Console の状態で最終同期します。
- Pan：モノは通常のパン、ステレオは左右を個別に保持します。対応エンコーダーを押すとセンターへ戻ります。
- Mute / Solo：Console の実際の状態を操作・表示します。
- Sends / Cues：対応するセンドレベルとパンを実単位で表示します。
- Input / Preamp：対応するゲイン、入力、PAD、48V、極性、HPF などを操作します。
- Inserts / UNISON：ロード済みプラグインのパラメーターを操作します。触れる・回すとパーセントではなく実際の値を表示します。
- CONFIG：現在のプラグイン構成を表示します。v1.1.0 では Avid Control/S3 からのプラグイン選択・挿入は正式対応外です。ロードや交換は UAD Console で行ってください。
- メーター：Console の dBFS データをアプリと EUCON へできるだけ速く送ります。

各チャンネルには実際に対応する機能だけが表示されます。機器やプラグイン構成が変わると古い操作を破棄し、最新の Console 状態へ結び直します。

## コントロールルーム

コントロールルームは通常チャンネルとは別で、チャンネルフェーダーを消費しません。メインモニター音量、MUTE、DIM、MONO、Mix/Cue ソース、Main/ALT1/ALT2 モニターセット、DIM 深度、TALKBACK、Talk dB を操作できます。メイン音量と Talk dB は連続リアルタイム制御です。Avid Control の Speaker Select には `Main` も表示され、Main セットボタンと同じ実際の切り替えを行います。

設定のモニター上限は本アプリから送る目標値だけを制限します。Console、Apollo 本体、実際の音圧を制限するものではなく、0 dB まで設定できます。

## 複数の Apollo

複数の Apollo が UAD Console で一つのオンラインシステムとして正しく構成されている場合、本アプリは一台固定ではなく、Console が提供する機器・チャンネル識別情報から一覧を作ります。追加、取り外し、再認識時には該当チャンネルを更新し、切断済みの古い識別先へ操作を送りません。利用できる台数、カスケード方法、機能は、現在の UAD Console とドライバーの対応範囲に従います。

## 設定とバックグラウンド動作

表示言語、起動時に隠す、トレイ常駐、Windows サインイン時の起動、EUCON 自動接続、CONFIG、コントロール範囲、モニター上限、グローバル呼び出しキーを設定できます。既定は `Ctrl+Alt+Shift+U` で、変更可能です。

通常、ウィンドウを閉じても通知領域で動作します。表示、設定、再起動、完全終了はトレイメニューから行います。

## トラブルシューティング

**概要に Apollo データがない：** まず UAD Console 自体が正常か確認します。数秒待っても接続しない場合は、トレイから本アプリを再起動します。日常的な復旧のために UAMixerEngine を強制終了しないでください。

**EUCON に表示されない：** EuControl が動作していること、Applications ページに登録されていることを確認し、`Ctrl+Alt+Shift+U` を押します。

**音量は変わるがフェーダーが戻る：** 設定で現在のコントロール範囲を再適用し、ドライバー再インストール後の機器識別情報を記録してから、本アプリを一度再起動します。

**プラグイン／CONFIG 項目がない：** v1.1.0 では Avid Control/S3 からのプラグイン選択・挿入は正式対応外です。UAD Console で行ってください。ロード済みプラグインのパラメーターは引き続き EUCON から操作できます。

**アンインストール：** Windows 設定 → アプリ → インストールされているアプリから削除します。再インストール用に個人設定は保持されます。

## 不具合報告

[GitHub Issues](https://github.com/lindelea/uad-console-bridge-eucon/issues) に、Apollo の型番と台数、UAD Software、EuControl、サーフェスのバージョン、再現手順、結果を記載してください。ログには機器、チャンネル、プラグイン名が含まれる場合があるため、アップロード前に確認してください。
