# VNC
```bash
#!/usr/bin/env bash

read -p "
  VNC Option
  
   S : Start
   E : End
<  " option

if [[ $option == "S"* ]] || [[ $option == "s"* ]]
then
  vncstart && am start --user 0 -n com.realvnc.viewer.android/com.realvnc.viewer.android.app.ConnectionChooserActivity
elif [[ $option == "E"* ]] || [[ $option == "e"* ]]
then
  am start --user 0 -n com.termux/com.termux.app.TermuxActivity && vncstop
fi
```
