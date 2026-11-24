# 🎙️ Dictate on your Mac with a Chromecast remote

[简体中文](README.md)

Hold the remote’s microphone button to speak, then release it to get text from Doubao Input Method or WeType (WeChat Input Method). You can also map 12 buttons, including the direction and volume buttons, to Mac shortcuts.

[**⬇️ Download the Mac app (434 preview)**](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-arm64.zip) · [Release notes](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/tag/v2.0.9-chromecast.434)

## 💻 Compatibility and installation

You’ll need an **Apple silicon Mac (macOS 14 or later)** and a **Chromecast with Google TV Voice Remote (G9N9N)**. Check the model inside the battery compartment. The Google TV Streamer remote and other models remain untested.

Unzip the download, move **Chromecast Remote for Mac.app** to Applications, and open it. Build 434 is ad hoc signed and has no Apple notarization. If macOS can’t verify the developer, confirm where you downloaded the app and see [Apple’s instructions](https://support.apple.com/en-us/102445). Dictation was tested on an earlier local build.

## ⚙️ First-time setup

1. **Pair the remote.** Use **System Settings → Bluetooth**. If the remote doesn’t appear, hold Back and Home together until the light flashes. Select the remote in the app’s connection settings, grant Bluetooth, Input Monitoring, and Accessibility permissions when prompted, then quit and reopen the app.
2. **Set up a virtual microphone.** Use **MiRemoteV 2ch** if it’s already installed, or [install the SayAll virtual microphone](https://github.com/HD838A/remote-mic-app/blob/0e10dc16890afdc3b9c8bb007671a27ff44e0e13/Resources/豆包输入法兼容说明.en.md). Select the same device for the app’s audio output and your input method’s microphone.
3. **Try dictation.** Set hold-to-talk to **Fn** and turn off global voice shortcuts in Doubao and WeType. If you use Doubao’s hands-free mode, give it a different shortcut. Switch to the input method you want, click in a note, hold the remote’s microphone button while you speak, then release it.

To switch input methods with Netflix, open **Buttons → Netflix → Single Click → System & Media** and select **Switch Between Doubao and WeType**.

[Google pairing guide](https://support.google.com/chromecast/answer/10109990) · [Report an issue](https://github.com/LeonLVup/Sayall-chromecast-remote-version/issues)

## 📦 Source and license

This is a third-party adaptation of [SayAll by HD838A](https://github.com/HD838A/remote-mic-app). The voice implementation builds on [upstream PR #876](https://github.com/HD838A/remote-mic-app/pull/876). The [434 source archive](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-source.tar.gz) includes build instructions in `CHROMECAST-BUILD.md`.

[GPL-3.0-only](LICENSE.md) · [Copyright](COPYRIGHT.en.md) · [Upstream icon license](LOGO-LICENSE.en.md) · [Third-party notices](THIRD_PARTY_NOTICES.md) · [Developer docs](DOCUMENTATION.md)
