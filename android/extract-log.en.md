# Extracting Android device log

### 1. On your phone, Setting -> About device -> Software info -> touch 10 times on 'Build number' (this operation will turn debug mode on)

### 2. On your phone, Setting -> Developer options -> Turn `USB debug` on

### 3. Connect your PC and Phone using USB cable. If your phone want to confirm about some permission, please allow it.

### 4. Download ADB(Android Debug Bridge) in [official Android website][official_android_website]
- You can also use below direct download link:
- For Windows: https://dl.google.com/android/repository/platform-tools-latest-windows.zip
- For MAC: https://dl.google.com/android/repository/platform-tools-latest-darwin.zip
- For Linux: https://dl.google.com/android/repository/platform-tools-latest-linux.zip

### 5. On your PC, Decompress a downloaded zip file into `c:\adb` directory. You can use another directory name. There may be subdirectories where adb.exe is located, we call that directory `working directory`

### 6. On your PC, From `Computer` icon move to the working directory where the adb.exe file is located. (maybe `c:\adb\platform-tools`). `<shift + mouse right button>` to open context menu, then select 'Open command window here'

### 7. On command window, run below commands line by line to verify your phone is properly connected.
```
adb version
adb devices
```

- If it works well, you will see the result like that below:

```
C:\adb\device_log>adb version
Android Debug Bridge version 1.0.31

C:\adb\device_log>adb devices
List of devices attached
FAXXXXXXXX18    device
```

- If the connection is not good, you may need to install adb drivder. Use [Universal Adb Driver][universal_adb_driver] for Windows user 

### 8. On command window, run below to extract platform information into `prop.txt` file

```
adb shell getprop > prop.txt
```

### 9. On command window, delete previous logs and start to extract logs into `log1.txt` file

```
adb logcat -c
adb logcat -v time > log1.txt
```

### 10. Right after executing the last command in no.9, On your phone, reproduce your error part. When done, back to the command window, use `<ctrl+c>` to exit from log extracting.

### 11. send `log1.txt` and `prop.txt` files to the person in charge.

> If you want to extract log multiple time, repeat no.9~no.10 using another file name like `log2.txt`


[official_android_website]: https://developer.android.com/studio/releases/platform-tools.html
[universal_adb_driver]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/universaladbdriver_v4.0.zip
