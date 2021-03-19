# MacOS TLS Key Logger

This repository contains a [Frida](https://frida.re/) script to log session keys of TLS traffic between macOS processes and distant servers (such as Apple services).

No need for proxy interception to decrypt traffic anymore, though it might require to deactivate SIP.

Tested on a MacbookPro13,3 on Catalina, and Big Sur 11.3 beta 4.

Credits to [Andy Davies](https://codeshare.frida.re/@andydavies/ios-tls-keylogger/) for the original script that works with iOS devices.


## Deactivate SIP

1. Turn off your Mac
2. Hold down `cmd+R` during boot
3. Choose *Utilities*, then *Terminal*
4. Enter the command `csrutil disable`

To enable again SIP, do the same steps but replace `disable` with `enable`.


## Usage 

Download the script and run the following command in a terminal:
```bash
frida -p <pid> -l catalina-tls-keylogger.js -o tls.keylog
```

The value `-p <pid>` can be replaced with `-n <process_name>`.

The log file can be used with Wireshark.


## Why it works

You can find details on [this page](https://andydavies.me/blog/2019/12/12/capturing-and-decrypting-https-traffic-from-ios-apps/) by the original author.