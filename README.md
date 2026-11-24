# 🎙️ 用 Chromecast 遥控器在 Mac 上语音打字

[English](README.en.md)

按住遥控器的话筒键说话，松开后由豆包输入法或微信输入法转成文字。也可以把方向键、音量键等 12 个按键设为 Mac 快捷操作。

[**⬇️ 下载 Mac 应用（434 预览版）**](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-arm64.zip) · [版本说明](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/tag/v2.0.9-chromecast.434)

## 💻 兼容性与安装

需要 **Apple 芯片 Mac（macOS 14 或更新版本）** 和 **Chromecast with Google TV 语音遥控器（G9N9N）**。型号可在电池仓查看。Google TV Streamer 遥控器及其他型号尚未验证。

解压 ZIP，把 **Chromecast Remote for Mac.app** 拖到「应用程序」后打开。434 使用临时签名，未经 Apple 公证。若系统提示无法验证开发者，请确认下载来源后参阅 [Apple 的打开说明](https://support.apple.com/zh-cn/102445)。语音打字实测使用的是此前的本地版本。

## ⚙️ 首次设置

1. **连接遥控器。** 在 Mac 的「系统设置 → 蓝牙」配对。搜不到时，同时按住遥控器的「返回」和「主页」直到灯闪。打开 App，在「连接」中选中遥控器，按提示授权蓝牙、输入监控和辅助功能，再重启 App。
2. **设置虚拟麦克风。** 有 **MiRemoteV 2ch** 就直接用，否则按[说明安装 SayAll 虚拟麦克风](https://github.com/HD838A/remote-mic-app/blob/0e10dc16890afdc3b9c8bb007671a27ff44e0e13/Resources/豆包输入法兼容说明.md)。在 App 的「音频输出」和输入法的「麦克风」里选择同一个设备。
3. **测试语音打字。** 将输入法的「按住说话」设为 **Fn**，关闭豆包和微信输入法的全局语音快捷键。若使用豆包免按模式，为它指定其他键。切到目标输入法，在备忘录里按住遥控器的话筒键说一句，再松开。

想用 Netflix 键切换输入法？在「按键 → Netflix 键 → 单击 → 系统与媒体」选择「切换豆包与微信输入法」。

[Google 配对说明](https://support.google.com/chromecast/answer/10109990) · [反馈问题](https://github.com/LeonLVup/Sayall-chromecast-remote-version/issues)

## 📦 源码与许可

本项目是 [HD838A 的无线麦 SayAll](https://github.com/HD838A/remote-mic-app) 的第三方适配版，语音实现参考了[上游 PR #876](https://github.com/HD838A/remote-mic-app/pull/876)。[434 源码包](https://github.com/LeonLVup/Sayall-chromecast-remote-version/releases/download/v2.0.9-chromecast.434/Chromecast-Remote-macOS-2.0.9-434-source.tar.gz)内的 `CHROMECAST-BUILD.md` 提供构建步骤。

[GPL-3.0-only](LICENSE.md) · [版权](COPYRIGHT.md) · [原项目图标许可](LOGO-LICENSE.md) · [第三方声明](THIRD_PARTY_NOTICES.md) · [开发文档](DOCUMENTATION.md)
