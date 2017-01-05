# googleauth_db2qr
Use an android extracted sqlite3 db for generating QR codes. Allows to recreate easily a google auth install (in iphone for ex)
The database in android is in /data/data/com.google.android.apps.authenticator2/databases/databases
I pull it from the device with adb and saved it in a google-authenticator2.db file

here is an example:

```bash
cohen@PCL30164 $ adb pull /data/data/com.google.android.apps.authenticator2/databases/databases google-authenticator2.db
55 KB/s (5250 bytes in 0.093s)
cohen@PCL30164 $ googleauth_db2qr google-authenticator2.db
Identification               cohen@PCLX30164
Email                        cohen@PCLX30164
Provider                     0
Issuer                       
Original name                cohen@PCLX30164
Secret                       F4YK4HPPDGYMBOFR
Normalized secret            F4YK4HPPDGYMBOFR

URL                          otpauth://totp/cohen%40PCLX30164?secret=F4YK4HPPDGYMBOFR&issuer=&original_name=cohen%40PCLX30164&

█████████████████████████████████████████████████
█████████████████████████████████████████████████
████ ▄▄▄▄▄ ██ ▄▀▀▀█▀ ▀█▄▄▄▄▄█▄▀█ ▀▄▄██ ▄▄▄▄▄ ████
████ █   █ █████ ▀▄▀▀ █    ▀█▀█ ▀ ▄ ██ █   █ ████
████ █▄▄▄█ █▀▀ ███▄█▀▀█▀ ▀▀▀█  ▀█  ▀▀█ █▄▄▄█ ████
████▄▄▄▄▄▄▄█▄█▄▀▄█▄▀ ▀ █▄▀▄█▄█▄▀▄▀ █ █▄▄▄▄▄▄▄████
████▄▀▀ █ ▄█▄█ ▄▀ ▄  █▄▀█ █▄  ██▀█▄▄█▄█▄██▀▀▀████
████▀▄ ▀▄ ▄ ▀▄█ █▀▀▄▀ ▄▄ ▄ █▄  ▀▀▄█▄ ▀█ ██▀  ████
████▀█▄ ▀▄▄▀▀▀█▄▀█▀▀█  █  ▀ ██▀▀▄▀█▄▄█▄▀▄▄█ ▄████
█████ ▀ ██▄▀▀ █▄██▀█▄██▄▀ █ █▄▄█▄██▄▀▄▄▀▄▀█  ████
████▄▄█▀██▄ ▀▄▀▄ ▀▄ ▀ ▀▀█▀▀▀▀█▀█ ▄▀▀█▄▀ ██ ▀█████
████▀▀ ▀▄▀▄▀▄ ▄█▄ █▀▄▄█ █▀▄ ▀ ██▄▀  █▄▄ ▄█▀▀ ████
████ ▄▀▀█▀▄ ▄▀▀ ▄  ▀█▄█▀▄█ ▄ █▄█▄█▄██ ▀ █ █▀▀████
████  ▄ ▀█▄█  ▀█▄▀▀▄ ▀▄ ▄ ▄█▄▀█▄ ▄▀▀▄ ▀▄▀ ▀ █████
████▀██▀ ▄▄█▀ █▄▀▄▄  ██▀█  ▄ ▄███▄▀ █▄  █▀▄▄ ████
████ █▄▀▄▀▄ ▀█▄▀█▄▄ ▀▀█▄▀██▄▀█▄█▀▄█▀█▀ ████  ████
████▄█▄█  ▄▄▀██ ▄ █▄▀██ ▀ ▀▄ ▀█ █▄▄█▄▀▄█ ▀▀ █████
████▄█▀█▀▄▄▄█▄▀  ▀▀▀█▄███▄▀▄ ▄█▀  ▀█   █▄██▄▀████
████▄███▄▄▄█   █  ▀██ ▄▀ █▀▀ ▀▀ █▀▄  ▄▄▄ █▄▀ ████
████ ▄▄▄▄▄ █▀█▄▀█▄█ ██ ▄▄▄▄   ▄▄▀▄▄▀ █▄█ ▀▀  ████
████ █   █ █▀▀▀█▄ ▀ ██ █▄▀▀███ ▀ ▀█▀ ▄    █▄ ████
████ █▄▄▄█ ██▄▀▀█▀▀▄▀▀█▄▄▀▄ ▄ ▀▄  █ ▀█▀▀▄█▄▀▄████
████▄▄▄▄▄▄▄█▄█▄▄▄▄▄▄▄█▄▄▄▄▄▄▄██▄█▄██▄█▄█▄▄█▄█████
█████████████████████████████████████████████████
█████████████████████████████████████████████████

cohen@PCL30164 $ 
```

* ScreenShot QRCode: https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/QRcode.png
* ScreenShot exec:   https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/ScreenShot.png
