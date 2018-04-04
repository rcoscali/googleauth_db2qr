# googleauth_db2qr
Use an android extracted sqlite3 db for generating QR codes. Allows to recreate easily a google auth install (in iphone for ex)
The database in android is in /data/data/com.google.android.apps.authenticator2/databases/databases
I pull it from the device with adb and saved it in a google-authenticator2.db file
Script also generate some png and svg for the QRcode for eventual use.
The script able to generate QRcodes displayed:
- In a terminal
- With the Image Magick display command
- With NodeJS in a browser window (allows to use the scan QRcode feature of some Authenticator chrome extensions, see https://chrome.google.com/webstore/detail/authenticator/bhghoamapcdpbohphigoooaddinpkbai or https://github.com/Authenticator-Extension/Authenticator)

It is also able to generate a JSON importation file for the Authenticator Chrome extension.
These feature may be activated/deactivated through env var.
(Didn't have time for a better interface, actually it does the trick)

```bash
    cohen@mobdevrcs:~/Sources/googleauth_db2qr$ ./googleauth_db2qr
    error: missing database filename argument !

    usage: ./googleauth_db2qr <DBFILE>
    usage:    use environment variables for disabling some features:
    usage:      - set NO_TERM_OUTPUT to disable display in terminal
    usage:      - set NO_DISPLAY to disable display with image magic
    usage:      - set NO_WAIT to disable pausing between each account
    usage:      - set NO_NODE_JS to disable running http server
    usage:      - set NO_AUTH_JSON_IMPORT to disable Chrome Authenticator JSON import file generation
    cohen@mobdevrcs:~/Sources/googleauth_db2qr$ 
```

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

Here are some of the generated images:

image                                | url
-------------------------------------|---------------------
* [ScreenShot QRCode](https://github.com/rcoscali/googleauth_db2qr/blob/master/QRcode.png): | [```https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/QRcode.png```](https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/QRcode.png)
* [ScreenShot exec](https://github.com/rcoscali/googleauth_db2qr/blob/master/ScreenShot.png): | [```   https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/ScreenShot.png```](https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/ScreenShot.png)
* [PNG QRcode](https://github.com/rcoscali/googleauth_db2qr/blob/master/cohen%40PCLX30164.png): | [```        https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/cohen@PCLX30164.png```](https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/cohen@PCLX30164.png)
* [SVG QRcode](https://github.com/rcoscali/googleauth_db2qr/blob/master/cohen%40PCLX30164.svg): | [```        https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/cohen@PCLX30164.svg```](https://raw.githubusercontent.com/rcoscali/googleauth_db2qr/master/cohen@PCLX30164.svg)

