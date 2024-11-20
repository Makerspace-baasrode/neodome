# WLED software

To keep it simple, and as a first step to light up the neodome, we use the default WLED firmware.

## WLED configuration files

To simplify the WLED configuration for 15 nodes, open the [WLED configuration template](wled_cfg_neodome_NNN.json) and find and replace NNN with the IRA Node number. Save the resulting file as wled_cfg_neodome_-`Node number`.json

## Flashing WLED firmware on IRA board

1.  Disconnect everything from the IRA board: no LED strips or 12V power!
2.  Push the BOOT button on the PCB while connecting the PCB with USB-C to your PC.
3.  Open the [WLED web installer](https://install.wled.me) in a chromium-based web browser.
4.  Select firmware version 0.14.3 build 2404040
> Note that we experienced serious lag and irresponsiveness running WLED firmware version 0.14.4! This was manifested in mostly timeouts and occasional high ping responses exceeding 1 second while normal responses should be around 10 milliseconds or less. 
5.  Click `Install` and select the appropriate serial port and Connect.
6.  Click `INSTALL WLED` and `INSTALL`. This will take about 2 minutes.
7.  Click `NEXT` when installation is complete, select the `Makerspace-Baasrode` wifi network and enter the Password to connect.
8.  Click `VISIT DEVICE` to open the WLED web interface

## WLED on IRA configuration

1.  Navigate to the WLED web interface of the neodome IRA board
2.  Config > Security & Updates
3.  Choose file under `Restore presets`, select `wled_presets_neodome.json` and click `Upload`. You should get a green `File Uploaded!` popup.
4.  Choose file under `Restore configuration`, select wled_cfg_neodome_`Node number`.json and click `Upload`. You should get a green `Configuration restores succesfull. Rebooting!` popup.

## WLED on IRA manual configuration via GUI
        
- Wifi setup
  - Network name: `Makerspace-Baasrode`
  - Network password: `password`
  - mDNS address: `wled-930`
  - AP SSID: `WLED-AP-930`
- LED Preferences
  - Maximum Current: `2000`
  - LED voltage: `12V 30mA`
  - LED outputs 1 Length: `45`
  - LED outputs 1 GPIO: `4`
  - LED outputs 1 Color Order: `BRG`
  - LED outputs 2 Length: `45`
  - LED outputs 2 GPIO: `12`
  - LED outputs 3 Length: `45`
  - LED outputs 3 GPIO: `14`
  - LED outputs 4 Length: `45`
  - LED outputs 4 GPIO: `25`
  - LED outputs 5 Length: `45`
  - LED outputs 5 GPIO: `27`
  - Apply preset at boot: `1`
 - User Interface
   - Server description: `Dome-Node-930`
   - Preset: `pink` / `solid`, preset `1`
        
Url for downloading JSON config: http://4.3.2.1/json/cfg when connected to the WLED AP.

