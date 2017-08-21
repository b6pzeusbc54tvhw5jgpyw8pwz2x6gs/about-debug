# Android 단말 로그 추출하기 for Windows 사용자

### 1. Phone 에서, 설정 -> 디바이스 정보 -> 소프트웨어 정보 -> 빌드번호를 10번정도 연속하여 터치(이동작은 디버그 모드를 활성화시킴)

### 2. Phone 에서, 설정 -> 개발자 옵션 -> USB 디버깅 on 으로 변경

### 3. PC 와 Phone 을 USB 케이블로 연결, 이후에 Phone 에서 권한관련 팝업이 나오면 '허용' 선택.

### 4.1. PC 에서, [platform-tools-for-windows.zip][platform_tools] 파일을 다운로드 후 압축해제.

### 4.2. `내 컴퓨터`를 통해 `adb.exe` 파일이 위치한 `platform-tools` 디렉토리까지 이동.

### 4.3. PC와 Phone 의 연결을 확인하기 위해 `platform-tools` 디렉토리에 있는 `check-connection.bat` 파일을 실행.

- 연결까지 잘 되었을 경우 아래처럼 `List of devices attached` 밑에 숫자와 영문으로된 `deivce ID` 가 나와야함:

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

- 확인 후 아무키나 눌러 창을 닫음.
- 연결이 잘 되지 않았을 경우, adb 드라이버를 설치해야함. [Universal Adb Driver][universal_adb_driver] 를 사용하자.
- 연결이 잘 되었을 경우 5번으로 넘어가고, 아니면 계속 `check-connection.bat` 파일을 실행하여 연결을 확인해야함.

### 5. Phone 에서, 문제 되었던 현상 재현 하기.

### 6.1. PC 에서, `platform-tools` 디렉토리에 있는 `extract-device-log.bat` 파일을 실행하여 로그 추출.

### 6.2. `platform-tools` 디렉토리에 `log-시간_분_초.txt` 파일이 생성되었을 것이다. 이 파일을 담당자에게 전달.

[official_android_website]: https://developer.android.com/studio/releases/platform-tools.html
[universal_adb_driver]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/universaladbdriver_v4.0.zip
[platform_tools]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/platform-tools-for-windows.zip
