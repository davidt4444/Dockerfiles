#### primary
sudo apt update
sudo apt upgrade
sudo apt install xvfb
sudo apt install x11vnc
sudo apt install wm2
sudo apt install vanilla-gnome-desktop
or
sudo apt install gnome-session
sudo apt install scrot
sudo apt install xterm
#### minimal run
Xvfb :1 -ac -screen 0 800x600x16 &
DISPLAY=:1 wm2 &
DISPLAY=:1 xterm &
DISPLAY=:1 scrot screen.png
x11vnc -nopw -localhost -display :1

#### normal minimal run
Xvfb :1 -ac -screen 0 1024x768x16 &
DISPLAY=:1 gnome-session &
DISPLAY=:1 xterm &
x11vnc -nopw -localhost -display :1
