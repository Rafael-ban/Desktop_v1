<div align="center">

# DiskNext Desktop

[![License](https://img.shields.io/badge/license-GPL%20v3-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Version](https://img.shields.io/badge/version-0.2.4-green.svg)](UPDATE.md)

**原名 HFR-Cloud Desktop 或 Cloudreve Desktop**

一个基于 Tkinter 的跨平台 HFR-Cloud/DiskNext/Cloudreve v3 桌面客户端  
兼容 Cloudreve V3，并使用 ttkBootstrap 库进行美化

---

⚠️ **重要提示：V1 已被归档，重构版的 V2 正在编写中……**

[查看更新日志](UPDATE.md) | [问题反馈](https://github.com/Rafael-ban/Desktop_v1/issues) | [贡献指南](#贡献指南)

</div>

---

## 📢 重要通知

- ⚠️ **请勿连接 Cloudreve 官方演示站** `https://demo.cloudreve.org`，会出现 JSON 读取错误（被 WAF 拦截），目前正在分析解决方案
- 💾 **数据迁移计划**：我们已经准备好向 sqlite3 数据库迁移，请保存好相关数据
- 📁 **数据存储位置**：为了保证单文件程序正常可用，后期版本将使用 `%appdata%/HeyFun/HFR-Cloud Desktop Community/` 文件夹来保存数据

---

## ✨ 目前已实现的功能

- ✅ 登录 & 注销
- ✅ 登录记录持久化
- ✅ 文件夹浏览
- ⚠️ 文件搜索（功能暂不可用，正在修复）
- ✅ 新建文件 / 文件夹
- ✅ 删除文件 / 文件夹
- ✅ 文件分类浏览
- ✅ 文件预览 / 下载
- ✅ 文件传输列表
- ✅ WebDAV 列表
- ✅ 新建 WebDAV 账户
- ✅ iOS 版 Cloudreve 扫码
- ✅ 本地策略文件上传
- ✅ OneDrive 存储策略上传

---

## 🐛 已知问题

### Bug
- 文件列表选中后，将无法再触发未选择时的右键菜单  
  **解决办法**：地址栏回车刷新

### 功能限制
- 部分功能只做了 UI，并未实现对应功能
- 显示比例在 100%-125% 体验为佳（未适配高分屏）
- 无法登录需要 Google 或腾讯验证码的服务端
- 账号（不包括密码）与 Cookies 为明文保存

---

## 🔧 兼容性

### 支持的服务端版本
| 服务端 | 版本 | 说明 |
|--------|------|------|
| HFR-Cloud | V0.0.x | - |
| Cloudreve | V3 | 推荐：**3.8.4 Pro**（本项目基于此版本开发，使用早期版本可能出现问题） |

### 系统要求
- **操作系统**：Windows / macOS / Linux
- **Python 版本**：3.8+
- **推荐字体**：思源黑体（可选）

---

## 程序配置设置
需要在程序根目录新建文件`config.ini`。示例内容如下，真正填写时请去掉分号以及分号后的内容：
```
[account]
url = http://localhost:5212         ;这里填写服务端的地址，若为ip访问，HFR-Cloud默认使用7030端口，Cloudreve默认使用5212端口；填写你需要接入的地址，结尾不需要加“/”
username = admin@yuxiaoqiu.cn       ;(可不填)邮箱，自动登录失败时会自动将此邮箱填入输入框
id = AqbS                           ;(可不填)用户ID
nickname = Cloudreve                ;(可不填)用户名
groupname = Admin                   ;(可不填)头衔（在Cloudreve被称为用户组名称）
allowshare = True                   ;(可不填)是否允许分享
allowremotedownload = True          ;(可不填)是否允许多线程下载
allowarchivedownload = True         ;(可不填)是否允许打包下载
advancedelete = True                ;(可不填)是否允许高级删除
allowwebdavproxy = False            ;(可不填)是否允许webdav代理

[settings]
Server = Hfrcloud                   ;服务器采用的是HFR-Cloud就填写Hfrcloud，否则请填写Cloudreve_V3
theme = light                       ;(可不填)程序主题，可自行填写light或者dark
fonts = 思源黑体                     ;(可不填)程序字体，推荐思源黑体，留空会检测系统是否安装思源黑体，有则使用无则宋体(Windows)或者苹方(macOS)
```

> **注意**：本地调试时无需新建 `config.ini`，程序会自动请求 `http://localhost:5212`

---

## 📦 安装使用

### 1. 安装依赖

```bash
pip install -r requirements.txt
```

**依赖包列表：**
- Pillow==10.3.0
- pyotp==2.9.0
- pyperclip==1.8.2
- qrcode==7.4.2
- Requests==2.32.0
- ttkbootstrap==1.10.1

### 2. 安装字体（可选，推荐）

下载并安装思源黑体：  
[SourceHanSansSC.zip](https://github.com/adobe-fonts/source-han-sans/releases/download/2.004R/SourceHanSansSC.zip)

### 3. 启动程序

```bash
python GUI_Launcher.py
```

---

## 📦 打包成可执行文件

### ⚠️ 重要提示
**打包前请务必删除以下敏感信息，否则您的个人信息将会被打包！**
- 删除 `Cookies.txt` 文件
- 删除 `config.ini` 中的 `[account]` 字段

### 打包步骤

1. 安装 PyInstaller
   ```bash
   pip install pyinstaller
   ```

2. 执行打包命令
   ```bash
   pyinstaller build.spec
   ```

3. 可执行文件将生成在 `/dist` 目录中

---

## 💎 升级到捐助版

开始着手这个项目时，我学 Python 并没有多久，现在回过头来看这个项目已经让我看不上了。所以我对这个代码进行了重构，新的程序拥有着更现代化的界面以及更完善的功能更新，它的名字叫做 **DiskNext Desktop**。

当然，持续为爱发电的项目注定活不长久，我希望能依靠这个产品来补充一下自己不多的生活费，让我更有动力来维护这个项目。

### 价格说明
- **订阅模式**：即将推出
- **买断模式**：即将推出
- **站长预售**：199元/根域名永久授权（正式版推出后价格翻倍）
- **联系方式**：微信 `yuxiaoqiu2333`

---

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request 来帮助改进项目！

### 如何贡献
1. Fork 本仓库
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

### 代码规范
- 遵循 Python PEP 8 编码规范
- 添加必要的注释
- 确保代码可读性

---

## 📄 开源许可

本项目采用 **GPL v3** 开源许可证。

本来我并不想开源这个项目的（因为之前我的项目开源之后被别人申请著作权以后返回来告我抄袭，加之这个项目也是自己很久做出来的心血），现在想通了，所以采用 GPL v3 进行开源。

---

## ❤️ 赞助支持

如果这个项目对您有帮助，欢迎：
- ⭐ Star 本项目
- 💰 赞助支持（感谢您的投喂！）
- 🐛 提交 Bug 报告
- 💡 提出新功能建议

---

## 👨‍💻 作者

**于小丘**
- Email: admin@yuxiaoqiu.cn
- 微信: yuxiaoqiu2333

**Debug 支持**
- 暗之旅者

---

<div align="center">

**感谢您的 Star！⭐**

Made with ❤️ by 于小丘

</div>
