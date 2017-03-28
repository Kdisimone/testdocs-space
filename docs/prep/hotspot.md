# Mobile Hotspot

<p align="center">
<img src="../img/watch.png" width="150">
</p>

Cell phones can use their cell data to act as a portable internet connection.  Mobile hotspot comes preinstalled on most compatible devices. Depending on your device, it may be an app in your App menu or an option under Settings. It may also be named something different than Mobile Hotspot, like Personal Hotspot (iOS), Internet Sharing (Windows) or Portable Wi-Fi Hotspot (Google Nexus devices). But these all do the same thing.  Unfortunately, the mobile hotspot feature is not standardized across all phones or all cellular service providers.  Some service providers charge extra for this feature, some limit the amount of data that can be used on personal hotpsot each month, and others only allow hotspotting through a wifi connection (and not through BT tethering).  

## Check your service provider

An absolute must-do ahead of your rig build...**CHECK YOUR CELLULAR SERVICE PROVIDER'S PERSONAL HOTSPOT FEATURE**.

Either call-in or login to your account and double check how your particular personal hotpsot feature is enabled for your device.  Check if there are any fees or restrictions.  Many providers will have areas in your online account where you simply need to toggle the feature "on" in order to use the personal hotspot service.  Other services like Ting, [restrict BT-tethered hotspot use to 3G data only (not LTE)](https://help.ting.com/hc/en-us/articles/205422068-FAQ-Tethering-and-Personal-Hotspots-) and you have to specifically turn off LTE service to use the feature.  Checking with your provider ahead will potentially save you a lot of troubleshooting time later.

## Hotspot Tethering

A device (like your rig) can be connected (tethered) to your phone's hotspot in one of 3 ways; wifi, BT, or USB:

* **wifi**:  The wifi tethering signal for the hotspot is not constantly broadcast by your phone, however.  So when you want to use the wifi connection to your hotspot (for example, you are leaving your home wifi network and traveling), you will need to **manually toggle your hotspot `off-on`** so that the phone will broadcast a wifi signal for the rig to connect to.  The other consideration is that since this is a wifi connection, the rig will not automatically disconnect when you come into one of your other known wifi networks.  You will have to remember to manually disconnect (toggle hotspot off), if you do not wish to continue using cell data when you are home.  Hotspot done by wifi connections also use more phone battery than a BT tether connection.

* **BT**:  BT tethering requires your phone and rig to be BT-paired before they can connect (and you'll specifically set that up later in these docs).  The advantage of connecting to your hotspot via BT tether is that it will happen automatically.  You do not have to remember to toggle hotspot.  Simply **leave your hotspot toggled `on`** as usual, leave the house, and within a few minutes (or sooner) your rig will BT tether to the hotspot.  You'll see a blue bar across the top of your iPhone screen indicating a device is connected via personal hotspot. Your rig will then use your cell phone as its internet connection.  When your rig comes back into a known wifi network, it will automatically drop the BT tether and connect with the wifi network.  Screenshot below shows what you'll see in your network logs as you move from known wifi network to BT tether.  oref0-online will automatically find BT tether and connect.

* **USB**: You can plug devices directly into your cell phone to use hotspot.  However, the phone would pull battery power from your rig and would drain your battery fairly quickly.  This is not a recommended connection method for OpenAPS use.

## Wifi vs. BT Hotspot

* If you choose **wifi tether**, you must manually turn it on; wait for the rig to connect; and when you get home, you must manually turn it off or your rig will not switch to home wifi. This also consumes more battery on the phone.

* If you choose to **BT tether**, it takes extra steps to setup ahead of time, but your rig will automatically connect when it loses connections to any known wifi networks (i.e. walking out the door) without you even having to pull the phone out of your pocket; it automatically allows the rig move to a known wifi network when one comes back in range; and it consumes less battery on the phone compared to wifi-connected hotspot.

## Tethering on Androids

Some android phones running marshmallow may want to check out this website for [information on tethering](http://techiezlounge.com/enable-tethering-android-6-0-marshmallow/)
