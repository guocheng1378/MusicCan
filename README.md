# MusicCan

针对小米 17 Pro / Pro Max 背屏音乐显示白名单的绕过方案。

使用 `com.luna.music` 包名模拟系统音乐应用，自动监听其他媒体会话并进行包装，使不受白名单支持的第三方音乐应用也能在背屏显示媒体控件和歌词。

## 工作原理

小米背屏仅允许白名单内的应用显示媒体控件。MusicCan 通过以下方式绕过限制：

1. 使用系统白名单中的 `com.luna.music` 包名
2. 监听设备上所有活跃的媒体会话
3. 将第三方音乐应用的媒体会话包装为系统可识别的形式
4. 使非白名单应用的音乐也能在背屏正常显示

## 前置条件

- 已 Root 的小米 17 Pro 或 Pro Max 设备
- Android 8.1 及以上
- 建议搭配 [REAREye](https://github.com/killerprojecte/REAREye) 使用

## 安装

### 1. 下载

从 [Releases](https://github.com/killerprojecte/MusicCan/releases) 下载最新版本的 APK（如果有的话），或自行构建。

### 2. 构建

```bash
git clone https://github.com/killerprojecte/MusicCan.git
cd MusicCan
./gradlew assembleDebug
```

### 3. 安装

通过文件管理器或 ADB 安装 APK：

```bash
adb install app/build/outputs/apk/debug/app-debug.apk
```

## 使用

1. 安装并打开 MusicCan
2. 在第三方音乐应用中播放音乐
3. MusicCan 会自动监听并包装媒体会话
4. 背屏应能显示音乐控件和歌词

## 注意事项

- 播放媒体的应用在超级岛、媒体中心上将不再直接显示（由 MusicCan 代理显示）
- 媒体包装功能存在概率性，可能被原始应用的通知顶掉
- 在 Apple Music 中直接播放大概率失败，建议返回桌面后通过超级岛或媒体中心播放
- 调整播放进度（包括上一曲按钮触发的重置）可能导致包装失效

## 已知问题

| 问题 | 状态 | 说明 |
| --- | --- | --- |
| Apple Music 直接播放失败 | 🔴 | 返回桌面后通过超级岛播放可解决 |
| 调整播放进度后包装失效 | 🔴 | 暂时无法解决 |
| 原始应用通知顶掉包装 | 🟡 | 存在概率性 |

## 与 REAREye 的关系

REAREye 提供了**音乐控件白名单**功能，可以直接在模块中添加第三方音乐应用到白名单。MusicCan 是一个独立的轻量方案，适用于以下场景：

- 不想使用 REAREye 的用户
- REAREye 白名单不生效的情况
- 需要更细粒度的媒体会话控制

## 贡献

- 本项目不会收取任何费用
- 项目依据 [GPL-3.0](LICENSE) 协议分发
- 欢迎有开发能力的用户向本项目贡献代码

## 许可证

[GPL-3.0](LICENSE)
