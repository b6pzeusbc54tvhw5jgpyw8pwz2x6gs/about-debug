# Android 단말 로그 추출 (한국어)

### 1. Phone 에서, 설정 -> 디바이스 정보 -> 소프트웨어 정보 -> 빌드번호를 10번정도 연속하여 터치(이동작은 디버그 모드를 활성화시킴)

### 2. Phone 에서, 설정 -> 개발자 옵션 -> USB 디버깅 on 으로 변경

### 3. PC 와 Phone 을 USB 케이블로 연결, Phone 에서 권한관련 팝업이 나오면 '허용' 해줌

### 4. [안드로이드 공식 웹사이트][official_android_website]에서 ADB(Android Debug Bridge) 다운로드
- 아래의 다운로드 링크를 바로 사용 할 수 있음:
- For Windows: https://dl.google.com/android/repository/platform-tools-latest-windows.zip
- For MAC: https://dl.google.com/android/repository/platform-tools-latest-darwin.zip
- For Linux: https://dl.google.com/android/repository/platform-tools-latest-linux.zip

### 5. PC 에서, 다운로드받은 zip 파일을 `c:\adb` 폴더에 압축해제. 다른 이름을 사용해도 된다. `adb.exe` 파일이 있는 하위 디렉토리가 있는데 이 디렉토리를 `워킹 디렉토리`라 부르자

### 6. PC 에서, `adb.exe` 파일이 위치한 `워킹 디렉토리`까지 `내 컴퓨터`를 통해 이동한다. `<shift+mouse 우측버튼>` 으로 컨텍스트 메뉴를 열고 '여기서 명령창 열기' 실행

### 7. 명령창에서, 다음의 명령어들을 한줄씩 실행하여 Phone 연결을 확인
```
adb version
adb devices
```

- 연결까지 잘 되었을 경우 아래와 같은 결과가 나옴

```
C:\adb\device_log>adb version
Android Debug Bridge version 1.0.31

C:\adb\device_log>adb devices
List of devices attached
FAXXXXXXXX18    device
```

- 연결이 잘 되지 않을 경우, adb 드라이버를 설치해야함. [Universal Adb Driver][universal_adb_driver] 를 사용하자.

### 8. 명령창에서, 플랫폼의 정보를 `prop.txt` 파일로 추출하기 위해 아래 명령어 수행

```
adb shell getprop > prop.txt
```

### 9. 명령창에서, 기존에 쌓여있던 단말로그 삭제 후 `log1.txt` 파일로 로그 추출을 시작하기위해 아래 명령어들 한줄씩 실행

```
adb logcat -c
adb logcat -v time > log1.txt
```

### 10. 9번의 마지막 명령 실행 후 바로 Phone 에서, 문제 되었던 현상을 다시 시도. 재현이 끝나면 다시 명령창으로 돌아와 로그 추출을 종료하기 위해 `<ctrl+c>`

### 11. `log1.txt`, `prop.txt` 파일들을 담당자에게 전달

> 만약 여러번의 로그추출이 필요하면, log1.txt 파일이름을 `log2.txt` 파일과 같이 변경해가면서 9번~10번을 반복실행

[official_android_website]: https://developer.android.com/studio/releases/platform-tools.html
[universal_adb_driver]: https://github.com/b6pzeusbc54tvhw5jgpyw8pwz2x6gs/about-debug/raw/master/android/universaladbdriver_v4.0.zip
