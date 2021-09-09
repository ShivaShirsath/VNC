# VNC
**Install**
```bash
PWDx=$PWD
cd ~
git clone git://github.com/ShivaShirsath/VNC.git
cd VNC
bash install
cd $PWDx
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
