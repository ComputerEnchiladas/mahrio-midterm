# mahrio-motion-server-mobile
WNM499: Motion Sensor on Server with Mobile client

## Raspberry Pi, Power Supply & GPIO
![img](https://i.stack.imgur.com/sVvsB.jpg)

**__Note: The next steps are to connect hardware sensors so be sure to have Pi shutdown and disconnected from power source__**

Using the image above, locate __pin 40__ with label **GPIO 21**. This will be the signal input for either the digital button or motion sensor. Connect this pin to motion sensor's **OUT** pin (or **S** pin for digital button). Next, locate pin 1 with label **3V3 Power** and connect this to **VCC** pin on the motion sensor or **+** pin on digital button. Lastly, locate pin 39 with label **Ground** on the pi and connect it to **GND** pin on the motion sensor or **-** pin for button.

With hardware setup complete you may now power the Raspberry Pi.

## Clone this Repo and Install Dependencies
Clone this repo using `git clone https://github.com/ComputerEnchiladas/mahrio-motion-server-mobile.git` under WNM499.

Next enter the repo by using `cd mahrio-motion-server-mobile`. Then run the following commands to install dependencies.
- ```npm install``` - server dependencies
- ```bower install``` - client dependencies

Next, we will go into mobile directory with `cd mobile`. Inside of mobile run ```npm install```

## Configure IP Addresses & Ports
**Whats my IP Address?** Using the command-prompt enter `ifconfig` and look for wlan0 section. In second line you will find __inet addr:XXX.XXX.XXX.XXX__

### IP Address & Port for Server
Go back to top level of repo. If you left off inside mobile folder, you will use `cd ..`. Open up __.env__ using `nano .env` and add your ip address and a port. A port will be assigned to you if multiple teams.

### Linking Mobile to Server
Using nano editor, open up the mobile app's index.html as followed `nano mobile/www/index.html`. Next scroll down to row 35 where you will find `var socket = io('http://192.168.0.8:8080');`, and replace __192.168.0.8:8080__ with you ip address and port that was configured for your server above.

## Start Web Server
Use the following command from top of directory: `node server/index.js`

If all went you should see on the console __Server running at: http://your-ip-address:port__

## Test Server using Web Client
With server running, navigate to the device's address with port. You should see a grey circle with black outline. Now Activate the motion sensor or button to see the grey circle turn green.

## Build & Test with Mobile App
You will need to download **Ionic View** for either IOS or Android. When app downloads, open and register with it. You will need the registration info in the next step.

Now we will navigate into mobile folder using `cd mobile`. Next, initiate upload of the mobile app to your account with the command: `ionic upload`. When upload completes, go back to **Ionic View** on your phone and you should see the app. Open it and see the same grey circle which turns green when button or motion is active.

Questions? Send them to jesus.rocha at whichdegree.co
