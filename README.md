# PCL-fix

这是 IMAX9D 基于 [Meloong-Git/PCL](https://github.com/Meloong-Git/PCL) 独立维护的第三方修改版，与 PCL 官方无隶属关系。
基于官方 **2.99.0.0**（`6b9a50d`），保留完整 Git 历史、原作者署名和 [上游许可与使用指南](LICENCE)。

## 修复内容

- 将 `Modules/ModSecret.vb` 的编译时常量 `RestrictMcDownload` 设为 `False`，恢复原有 Minecraft 版本列表、下载安装、整合包安装及版本修改入口。
- 分支标识改为 `PCL-fix`，关于页面标明第三方修改版，保留龙腾猫跃的首位署名与赞助入口。
- 不修改账号验证、正版购买劝导或游戏授权逻辑。

这项修复需要重新编译，不能通过 `Setup.ini` 生效。下载与安装逻辑沿用上游实现。

## 构建

可在本仓库的 **Actions → Build** 运行构建并下载产物；也可使用 Visual Studio 的 .NET 桌面开发工具、.NET Framework 4.8 目标包和 .NET SDK：

```powershell
git clone --recurse-submodules https://github.com/IMAX9D/PCL-fix.git
cd PCL-fix
dotnet restore PCLCS/PCLCS.csproj
msbuild "Plain Craft Launcher 2/Plain Craft Launcher 2.vbproj" -p:Configuration=Release
```

上游公开源码通过 `PCL_MS_CLIENT_ID`、`PCL_CURSEFORGE_API_KEY` 环境变量读取微软登录与 CurseForge 所需的配置；本仓库不包含这些凭据。GitHub Actions 沿用上游的 `CLIENT_ID`、`CURSEFORGE_API_KEY` 仓库机密配置方式。
公开源码版本的账号与设置存储沿用上游 `PCLDebug` 隔离规则，与官方发行版不完全相同。

---

以下为上游项目说明。

# Plain Craft Launcher

[![Stars](https://img.shields.io/github/stars/Meloong-Git/PCL?style=flat&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEiIHdpZHRoPSIxNiIgaGVpZ2h0PSIxNiI+PHBhdGggZD0iTTggLjI1YS43NS43NSAwIDAgMSAuNjczLjQxOGwxLjg4MiAzLjgxNSA0LjIxLjYxMmEuNzUuNzUgMCAwIDEgLjQxNiAxLjI3OWwtMy4wNDYgMi45Ny43MTkgNC4xOTJhLjc1MS43NTEgMCAwIDEtMS4wODguNzkxTDggMTIuMzQ3bC0zLjc2NiAxLjk4YS43NS43NSAwIDAgMS0xLjA4OC0uNzlsLjcyLTQuMTk0TC44MTggNi4zNzRhLjc1Ljc1IDAgMCAxIC40MTYtMS4yOGw0LjIxLS42MTFMNy4zMjcuNjY4QS43NS43NSAwIDAgMSA4IC4yNVoiIGZpbGw9IiNlYWM1NGYiLz48L3N2Zz4=&logoSize=auto&label=Stars&labelColor=444444&color=eac54f)](https://github.com/Meloong-Git/PCL/)
[![Issues](https://img.shields.io/github/issues/Meloong-Git/PCL?style=flat&label=Issues&labelColor=444444&color=1F883D)](https://github.com/Meloong-Git/PCL/issues)
[![哔哩哔哩](https://img.shields.io/badge/动态-BiliBili-00A4DB?style=flat&labelColor=444444&logoSize=auto)](https://space.bilibili.com/11343203/dynamic)
[![爱发电](https://img.shields.io/badge/赞助-爱发电-946ce6?style=flat&labelColor=444444&logoSize=auto)](https://meloong.com/afd/a/LTCat)

包含 PCL 的大部分源代码，包括 UI 库、动画模块、下载模块、Minecraft 启动模块等！<br/>
代码并不是实时更新的，它会在每次 PCL 发布更新时同步一次。<br/>
非常感谢社区的大力支持！

<br/>

### 相关资源
- [PCL 下载](https://meloong.com/pcl)：下载可免费使用的正式版 PCL！
- [PCL 功能投票](https://github.com/Meloong-Git/PCL/discussions/2)：来参加投票吧，开发者会优先处理票数较高的项目！
- [帮助文档库](https://github.com/LTCatt/PCL2Help)：PCL 内置帮助文档的存储库
