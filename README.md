# Force Pinyin CN - 微软拼音强制中文工具

[English](./README_en.md)

微软拼音存在一个烦人的问题，输入法可能意外地自动进入英文模式。导致用户可能要经历“输入错误-确认输入法-确认中英文模式-最终进入中文模式”的繁琐过程。

所以有了这个小工具，专门针对Microsoft Pinyin输入法优化。

## 功能特性

- 检测到Microsoft Pinyin英文模式时自动切换到中文模式
- 检测到用户主动按Shift切换时，0.5秒内不执行自动切换

## 使用方法

### 方式一：使用编译好的可执行文件

直接运行 `force_pinyin_cn.exe`:

```bash
# 持续监控模式
./force_pinyin_cn.exe

# 单次检查模式
./force_pinyin_cn.exe --test
```

### 方式二：使用Python源码

```bash
# 持续监控模式
python force_pinyin_cn.py

# 单次检查模式  
python force_pinyin_cn.py --test
```

### 退出
暂时没有实现托盘tray功能，退出请在任务管理器中结束进程

## 运行说明

### 持续监控模式
- 程序会持续监控输入法状态和Shift键按下事件
- 当检测到Microsoft Pinyin处于英文模式时，自动切换到中文模式
- 智能识别用户主动按Shift切换：如果0.5秒内检测到Shift按下，将跳过自动切换
- 实时显示当前输入法状态和活动窗口信息
- 按 `Ctrl+C` 退出程序

### 单次检查模式
- 执行一次输入法状态检查
- 显示详细的输入法信息
- 如果检测到需要切换，会尝试执行切换操作

## 输出示例

```
开始监控输入法状态... 按 Ctrl+C 退出。
自动切换功能已启用：检测到Microsoft Pinyin英文模式时将自动切换到中文模式
智能防护功能已启用：如果在0.5秒内检测到Shift键按下，将跳过自动切换
------------------------------------------------------------
[14:30:20] 输入模式: 中文 (Microsoft Pinyin) | 标点状态: 中文标点 | 语言ID: 0x804
           窗口: Visual Studio Code
🔄 检测到Shift键按下 [14:30:22]
[14:30:22] 输入模式: 英文 (Microsoft Pinyin) | 标点状态: 英文标点 | 语言ID: 0x804
           窗口: Visual Studio Code
⏸️  检测到用户在 0.3秒前按下Shift键，跳过自动切换
[14:30:25] 输入模式: 英文 (Microsoft Pinyin) | 标点状态: 英文标点 | 语言ID: 0x804
           窗口: Visual Studio Code
✅ 已切换到中文模式
[14:30:25] 输入模式: 中文 (Microsoft Pinyin) | 标点状态: 中文标点 | 语言ID: 0x804
           窗口: Visual Studio Code
```

## 系统要求

- Windows 10/11
- Microsoft Pinyin 输入法
- Python 3.6+ (如果运行源码)

## 开发构建

如需重新编译可执行文件，使用以下命令：

```bash
python -m nuitka --onefile --windows-console-mode=disable --noinclude-dlls=libcrypto-3.dll --windows-icon-from-ico=.\icon.ico force_pinyin_cn.py
```

## 引用感谢

本项目的输入法状态检测实现参考了 [ImTip](https://github.com/aardio/ImTip/) 项目的相关技术方案。

**ImTip** 是一个优秀的智能桌面助手，提供输入跟踪提示、超级热键和AI助手功能，仅832KB体积却功能强大。感谢aardio团队在输入法状态检测方面的技术贡献，为本项目提供了宝贵的参考。

- 🔗 **ImTip项目地址**: https://github.com/aardio/ImTip/
- 📖 **官方网站**: https://imtip.aardio.com/
- ⭐ **Stars**: 2.2k+ (MIT License)

---

本工具旨在提高中文输入的便利性，减少手动切换输入法的麻烦。
