
If you want to keep your rig small and portable, using the internet will be important.  Without an internet connection, you will need to plug your receiver directly into the rig's OTG port and a portable battery pack into the UART port.  This increases your rig's size pretty substantially.  (see offline looping for more detailed information about alternate way to achieve offline looping...some of which are more complex to setup)

## Known wifi networks

You will want to prepare ahead of your rig-build by gathering the wifi network names and passwords from areas that you will be at frequently (home, friends' houses, work, etc).  By adding known wifi networks to your your rig's setup, you can save from using your cellular data plan to keep your rig running.  As you are gathering the network names and passwords, remember to pay attention to lower vs upper case letter, hypens, or special characters.  If the names and passwords do not match exactly, the rig will not be able to connect to the network.

## School wifi networks

If you are sending your t1d kid to school with an OpenAPS rig, talk with the school district's IT department ahead of building your rig.  Find out if they will allow your rig to access their wifi network, and if so, whether there is any special restrictions or login issues you should know about.  Some school districts will need the MAC address of the rig to add it to their "approved" devices list.  Other school districts may need a more complex wifi access setup ahead of time (see Rig, Wifi for more info).

If the school district refuses to allow the rig access to the school's wifi network, you can use BT tethering to your phone's hotspot to stay online while at school.  The downside is that you will be using your cell data during the school day and it will cause added drain on the phone's battery.  

In some cases, schools have let the phone on the school's wifi but not the rig.  Unfotunately though, the phone cannot use the school's wifi while the rig is BT-tethered to it.  A work-around would be to use a mifi device through your cell provider.  The mifi is a small box (about half the size of a dex receiver usually) that projects a wifi signal using your cellular dat plan.  If you use a mifi, the phone could stay connected to the school's wifi and the rig could stay connected to the mifi.

Ideally, though, work to get the school to allow the rig access on their wifi network.

## Home router

Have you ever accessed your home router to see the devices connected to it?  You should try to do that ahead of your rig build, as it can be a super fast tool for troubleshooting during early rig building steps.  Most home routers can be accessed by going to the URL `http://192.168.1.1` on your computer's browser.  The default login for NetGear routers has user as `admin` and the password as `password`.  The default login for Linksys routers has no user name and password is `admin`.  For Asus routers, the default for both user and password is `admin`.  If you are unsure of your router's specifics, google "how to access _______ router" and put your router's brand name in that search field.

By having access to your home router, you can easily see if you rig is listed as a connected device.  You can also bring up the MAC address and IP address of the rig, which may be helpful in other areas of the rig setup that are discussed later.  [Note:  The rig's MAC address will remain constant.  The IP address of the rig will change depending on where it is connected.]

<p align="center">
<img src="../img/app_group_name.jpg" width="400">
</p>




