# Force Pinyin CN - Microsoft Pinyin Chinese Mode Enforcer

[中文](./README_cn.md)

Microsoft Pinyin has an annoying issue where the input method may unexpectedly switch to English mode automatically. This forces users through the tedious process of "typing incorrectly - checking input method - confirming Chinese/English mode - finally entering Chinese mode".

This small tool was created to address this issue, specifically optimized for Microsoft Pinyin input method.

## Features

- 🎯 **Auto Switch**: Automatically switches to Chinese mode when Microsoft Pinyin English mode is detected
- 📊 **Real-time Monitoring**: Real-time display of input method status, including language mode, punctuation status, etc.
- 🧠 **Smart Protection**: When user actively presses Shift to switch, auto-switching is disabled for 0.5 seconds

## Usage

### Method 1: Using Compiled Executable

Run `force_pinyin_cn.exe` directly:

```bash
# Continuous monitoring mode
./force_pinyin_cn.exe

# Single check mode
./force_pinyin_cn.exe --test
```

### Method 2: Using Python Source Code

```bash
# Continuous monitoring mode
python force_pinyin_cn.py

# Single check mode  
python force_pinyin_cn.py --test
```

### Exit
No tray functionality implemented. To exit, please terminate the process in Task Manager.

## Operation Instructions

### Continuous Monitoring Mode
- The program continuously monitors input method status and Shift key press events
- When Microsoft Pinyin English mode is detected, it automatically switches to Chinese mode
- Smart recognition of user-initiated Shift switching: if Shift press is detected within 0.5 seconds, auto-switching is skipped
- Real-time display of current input method status and active window information
- Press `Ctrl+C` to exit the program

### Single Check Mode
- Performs a one-time input method status check
- Displays detailed input method information
- If switching is needed, attempts to execute the switch operation

## Output Example

```
Starting input method status monitoring... Press Ctrl+C to exit.
Auto-switch function enabled: Will automatically switch to Chinese mode when Microsoft Pinyin English mode is detected
Smart protection function enabled: If Shift key press is detected within 0.5 seconds, auto-switching will be skipped
------------------------------------------------------------
[14:30:20] Input Mode: Chinese (Microsoft Pinyin) | Punctuation: Chinese punctuation | Language ID: 0x804
           Window: Visual Studio Code
🔄 Shift key press detected [14:30:22]
[14:30:22] Input Mode: English (Microsoft Pinyin) | Punctuation: English punctuation | Language ID: 0x804
           Window: Visual Studio Code
⏸️  User pressed Shift 0.3 seconds ago, skipping auto-switch
[14:30:25] Input Mode: English (Microsoft Pinyin) | Punctuation: English punctuation | Language ID: 0x804
           Window: Visual Studio Code
✅ Switched to Chinese mode
[14:30:25] Input Mode: Chinese (Microsoft Pinyin) | Punctuation: Chinese punctuation | Language ID: 0x804
           Window: Visual Studio Code
```

## System Requirements

- Windows 10/11
- Microsoft Pinyin Input Method
- Python 3.6+ (if running from source code)

## Development Build

To recompile the executable file, use the following command:

```bash
python -m nuitka --onefile --windows-console-mode=disable --noinclude-dlls=libcrypto-3.dll --windows-icon-from-ico=.\icon.ico force_pinyin_cn.py
```

## Notes

- This tool only works on Windows systems
- Requires Microsoft Pinyin input method support
- The program needs permissions to read system input method status and keyboard key status
- The program automatically detects if an instance is already running at startup, and exits if one exists
- Smart protection function identifies user-initiated switching behavior by monitoring Shift key

## Troubleshooting

If the program doesn't work properly, please check:
1. Whether Microsoft Pinyin input method is installed
2. Whether the input method is working properly

## Acknowledgments

The input method status detection implementation in this project references technical solutions from the [ImTip](https://github.com/aardio/ImTip/) project.

**ImTip** is an excellent smart desktop assistant that provides input tracking tips, super hotkeys, and AI assistant features, all in just 832KB. We thank the aardio team for their technical contributions in input method status detection, which provided valuable reference for this project.

- 🔗 **ImTip Project**: https://github.com/aardio/ImTip/
- 📖 **Official Website**: https://imtip.aardio.com/
- ⭐ **Stars**: 2.2k+ (MIT License)

---

This tool aims to improve the convenience of Chinese input and reduce the hassle of manually switching input methods. 