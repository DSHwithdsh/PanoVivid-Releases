# 幻瞳界域 1.0.7-android.8 · Android

versionName 1.0.7-android.8 · versionCode 10702 · minSdk 23 · targetSdk 36

## 本版更新

### 全景视角与转屏

- 360° 视频的「前进视角」可实时跟随行进方向。播放器先补偿相机自身的旋转，再从多个纬度区域的光流估算运动扩张中心（FOE），减少摇摄时的误转向。
- 打开全景视频时读取 V1、V2 或 EBML 元数据中的片源朝向。播放器分别记住手动选择的普通／全景模式和立体布局。
- 普通全景和 VR 分屏都按每只眼睛可见区域的长边计算视场角（FOV）。转屏时按新窗口尺寸重绘当前帧，暂停画面也能保持比例。

### 画面与播放控制

- SDR 画面按需渲染，帧时间戳不可用时使用备用计时。修正带旋转标记的竖屏视频在 FSR1、Anime4K 超分和插帧时的画面方向。
- 播放结束时先将进度更新到片尾。重播时先跳回片头，待跳转完成后再开始播放。
- Android 13 及以上的底部导航栏和迷你播放栏使用 Kyant AGSL 液态玻璃折射。Android 12 系列使用实时模糊，更早系统使用实色底栏。

### B 站与系统集成

- B 站 DASH 按轨道隔离解析失败，保留其余可用轨道。CDN 地址支持非 443 端口。修复官方登录 WebView 的输入法交互，以及 Android Keystore 密钥失效后的恢复流程。
- 修复文件访问框架（SAF）授权、SQLite 预写日志（WAL）、系统画中画（PiP）和字幕处理中的 P0 至 P2 问题。

## 验证范围

- `assembleDebug` 和启用 R8 的 `assembleRelease` 均通过。`lintDebug` 报告 0 errors / 61 warnings。
- JVM 单元测试通过 64/64 项。在 Android 17 模拟器 `PanoVivid_API37_2` 上，`connectedDebugAndroidTest` 通过 36/36 项。
- 模拟器冷启动至截图耗时 639 ms，本次记录中 GL、AGSL 和应用错误均为 0。
- 当前测试环境中，未登录时尝试 B 站实际在线播放返回 HTTP 412。需先通过官方 WebView 或扫码登录，再验证实际播放。
- HDR 显示、杜比视界、陀螺仪跟随和功耗仍待真机验证。

## 下载与安装

最低支持 Android 6.0（API 23）。本地交付目录为 `dist/`。

| 安装包 | 安装方式 | SHA-256 |
| --- | --- | --- |
| `PanoVivid-Android-1.0.7-android.8-preview.apk` | 使用 debug 签名，可直接安装预览。 | `f6d553c3468a8d19be555eb57330529bb162518b467732b0ba0d4e8c61169e98` |
| `PanoVivid-Android-1.0.7-android.8-unsigned.apk` | 启用 R8 的未签名 release 包，安装前需签名。 | `cb3a05a3f5a734503f64ea36beaee95a00cc2fb01bc959a4f41f321d98ee1371` |
