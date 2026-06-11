Method1:
- https://forums.lenovo.com/t5/Lenovo-C-E-K-L-M-N-and-V-Series-Laptops/Update-lenovo-bios-without-battery-in-the-pc/m-p/5148992?page=1
1. Just download the bios.exe file 
2. run the exe while extracting it press cancel .Do not press Yes after cancel. Leave it on that screen, goto temp folder (Win+R from keyboard , write without quotes "%temp%"  enter. find the bios extracton folder and .ini file in it.
3. Open the .ini file , find "BatteryCheck=1" line in the page, change 1 to 0 and save the .ini file
4. Go back the screen that we leave background and press No.

Method2:
- https://www.youtube.com/watch?v=rGp-Zydc2JM
- Bat Dateibearbeiten und cbp flag entfernen

Method3:
- ThinkPad T430 without a battery, I finally get it done by running the winflash64.exe in CMD with the following flags:
- winflash64.exe -file G1ETC2WW\$01D2000.FL1 -sn -oc bypass_power (change Folder und Filename accordingly)
