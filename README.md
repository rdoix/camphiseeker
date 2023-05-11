# CamPhiseeker
Collect Geo Location, device information, and Front Cam Shoot from target's smartphone camera or PC just sending a link.
This tool is a Proof of Concept and is for Educational Purposes Only, CamPhiseeker shows what data a malicious website can gather about you and your devices and why you should not click on random links and allow critical permissions such as Location, Camera and etc, it's not responsible for any misuse or illegal purposes.

## What is CamPhiseeker
This tool are adopted from [CamPhish](https://github.com/techchipnet/CamPhish) and [Seeker](https://github.com/thewhiteh4t/seeker), They are great tools, and I am grateful to the contributors.

The concept of CamPhiseeker is very simple. Generally, phishing pages are used to steal credentials, but CamPhiseeker is designed to gather information based on location, device information, and camera usage, utilizing popular web templates.

CamPhiseeker host a fake website can collect information without any permission, such as :
* Unique ID using Canvas Fingerprinting
* Device Model - Not always available
* Operating System
* Platform
* Number of CPU Cores - Approximate Results
* Amount of RAM - Approximate Results
* Screen Resolution
* GPU information
* Browser Name and Version
* Public IP Address
* Local IP Address
* Local Port
* ISP Information

CamPhiseeker host a fake website which ask for "Location" and "Camera" Permission and if the target "Allows" it, we can Get:
* Longitude
* Latitude
* Accuracy
* Altitude - Not always available
* Direction - Only available if user is moving
* Speed - Only available if user is moving
* Images from Front Camera

## How is this Different from IP GeoLocation
* Other tools and services offer IP Geolocation which is NOT accurate at all and does not give location of the target instead it is the approximate location of the ISP.
* Use HTML API and gets Location Permission and then grabs Longitude and Latitude using GPS Hardware which is present in the device, so works best with Smartphones, if the GPS Hardware is not present, such as on a Laptop, and fallbacks to IP Geolocation or it will look for Cached Coordinates.
* Generally if a user accepts location permsission, Accuracy of the information recieved is accurate to approximately 30 meters
* Accuracy depends on multiple factors which you may or may not control such as :
  * Device - Won't work on laptops or phones which have broken GPS
  * Browser - Some browsers block javascripts
  * GPS Calibration - If GPS is not calibrated you may get inaccurate results and this is very common

## Templates

Available Templates : 

* NearYou (Made by seeker team)
* Google Drive (Suggested by @Akaal_no_one)
* WhatsApp (Suggested by @Dazmed707)
* Telegram (Made by seeker team)
* Zoom (Made by @a7maadf)
* Google reCAPTCHA (Made by @MrEgyptian)

## Installation

### Kali Linux / Arch Linux / Ubuntu / Parrot OS / Termux

```bash
git clone https://github.com/rdoix/camphiseeker.git
cd camphiseeker/
chmod +x install.sh
./install.sh
```

### OSX
```bash
git clone https://github.com/rdoix/camphiseeker.git
cd camphiseeker/
python3 camphiseeker.py
````

In order to run in tunnel mode, install ngrok by running this command in the terminal:
```bash
brew install ngrok/ngrok/ngrok

ngrok http 8080
````

## Usage
CamPhiseeker manual
```bash
$ python3 camphiseeker.py -h

usage: camphiseeker.py [-h] [-k KML] [-p PORT] [-u] [-v]

options:
  -h, --help            show this help message and exit
  -k KML, --kml KML     KML filename
  -p PORT, --port PORT  Web server port [ Default : 8080 ]
  -u, --update          Check for updates
  -v, --version         Prints version
  ```
  
  ### Example 1
  Step 1 : Running in first terminal
  ```bash
  $ python3 camphiseeker.py
  ````
  
   Step 2 : Open the second teriminal to start a tunnel service with ngrok
  ```bash
 $ ./ngrok http 8080
  ````
  
  ### Example 2 (with optional)
  Step 1 : Running in first terminal with Ouput KML File for Google Earth dan custom port
  ```bash
$ python3 camphiseeker.py -k <filename> -p 1337
  ````
  
   Step 2 : Open the second teriminal to start a tunnel service with ngrok
  ```bash
$ ./ngrok http 1337
  ````
  
  For alaternative ngrok tunnel, you can use Cloudflared Tunnel, SSH tunnel, etc. or directly on VPS
