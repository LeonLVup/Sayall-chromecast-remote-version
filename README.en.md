# Dictate on your Mac with a Chromecast remote

[简体中文](README.md)

Connect the Google remote to your Mac, **hold its microphone button to speak, and release it to turn your voice into text** with Doubao Input Method or WeType. You can also assign Mac shortcuts to the direction, Select, and side volume buttons.

[**Download the Mac app (434 preview)**](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-arm64.zip) · [Release notes and source](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/tag/v2.0.9-chromecast.434)

## Will it work with my devices?

- **Remote**: The Google Voice Remote that came with Chromecast with Google TV, model **G9N9N**. Check the label inside the battery compartment. The Google TV Streamer remote and other models have not been verified.
- **Mac**: An Apple silicon Mac running **macOS 14 or later**. Check the chip and macOS version under **Apple menu → About This Mac**.
- **Input method**: Dictation was tested with **Doubao Input Method** and **WeType** (WeChat Input Method). You will also need a compatible virtual microphone, as described below.

## Download and open

1. Click **Download the Mac app** above. The file name ends in **arm64.zip**. The **Source code** and **source.tar.gz** files on the release page are for readers who want to inspect or build the software.
2. Double-click the ZIP in Downloads. Move **Chromecast Remote for Mac.app** to Applications and open it.
3. Build 434 is an ad hoc signed preview without Apple notarization. If macOS says it cannot verify the developer, confirm you downloaded it from the release page above and see [Apple’s instructions for opening apps](https://support.apple.com/en-us/102445).

The download is ready to try without Terminal, Xcode, or compiling. The build 434 archive and signature were verified. Dictation was tested with the earlier local build.

## Set up dictation

1. **Pair the remote.** Go to **System Settings → Bluetooth** on the Mac and connect the Chromecast remote. If it does not appear, hold **Back and Home** together until the light pulses and look again. Select it on the app’s connection page and grant Bluetooth, Input Monitoring, and Accessibility permissions when prompted. Quit and reopen the app after granting permissions. [Google pairing instructions](https://support.google.com/chromecast/answer/10109990)
2. **Select the same virtual microphone.** It passes the remote audio to the input method. If your Mac already shows **MiRemoteV 2ch**, you can use it. Otherwise, see the [upstream virtual microphone setup](https://github.com/HD838A/remote-mic-app/blob/0e10dc16890afdc3b9c8bb007671a27ff44e0e13/Resources/豆包输入法兼容说明.en.md). A new installation following that guide shows **SayAll** as the device name. Choose the **same device** for the app’s audio output and the input method’s microphone. The virtual microphone is installed separately from the app ZIP.
3. **Try a sentence.** Set the input method’s hold-to-talk shortcut to **Fn** and turn off the global voice shortcuts in Doubao and WeType. Switch to the input method you want, click in a blank note, hold the **remote’s microphone button**, say a sentence, and release. If you use Doubao’s hands-free mode, assign it a different shortcut, such as Right Option.

If the button responds but no text appears, check that the audio devices match and the cursor is in an editable field. In QuickTime Player, you can choose **File → New Audio Recording**, select the same microphone, and check whether its input level moves while you hold the remote’s microphone button and speak. [Report an issue](https://github.com/LeonLVup/Sayall-chromecast-remote-version/issues)

## How is this different from SayAll?

- This version adds a **G9N9N** layout and hold-to-talk support. You can customize **12 buttons**, including the four directions, Select, Back, Volume Up and Down, Home, Mute, YouTube, and Netflix.
- To switch between Doubao and WeType with Netflix, open **Buttons → Netflix → Single Click → System & Media** and select **Switch Between Doubao and WeType**. It switches between those two even if you use ABC in between.
- This preview has its own app name and icon. It uses a separate app identity and has upstream updates disabled. Your selected input method handles speech-to-text.

## Upstream acknowledgments

Thanks to [HD838A](https://github.com/HD838A) for creating and maintaining SayAll. This third-party adaptation builds on its public code. [Original project HD838A/remote-mic-app](https://github.com/HD838A/remote-mic-app)

## Source and license

The build 434 release includes the corresponding source archive. See `CHROMECAST-BUILD.md` inside the archive for build instructions. The patch is licensed under GPL-3.0-only. The public Chromecast voice implementation builds on [upstream PR #876](https://github.com/HD838A/remote-mic-app/pull/876). [GPL license](LICENSE.md) · [Copyright](COPYRIGHT.md) · [Upstream icon license](LOGO-LICENSE.md) · [Third-party notices](THIRD_PARTY_NOTICES.md)

<details>
<summary>For developers: apply the patch and build</summary>

Use an Apple Silicon Mac running macOS 14 or later and an Xcode toolchain with Swift 6.2 or later. For unit tests, select a full Xcode installation with Swift Testing.

```bash
git clone https://github.com/LeonLVup/Sayall-chromecast-remote-version.git
git clone https://github.com/HD838A/remote-mic-app.git
cd remote-mic-app
git switch --detach 0e10dc16890afdc3b9c8bb007671a27ff44e0e13
git apply --check ../Sayall-chromecast-remote-version/sayall-chromecast-source.patch
git apply ../Sayall-chromecast-remote-version/sayall-chromecast-source.patch

SAYALL_PRIVATE_PLATFORM_MODE=public SAYALL_PUBLIC_CHROMECAST_VOICE=1 \
  xcrun swift build --disable-keychain --product RemoteMic
```

To package an app for local testing, first replace `Resources/AppIcon.png`, `Resources/AppIcon.icns`, `Resources/AppIcons/standard.png`, and `Resources/AppIcons/faceted-duck.png` with artwork you have the right to use. Use a distinct app name and bundle identifier and disable the upstream update feed to keep the test build separate from the official app and its updates. Then run the following in the patched source tree.

```bash
# Use a bundle identifier you control.
plutil -replace CFBundleIdentifier -string org.example.ChromecastRemoteTest Resources/Info.plist
plutil -replace SUEnableAutomaticChecks -bool false Resources/Info.plist
plutil -remove SUFeedURL Resources/Info.plist

SAYALL_BUILD_CHANNEL=public SAYALL_PRIVATE_PLATFORM_MODE=public \
  SAYALL_PUBLIC_CHROMECAST_VOICE=1 ./scripts/build-app.sh
```

The app bundle is written to `dist/SayAll.app`. Use it as a separate local test app so that it does not overwrite an existing installation.

</details>
