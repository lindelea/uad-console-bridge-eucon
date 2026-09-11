# v1.1.0

## 简体中文

本次更新完善了 UAD Console 控制室在 Avid Control 与 Avid S3 上的实际操作：Mix/Cue 监听源和 Main/ALT1/ALT2 监听组现在可以正确显示、切换并反馈状态，Avid Control 的 Speaker Select 区域也提供可用的 Main 入口。新增 Talk dB 连续控制，TALK 在 S3 Control Room 中按一下开启、再按一下关闭。立体声通道恢复独立的左、右 Pan，并按左声道、右声道的自然顺序显示。实时操作与峰值反馈不加入人为延迟。

插件参数控制继续可用；从 Avid Control/S3 选择或插入插件尚未列为 v1.1.0 正式支持功能，请在 UAD Console 中完成。

## English

This release completes practical UAD Console control-room operation on Avid Control and Avid S3. Mix/Cue sources and Main/ALT1/ALT2 monitor sets now render, switch, and report state correctly; Avid Control also receives a working Main entry in Speaker Select. Talk dB is now continuously controllable, and TALK in the S3 Control Room toggles on with one press and off with the next. Stereo channels again expose independent left and right pan controls in natural L/R order. No artificial delay is added to live control or meter feedback.

Loaded plug-in parameters remain controllable. Selecting or inserting plug-ins from Avid Control/S3 is not a formally supported v1.1.0 feature; use UAD Console for that operation.

## 日本語

このリリースでは、Avid Control と Avid S3 における UAD Console コントロールルーム操作を改善しました。Mix/Cue ソースと Main/ALT1/ALT2 モニターセットが正しく表示・切替・状態反映され、Avid Control の Speaker Select にも実際に動作する Main が表示されます。Talk dB の連続操作に対応し、S3 Control Room の TALK は一度押すとオン、もう一度押すとオフになります。ステレオチャンネルの左右 Pan も独立して、自然な L/R 順で表示されます。操作とメーターには意図的な遅延を追加していません。

ロード済みプラグインのパラメーター操作は引き続き利用できます。Avid Control/S3 からのプラグイン選択・挿入は v1.1.0 の正式対応外のため、UAD Console で行ってください。

The installer and application are currently unsigned. Verify the SHA-256 value shown below after downloading.

`UAD-Console-Bridge-for-EUCON-v1.1.0-Setup-x64.exe`
SHA-256: `8056A1E225C4A72AC7F588B63D2734E959C4B597061D5FE2E9F84A67EBA079E9`

---

# v1.0.0

## 简体中文

首个面向用户的正式版本。提供 Windows 11 x64 安装程序、中英双语应用界面和中英日三语使用手册。支持 Apollo 通道、发送、话放、插件、UNISON、CONFIG 与控制室的实时 EUCON 控制和 dBFS 峰值反馈。已用 Apollo、Avid S3 与 Avid Control 验证，并支持 UAD/EUCON 启动较慢时自动等待重连。

## English

First public user release. Includes a Windows 11 x64 installer, English/Chinese app UI, and English/Chinese/Japanese guides. Provides real-time EUCON control and dBFS metering for Apollo channels, sends, preamps, plug-ins, UNISON, CONFIG, and the control room. Verified with Apollo, Avid S3, and Avid Control, with automatic waiting and reconnection for late UAD/EUCON startup.

## 日本語

一般ユーザー向け初回正式リリースです。Windows 11 x64 インストーラー、中英対応アプリ画面、中英日ユーザーガイドを収録しています。Apollo チャンネル、センド、プリアンプ、プラグイン、UNISON、CONFIG、コントロールルームを EUCON からリアルタイム操作し、dBFS メーターを表示します。Apollo、Avid S3、Avid Control で確認済みで、UAD/EUCON の起動が遅い場合も自動待機・再接続します。

The installer and application are currently unsigned. Verify the SHA-256 value shown below after downloading.

`UAD-Console-Bridge-for-EUCON-v1.0.0-Setup-x64.exe`  
SHA-256: `412D526E47534FDD5640E7337D536146F08DAE28477FF77B265708011308D881`
