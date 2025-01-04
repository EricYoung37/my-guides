## Guide for Using Xfce4 Desktop with WSL2

### Install Linux on Windows with WSL

Follow the instructions [here](https://learn.microsoft.com/en-us/windows/wsl/install).
<br>**Note:** use `wsl.exe -l -o` to check available Linux distro before `wsl --install -d <Distribution Name>`

### Install and configure VcXsrv Server for Linux GUI

Follow the instructions [here](https://www.youtube.com/watch?v=8SuERIEJJUA), starting 7:39.
**For IPv4 configuration in `.bashrc`**, follow the instructions below instead.

1. Open Powershell or Command Prompt from Windows start menu
2. Type `ipconfig` and press enter
3. Take a note of the **native** IPv4 address of your Windows (NOT WSL), which typically starts with `192.168.`
4. Back to your `.bashrc` file, add `export DISPLAY=:192.168.D.D:D` at the end
5. In the Ubuntu terminal, type `source ~/.bashrc` and press enter

Now, go to Windows desktop to configure VcXsrv display.

1. Find the VcXsrv shortcut, right click and choose `Properties` from the context menu
2. Select the tab `Compatibility` and then click `Change high DPI settings`
3. Under `High DPI scaling override`, check `Override high DPI scaling behavior` and select `Application` in the drop-down menu labeled `Scaling performed by:`.

### Run Xfce4

1. Run VcXsrv. Select `One large window` in display settings and check `Disabled access control` in extra settings.
2. In the Ubuntu terminal, type command `startxfce4` (with VcXsrv already running) and press enter

### Install and Run IntelliJ IDEA in WSL

1. Run Firebox in the Ubuntu desktop
2. Get [IntelliJ IDEA](https://www.jetbrains.com/idea/)
3. After it is installed, configure the PATH variable in WSL so that it is more convenient to launch IDEA.<br>
   In the IDEA installation folder, there should be a file named `Install-Linux-tar.txt`, which suggests adding
   `export PATH=$PATH:"{IDEA installation folder}/bin"` at the end of `.bashrc`
4. In a new Ubuntu Terminal, type `idea.sh` and press enter to run IDEA.

### Other Useful Tips for IDEA

In **Project Structure-Platform Settings**,

1. The **SDKs** section can be used for setting the **JDK** version
2. The **Global libraries** section can be used for setting other languages (e.g., Scala, OCaml)
3. The SDKs installed in the native Windows environment cannot be used by the Ubuntu environment
