# Extracting Android device log

### 1. On your phone, Setting -> About device -> Software info -> touch 10 times on 'Build number' (this operation will turn debug mode on)

### 2. On your phone, Setting -> Developer options -> Turn `USB debug` on

### 3. Connect your PC and Phone using USB cable. If your phone want to confirm about some permission, please allow it.

### 4. Download ADB(Android Debug Bridge) in [official Android website][official_android_website]
- You can also use below direct download link:
- For Windows: https://dl.google.com/android/repository/platform-tools-latest-windows.zip
- For MAC: https://dl.google.com/android/repository/platform-tools-latest-darwin.zip
- For Linux: https://dl.google.com/android/repository/platform-tools-latest-linux.zip

### 5.1. On your PC, Decompress a downloaded zip file and decompress it. Use `Computer(File explorer)` to move into the `platform-tools` directory where the `adb.exe` file is located.

### 5.2. Use `<shift + mouse right button>` to open context menu, then select 'Open command window here'

### 6. On command window, Execute following commands line by line to verify your phone is properly connected.
```
adb version
adb devices
```

- If it works well, you will see the result like that below:

```
C:\platform-tools> adb version
Android Debug Bridge version 1.0.31

C:\platform-tools> adb devices
List of devices attached
FAXXXXXXXX18    device
```

- If the connection is not good, you may need to install adb drivder. Use [Universal Adb Driver][universal_adb_driver] for Windows user 

### 7. On your phone, reproduce your error part.

### 8. On command window, To extract logs, execute the following commands line by line immediately after No.8.
```
C:\platform-tools> adb logcat -d -v time > log1.txt
C:\platform-tools> adb shell getprop > prop.txt
```

### 9. `log1.txt` and `prop.txt` files would have been created in `platform-tools` directory. Send it to the person in charge.

> If you want to extract log multiple time, repeat no.7~no.8 using another file name like `log2.txt`


[official_android_website]: https://developer.android.com/studio/releases/platform-tools.html
[universal_adb_driver]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/universaladbdriver_v4.0.zip
