# VNC
```bash
#!/bin/bash

YES=0
NO=1
DIALOG_ESC=255
HEIGHT=0
WIDTH=0

display_result() {
        dialog \
        --title "$1" \
        --no-collapse \
        --msgbox "$result" $HEIGHT $WIDTH
}

type -p "dialog" &>/dev/null || {
        echo -e "\n${R} [${W}-${R}]${G} Installing package : ${Y}dialog${C}"${W};
        sudo apt install "dialog" -y --no-install-recommends;
}

while true; do
        dialog \
        --title "VNC" \
        --clear \
        --ok-label "Start" \
        --cancel-label "Stop" \
        --yesno "Start\nStop\nESC" $HEIGHT $WIDTH

        case $? in
                $YES )
                        clear
                        tigervncserver -kill :*
                        rm -rf /username/.vnc/localhost:*.pid
                        rm -rf /tmp/.X1-lock
                        rm -rf /tmp/.X11-unix/X1

                        tigervncserver -kill :*
                        rm -rf /username/.vnc/localhost:*.pid
                        rm -rf /tmp/.X1-lock
                        rm -rf /tmp/.X11-unix/X1

                        tigervncserver \
                                -xstartup /usr/bin/startxfce4 \
                                -geometry 1512x750 \
                                -localhost no :1 \
                                -pixelformat rgb888 \
                                -depth 32 \
                                -SecurityTypes None \
                                --I-KNOW-THIS-IS-INSECURE

                        $PREFIX/bin/termux-open vnc://localhost:5901
                break
                ;;
                $NO )
                        clear
                        tigervncserver -kill :*
                        rm -rf /username/.vnc/localhost:*.pid
                        rm -rf /tmp/.X1-lock
                        rm -rf /tmp/.X11-unix/X1
                break
                ;;
                $DIALOG_ESC )
                        clear
                        exit 1
                break
                ;;
        esac
done
```
**Error**
```bash
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```
   **Solution**
   ```bash
   locale-gen en_US.UTF-8
   export LANGUAGE=en_US.UTF-8
   export LANG=en_US.UTF-8
   export LC_ALL=en_US.UTF-8
   locale-gen en_US.UTF-8
   sudo dpkg-reconfigure locales 
   # select en_US.UTF-8 UTF-8 (159 ) 
   # select en_US.UTF-8 ( 3 )
   ```
