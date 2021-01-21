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

## Get info on all packages
`adb shell dumpsys package packages`

## uninstall packages
`adb shell pm uninstall -k --user 0 <package_name>`

eg.
`adb shell pm uninstall -k --user 0 com.cybermedia.cyberflx`
