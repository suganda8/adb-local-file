# ADB - Pulling App Local File without Root Access

According to [Android Studio Developers User Guide](https://developer.android.com/studio/command-line/adb).
\
Android Debug Bridge (adb) is a versatile command-line tool that lets you communicate with a device.
\
The adb command facilitates a variety of device actions, such as installing and debugging apps,
\
and it provides access to a Unix shell that you can use to run a variety of commands on a device.
\
It is a client-server program that includes three components:

- A client, which sends commands. The client runs on your development machine. You can invoke a client from a command-line terminal by issuing an adb command.
- A daemon (adbd), which runs commands on a device. The daemon runs as a background process on each device.
- A server, which manages communication between the client and the daemon. The server runs as a background process on your development machine.

## Download
`adb` is included inside the Android SDK Platform-Tools package.

To download Android SDK Platform-Tools, you need to download [Android SDK Manager](https://developer.android.com/studio/index.html#command-tools).
\
But if you already have `android-sdk` installed by Android Studio, check under your `android-sdk` path to look for `platform-tools` folder.

Use `sdkmanager` command through your terminal. An example command : `sdkmanager "platform-tools" "platforms;android-31"`

`sdkmanager` will installs `platform-tools` at android_sdk/platform-tools/.

To quick accessing command, add `.exe`'s folder or bin named folders path to System Environtment Variable.

## Local File
Managing local file such as SQLite databases, shared preferences, and other files without Android Studio's Device File Explorer is not quite a big problem. Here is basic commands of local file that you should know. Commands below can be used without root access.

### Commands
- List of devices
```
adb devices
```


- Run command to specific devices
```
adb -s <devices-id or ip:port> <command>
```


- Direct command to the only attached USB device
```
adb -d <command>
```
Note: Returns an error when more than one USB device is attached.


- Direct command to the only running Emulator
```
adb -e <command>
```
Note: Returns an error when more than one emulator is running.


- Checking file and paths
```
adb shell
run-as <package-name>
ls -l
```
Note: "run-as \<package-name>" will automatically enter to app's local directory.


- Pulling file without root access
```
adb exec-out run-as com.example.app_name cat file.ext > D:/file.ext
```
Note: You will copy "file.ext" out from app's local directory to your PC directory using "exec-out" command. (C:/ Path access needs Terminal as an Administrator)


- Deleting file inside app's local dir
```
adb shell "run-as com.example.app_name rm file.ext"
```
