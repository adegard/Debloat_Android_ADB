## secondary screen
Install Taskbar first
adb shell settings put global overlay_display_devices \"\"
adb shell settings put global overlay_display_devices 1915x998/225
scrcpy -b24M --display 13

# adb shell pm grant com.farmerbb.taskbar android.permission.WRITE_SECURE_SETTINGS

see
</br>
https://github.com/nikp123/scrcpy-desktop
</br>and

https://github.com/Genymobile/scrcpy/issues/2114#issue-comment-box

# resizing screen
adb shell wm size reset
</br>
adb shell wm size 1080x1920
</br>

Physical size: 720x1280
Override size: 1080x1920


# Debloat_Android_ADB
Collection of script (launched with Powershell or comand) to Debloat or Modify Android via  ADB (no root required)

## Install ADB
Easiest way is with <a href="https://chocolatey.org/install" target="_blank">Chocolatey</a>:

`choco install adb` 

## Resize Screen

`adb shell wm size reset`

`adb shell wm size 1080x1920`

eg.
Physical size: 720x1280
Override size: 1080x1920

## List all packages (apps)
`adb shell pm list packages`


## List all permissions
`adb shell cmd appops query-op RUN_IN_BACKGROUND allow | sort`


## Ignore Apps running in Background

`adb shell cmd appops set <package_name> RUN_IN_BACKGROUND ignore`

eg.
`adb shell cmd appops set com.amazon.mShop.android.shopping RUN_IN_BACKGROUND ignore`

## uninstall packages
`adb shell pm uninstall -k --user 0 <package_name>`

## install packages
`wget https://f-droid.org/F-Droid.apk`

then:
`adb install F-Droid.apk`

## GPU enhabcement (old phone / tablet)
`adb shell settings put global sem_enhanced_cpu_responsiveness 1`

