# Extracting Android device log for Windows User

### 1. On your phone, Setting -> About device -> Software info -> touch 10 times on 'Build number' (this operation will turn debug mode on)

### 2. On your phone, Setting -> Developer options -> Turn `USB debug` on

### 3. Connect your PC and Phone using USB cable. If your phone want to confirm about some permission, please allow it.

### 4.1. On your PC, Download [platform-tools-for-windows.zip][platform_tools] file and decompress it.

### 4.2. Use `Computer(File explorer)` to move into the `platform-tools` directory where the `adb.exe` file is located.

### 4.3. To verify your phone is properly connected, execute the `check-connection.bat` file in `platform-tools` directory.

- If it works well, you will see the `device ID` under the `List of devices attached` as follow:

```
C:\platform-tools>adb version
Android Debug Bridge version 1.0.39
Revision 3db08f2c6889-android
Installed as C:\platform-tools\adb.exe

C:\platform-tools>adb devices
List of devices attached
05157dxxxxx8d727        device

C:\platform-tools>SET /P P=Press any key continue:
Press any key continue:
```

- Press any key to close the window.
- If the connection is not good, you may need to install adb drivder. Use [Universal Adb Driver][universal_adb_driver].
- If the connection is well, you can go over to No.5, or you should check connection again using `check-connection.bat` file.

### 5. On your phone, reproduce your error part.

### 6.1. On your PC, To extract log execute `extract-device-log.bat` file in `platform-tools` directory.

### 6.2. In the `platform-tools` directory, `log-hour_min_sec.txt` file would have been created. Send it to the person in charge.

[official_android_website]: https://developer.android.com/studio/releases/platform-tools.html
[universal_adb_driver]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/universaladbdriver_v4.0.zip
[platform_tools]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/platform-tools-for-windows.zip
