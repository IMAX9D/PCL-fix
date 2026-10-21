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

微软登录默认使用官方 PCL 2.99.0.0 的公开 OAuth Client ID。Client ID 是公开应用标识，不是客户端密钥或用户令牌；克隆本仓库后直接构建即可包含该默认配置，无需另外填写。维护者可用 `PCL_MS_CLIENT_ID` 运行时环境变量，或 GitHub Actions 的 `CLIENT_ID` 仓库配置覆盖它。该应用仍由原维护者控制，其后续变更可能影响登录。

已用默认 Client ID 请求微软设备码接口，接口成功签发登录码；这只验证登录流程第一步，未验证用户完成授权后的 Xbox、Minecraft 服务访问和游戏启动。

CurseForge API Key 不属于公开应用标识，本仓库不包含它。需要使用 CurseForge 时，维护者须自行配置 `PCL_CURSEFORGE_API_KEY` 环境变量或 GitHub Actions 的 `CURSEFORGE_API_KEY` 仓库机密。此限制与微软登录无关。
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
