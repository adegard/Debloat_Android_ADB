## secondary screen
Install Taskbar first
https://github.com/Genymobile/scrcpy/issues/1887
</br>
So to summarize:

# enable a secondary display (2560x1440, dpi=160, use a higher value for bigger icons)
adb shell settings put global overlay_display_devices 2560x1440/160

# run on the secondary display (if the id does not exist, scrcpy will print available display ids)
# (set the bitrate to 16Mbps for better quality)
scrcpy -b16M --display=1

# disable secondary displays
adb shell settings delete global overlay_display_devices

To enable freeform window mode:

# enable freeform support
adb shell settings put global enable_freeform_support 1  # then reboot the device

(It could be added in the README I guess)

Some feedbacks: in practice (at least on my device), it's not very convenient for daily usage:

    the secondary display "overlay" is visible on the main device
    if an app is started on the main display, opening it from the secondary display launcher does nothing (it's already open, but not visible on the computer, which is confusing)
    dpi has not the same effects on all apps (for example, on Firefox, the text is big, while it's ok in some other apps)
    freeform window does not work for all apps
    when it works, the window has a given size, but cannot be resized (or I didn't find how)

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

