# UAD Console Bridge for EUCON User Guide

[简体中文](USER_GUIDE.zh-CN.md) ・ [日本語](USER_GUIDE.ja.md) ・ [Home](../README.md)

## What it does

The app publishes the Apollo DSP mixer in UAD Console as a dedicated EUCON application. It controls channel faders, pan, mute, solo, sends, input preamps, loaded plug-ins, and the control room while providing names, engineering values, levels, and state feedback on the surface.

Audio remains inside Apollo DSP and UAD Console. The bridge provides real-time control and feedback; it does not replace Console or alter the audio driver.

## Requirements

- Windows 11, 64-bit.
- A working Apollo and UAD Console installation. Confirm that Console can see the interface and its meters first.
- Avid EuControl / EUCON Workstation 2026.4 installed and working.
- A compatible surface connected in EuControl, or a tablet running Avid Control.

## Install

1. Download the file ending in `Setup-x64.exe` from [Releases](https://github.com/lindelea/uad-console-bridge-eucon/releases/latest).
2. Quit any portable copy you previously started, run the installer, and follow the prompts.
3. Open **UAD Console Bridge for EUCON** from the Start menu.

The project does not currently have a paid Windows code-signing certificate, so Windows may show “Unknown publisher.” Download only from this repository and compare the file with the SHA-256 value on the release page if needed.

## First connection

1. Start UAD Console and confirm that Apollo is online.
2. Start EuControl and confirm that your surface is online.
3. Start the bridge. Once the overview shows interfaces, sample rate, and channels and EUCON reports ready, control is available.
4. Choose the required control scope in Settings and save it. If reinstalling the UAD driver makes Apollo appear as a new device, apply the scope once again; the bridge does not need reinstalling.
5. Press `Ctrl+Alt+Shift+U` to bring the bridge forward and make it the current EuControl application. Settings decide whether it returns to the background after recognition.

The companion defaults do not conflict: Windows EUCON uses `Ctrl+Alt+Shift+W`, UAD EUCON uses `Ctrl+Alt+Shift+U`, and Mackie Control uses `Ctrl+Alt+Shift+M`. **Windows EUCON** and **UAD EUCON** commands can also be assigned to EuControl Soft Keys.

The bridge waits for a late UAD Mixer Engine or EUCON service and reconnects automatically, so sign-in startup order is not critical.

## Channel control

- Fader: real-time channel level with reconciliation from Console state.
- Pan: normal pan for mono channels; stereo channels retain separate left and right positions. Press the corresponding encoder to return to center.
- Mute / Solo: change and display the actual Console state.
- Sends / Cues: supported send level and pan with engineering-unit feedback.
- Input / Preamp: supported gain, input, pad, phantom power, polarity, HPF, and related controls.
- Inserts / UNISON: parameters of already loaded plug-ins. Touching or turning an encoder shows the parameter's real value rather than a percentage.
- CONFIG: select or remove a plug-in and recall presets already present in Console. Turn to choose and press `In` to confirm.
- Meters: native Console dBFS data delivered to the app and EUCON as quickly as possible.

Each channel exposes only the features it actually supports. If device or plug-in topology changes, stale page actions are discarded and controls bind to the newest Console state.

## Control room

The control room is separate and does not consume a normal channel fader. It includes main monitor level, MUTE, DIM, MONO, monitor source, DIM depth, and TALKBACK. Main level is a continuous real-time control; it is not held until the gesture ends.

The monitor ceiling in Settings limits only targets sent by this bridge. It does not limit Console, Apollo hardware, or acoustic SPL and may be set as high as 0 dB.

## Multiple Apollo interfaces

When multiple Apollo units form one online system in UAD Console, the bridge builds its list from the device and channel identities supplied by Console rather than assuming a single unit. Added, removed, or re-identified hardware refreshes the relevant channels, and a disconnected identity receives no further action. Available channel count, cascading, and features still follow the installed UAD Console and driver.

## Settings and background operation

Settings include English/Chinese language, hidden startup, close to tray, launch at Windows sign-in, automatic EUCON connection, CONFIG, control scope, monitor ceiling, and the global summon shortcut. The default is `Ctrl+Alt+Shift+U` and can be re-recorded.

Closing the window normally hides it in the notification area. Use the tray menu to show, configure, restart, or fully quit the bridge.

## Troubleshooting

**No Apollo data in the overview:** first confirm that UAD Console itself is working. Wait a few seconds; if it still does not connect, restart the bridge from its tray menu. Do not routinely terminate UAMixerEngine to recover the bridge.

**EUCON cannot see the bridge:** confirm that EuControl is running, check its Applications page, then press `Ctrl+Alt+Shift+U`.

**The level changes but the fader rebounds:** open Settings and apply the current control scope again so the bridge records the device identity created by a driver reinstall, then restart the bridge once.

**A plug-in or CONFIG item is missing:** confirm that the Console channel supports the slot or feature and that CONFIG is enabled. Some CONFIG exposure changes take effect after restarting this bridge.

**Uninstall:** use Windows Settings → Apps → Installed apps. Personal settings are retained for reinstall.

## Report a problem

Open a [GitHub issue](https://github.com/lindelea/uad-console-bridge-eucon/issues) with Apollo model/count, UAD Software, EuControl and surface versions, reproduction steps, and observed result. Logs may contain device, channel, and plug-in names, so review them before uploading.
