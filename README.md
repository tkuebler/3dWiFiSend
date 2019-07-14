# 3dWiFiSend
Qidi X-Pro/X-Max Network Script

##### _note from original author:_
_This is a python script I threw together to allow me to send my gcode file from my pc to my printer over the network._

_The Qidi X-Pro 3D printer has network built in and allows you to send your files and start printing from Qidi's own software. I wanted to use Simplify 3D instead and also not have to walk to and from my printer so this script came out._

_I am not a python person. I absolutely hate python with a burning passion so this code is ugly and does not error-check. Basically, it is not written to really be distributed but I figured I'd share so that someone who actually has the patience to deal with python can improve it or whatever._

_I've tried to keep it simple to use._ 

### Instructions 

There are 2 files. 

One is the python script itself the other is a compressor for windows only - 
for macs you must have the QIDI Print software installed because it gets the compressor from there.
 
There is also a test file included, which is a small printer test file.

To use make sure that you have a flash drive plugged into the printer. I find it is a lot more reliable over ethernet than over wifi but YMMV. 

Here is how to use it:
"python 3DWiFiSendFile.py IPADDRESS FILE.GCODE [yes|no]"

example:

    python3 3DWiFiSendFile.py 192.168.3.100 test.gcode yes

The first argument is the ip address of the printer. Second argument is the name/path to the gcode file. Third arg is an optional print flag. If you add 'yes' as the third arg, the printer will also print the file after copying it. If you don't put anything there, it will just copy the file over without printing.

youtube video:   https://youtu.be/agJc9IzfyQk

note: Now works on mac and against QIDI X-MAX as well.


### Erratta

Sources for M Commands:

experimentation with just sending codes to the printer and seeing what happens:

    echo "M4001" | nc -u 192.168.3.100 3000
    
 -and-

observation of QIDI Print softare interacting with printer via tcpdump:  

    sudo tcpdump -i en9 -nn -s0 -v host 192.168.3.100

  -and-
  
[GCode Spec](https://reprap.org/wiki/G-code#M115:_Get_Firmware_Version_and_Capabilities)

[Similar printer board info](https://github.com/Photonsters/anycubic-photon-docs/blob/master/photon-blueprints/readme.md)

[Similar board, diffeent info site](https://github.com/Photonsters/anycubic-photon-docs/blob/master/photon-blueprints/ChituClientWifiProtocol-translated.txt)
