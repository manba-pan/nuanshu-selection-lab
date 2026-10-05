# 暖树 Selection Lab

<img src="assets/icon.png" alt="Selection Lab" width="96" />

在 Photoshop 当前选中图层上进行人物、身体部位、裸露皮肤与衣物颜色选区。作者：**暖树**。

**独立测试版 · 核心源码暂不公开 · 不属于 Dreamer 正式插件。** 本仓库只提供原版安装程序、校验文件、使用说明与更新记录。

## 下载与更新

**[下载最新安装包](https://github.com/manba-pan/nuanshu-selection-lab/releases/latest)**

下载 `SelectionLab-0.3.0-Windows-x64-Setup.exe`，同时保留对应的 SHA-256 文件。未来版本继续从上面的固定地址下载，不需要查找新的仓库。

```powershell
Get-FileHash .\SelectionLab-0.3.0-Windows-x64-Setup.exe -Algorithm SHA256
```

将结果与同一 Release 中的 SHA-256 校验文件对照。本版未做商业代码签名，Windows 可能显示未知发布者或 SmartScreen 提示；请先确认来自本仓库并核对文件，**不要关闭杀毒软件或系统防护**。

## 安装

1. 保存正在编辑的 Photoshop 文档，运行安装程序，按提示选择 Photoshop 安装目录。写入受保护目录时，安装程序会请求一次正常的 Windows 管理员权限。
2. 安装器准备程序、独立 PS 面板、快捷方式与所需的 Microsoft VC++ 运行库。无需安装 Python、Anaconda 或开发工具。
3. 新安装的面板需要 Photoshop 重新启动后扫描；安装程序不会强制结束或重启 Photoshop。
4. 双击 **Selection Lab 选区实验室**，或从 **增效工具 → Selection Lab 选区实验室** 打开。
5. 阅读启动须知。首次点击下载并校验模型，完整模型约 **9.24 GB**，支持中断后重试续传。模型下载需要能访问公开的 Hugging Face 模型源；网络不可用时会提示，不会伪装已就绪。

建议 Windows 10/11 x64、Photoshop 2026，至少预留25GB磁盘；建议32GB以上内存，1B高精模式建议更充裕内存。本次在48GB内存、AMD RX9070XT、Photoshop27.7环境验证。其他硬件/PS版本仍需实际测试，不能承诺全部兼容。

## 使用

- 在 PS 选中**单个图层**，点击“读取当前图层”。多层/图层组会明确拒绝，不会静默读取合成图。
- 选择主体、部位、裸肤或指定颜色；默认1B + SAM精度优先，首次处理可能需要一至数分钟。
- 放大检查后，可框选局部目标，加保留点/排除点进行智能精修；也保留普通补选/减选画笔。
- 点击“写回原文档选区”。程序核对文档、图层、尺寸、历史状态，保留图层偏移和透明度；不会自动保存或覆盖原文件。
- 修改图层、切换文档后重新读取，保留原PSD副本。AI可能漏选或误选，结果始终需要人工复核。

更新安装前可从开始菜单选择“停止 Selection Lab 后台”；这只停止本工具的计算/下载，不关闭 Photoshop。安装器会处理本安装目录的后台，异路径旧开发服务需要先退出。

## 本地文件与隐私

当前推理在本机进行，照片不自动上传云端AI。模型下载和手动打开 GitHub 会产生普通网络连接。

图像副本、蒙版、设置及日志默认保留在：

```text
%LOCALAPPDATA%\NuanShu\SelectionLab
```

关闭面板不会清理这些副本。卸载默认保留本地数据和模型；敏感照片使用后请退出程序并自行管理输出目录。反馈问题时不要把隐私原图或包含个人信息的日志直接发到公开 Issues。

## 闭源与第三方组件

本版将核心程序编译为原生EXE，界面资源采用认证加密，PS宿主桥接做混淆；**这些措施增加提取和逆向成本，不保证无法逆向**。应用源码暂不公开；第三方模型、运行库分别适用其原始许可证，不能视为作者独占资产。

使用 Sapiens2、GroundingDINO、SAM2.1、BiRefNet，完整许可证随应用提供，也可在启动须知中阅读。本软件不对所有照片承诺逐像素正确；它是一个可审查、可修正的辅助选区工具。

[更新记录](CHANGELOG.md) · [使用与版权说明](LICENSE.txt) · [反馈问题](https://github.com/manba-pan/nuanshu-selection-lab/issues)
