# 用 Chromecast 遥控器在 Mac 上语音打字

[English](README.en.md)

把 Google 遥控器连到 Mac，**按住话筒键说话，松开后由豆包输入法或微信输入法把语音变成文字**。方向键、确认键、侧边音量键等也可以改成 Mac 快捷操作。

[**下载 Mac 应用（434 预览版）**](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-arm64.zip) · [版本说明和源码](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/tag/v2.0.9-chromecast.434)

## 我的设备能用吗？

- **遥控器**：随 Chromecast with Google TV 提供的 Google 语音遥控器，型号 **G9N9N**。可以查看电池仓内的型号。Google TV Streamer 遥控器和其他型号尚未验证。
- **电脑**：Apple 芯片 Mac，运行 **macOS 14 或以上**。在「苹果菜单 → 关于本机」查看「芯片」和系统版本。
- **输入法**：语音打字已用**豆包输入法**和**微信输入法**测试。还需要一个兼容的虚拟麦克风，配置见下方。

## 下载并打开

1. 点上方的「下载 Mac 应用」。文件名以 **arm64.zip** 结尾。发布页上的 **Source code** 和 **source.tar.gz** 是给想看代码或自己编译的人用的。
2. 在「下载」里双击 ZIP，把解压出的 **Chromecast Remote for Mac.app** 拖进「应用程序」，再打开。
3. 434 是临时签名的预览版，未经 Apple 公证。如果 Mac 提示无法验证开发者，请先确认文件来自上方发布页，再查看 [Apple 的打开说明](https://support.apple.com/zh-cn/102445)。

用上面的下载包，无需终端、Xcode 或编译。434 已检查下载包和签名完整性，语音功能实测用的是此前的本地版本。

## 第一次设置语音打字

1. **连遥控器。** 打开 Mac 的「系统设置 → 蓝牙」，连接 Chromecast 遥控器。如果搜索不到，同时按住遥控器的**返回键和主页键**，等指示灯闪烁后再找。打开 App，在「连接」里选中遥控器，按提示允许蓝牙、输入监控和辅助功能。授权后完全退出并重新打开 App。[Google 配对说明](https://support.google.com/chromecast/answer/10109990)
2. **选同一个虚拟麦克风。** 它负责把遥控器的声音交给输入法。若 Mac 上已有 **MiRemoteV 2ch**，可以直接用。若没有，请看原项目的[虚拟麦克风安装说明](https://github.com/HD838A/remote-mic-app/blob/0e10dc16890afdc3b9c8bb007671a27ff44e0e13/Resources/豆包输入法兼容说明.md)。按该说明新安装的设备名为 **SayAll**。在本 App 的「音频输出」和输入法的「麦克风」中选**同一个设备**。本下载包需另装虚拟麦克风。
3. **试着说一句。** 在要用的输入法里，将「按住说话」设为 **Fn**，关闭豆包和微信输入法的全局语音快捷键。切换到目标输入法，点进备忘录的空白处，按住**遥控器上的话筒键**说一句，再松开。如果豆包启用了免按模式，把免按快捷键设成其他键，例如右 Option。

如果遥控器有反应但没有出字，先看 App 和输入法选的是不是同一个虚拟麦克风，再确认光标在输入框里。可以用 QuickTime Player 的「文件 → 新建音频录制」选同一个麦克风，看按住话筒键说话时电平会不会动。[反馈问题](https://github.com/LeonLVup/Sayall-chromecast-remote-version/issues)

## 和原版 SayAll 有什么区别？

- 这个版本为 **G9N9N** 增加了对应的按键布局和按住话筒键说话。可以自定义 **12 个键**，包括四个方向键、确认、返回、音量加减、主页、静音、YouTube 和 Netflix。
- 想用 Netflix 键切换豆包和微信输入法，可以在「**按键 → Netflix 键 → 单击 → 系统与媒体**」选择「**切换豆包与微信输入法**」。即使中途用过 ABC，它也只在这两个输入法之间切换。
- 下载包有独立的应用名称和图标，停用了原版的更新源。语音转文字仍由你选择的输入法完成。

## 上游致谢

感谢 [HD838A](https://github.com/HD838A) 创建并维护无线麦 SayAll。这个第三方适配版基于原项目的公开代码。[原项目 HD838A/remote-mic-app](https://github.com/HD838A/remote-mic-app)

## 源码与许可

434 下载页提供与安装包对应的源码压缩包，里面的 `CHROMECAST-BUILD.md` 说明怎样编出同一版本。补丁按 GPL-3.0-only 发布。公开的 Chromecast 语音实现参考了[上游 PR #876](https://github.com/HD838A/remote-mic-app/pull/876)。[GPL 许可](LICENSE.md) · [版权说明](COPYRIGHT.md) · [原项目图标许可](LOGO-LICENSE.md) · [第三方声明](THIRD_PARTY_NOTICES.md)

<details>
<summary>开发者：应用源码补丁并编译</summary>

准备 Apple Silicon Mac、macOS 14 或以上，以及带 Swift 6.2 或以上的 Xcode 工具链。需要运行单元测试时，请选用含 Swift Testing 的完整 Xcode。

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

如需生成可在本机试用的 App，先用你拥有使用权的图片和图标替换 `Resources/AppIcon.png`、`Resources/AppIcon.icns`、`Resources/AppIcons/standard.png` 和 `Resources/AppIcons/faceted-duck.png`。请使用独立的 App 名称和 Bundle ID，并停用官方自动更新来源，避免和官方 App 的设置或更新混用。然后在同一源码目录运行：

```bash
# 换成你自己使用的 Bundle ID。
plutil -replace CFBundleIdentifier -string org.example.ChromecastRemoteTest Resources/Info.plist
plutil -replace SUEnableAutomaticChecks -bool false Resources/Info.plist
plutil -remove SUFeedURL Resources/Info.plist

SAYALL_BUILD_CHANNEL=public SAYALL_PRIVATE_PLATFORM_MODE=public \
  SAYALL_PUBLIC_CHROMECAST_VOICE=1 ./scripts/build-app.sh
```

生成的 App 在 `dist/SayAll.app`。将其作为单独的本地测试 App 试用，避免覆盖现有的 App。

</details>
