# AirCard-iOS 简体中文版

本分支基于 [Mak5er/AirCard-iOS](https://github.com/Mak5er/AirCard-iOS) 的 `main` 分支，加入简体中文界面与 GitHub Actions IPA 构建流程。原项目采用 MIT 许可证；版权与致谢信息保留在 [LICENSE](LICENSE) 和 [README.md](README.md)。

## 兼容性

请以原项目的 [兼容性说明](README.md#compatibility) 为准。当前源码声明支持 iOS 18.0 至 iOS 27.2 beta 2；iOS 27.2 beta 3 及更新版本的相关功能已被修补。运行时仍需原项目要求的配对文件及 LocalDevVPN 环回连接。

## 编译与发布

- 推送到 `main`，或在 GitHub Actions 页面手动运行“编译并发布 IPA”，会生成可下载的构建产物。
- 推送以 `v` 开头的标签（例如 `v1.3.2-zh.1`），工作流还会创建 GitHub Release 并附上 `AirCard-iOS.ipa`。
- IPA **未签名**。安装前需使用 SideStore、AltStore 等方式签名；该产物无法直接作为已签名安装包使用。
- 工作流使用 GitHub 托管的 macOS 运行器和仓库自带的 `AirliftFFI.xcframework`。修改 `rust-core` 后，须先在适用的 macOS/Xcode 环境运行 `./build-ios.sh` 并提交重建的框架，否则 IPA 仍会链接旧版 Rust 库。

本地构建：在 macOS 上安装 Xcode，运行 `./build-ipa.sh Release`；输出在 `build/AirCard-iOS.ipa`。

## 汉化范围

主要页面、引导、设置、常见错误与结果提示，以及系统权限用途说明已加入简体中文。内部调试日志、部分来自系统或 Rust 核心的错误文本可能仍显示英文。
