
You won't get far in your OpenAPS without some important pieces of gear.  Get your gear together well ahead of your build for a smooth setup.
*********************

## Computer

You can use a Windows or Apple computer (or raspberry pi or...)
**********************

## Cell Phone

OpenAPS can use either Android or iPhone.  There are some features that are only available on Android vs iPhone, but they are only about the peripheral parts of the OpenAPS setup (such as x-drip+ app and http widget).  The core of OpenAPS (oref0 and openaps) is the same no matter which phone you are using.
*********************

## Medtronic pump


!["Can I do OpenAPS with this pump?"](../Can_I_close_the_loop_with_this_pump_May_20_2016.jpg "Can I do OpenAPS with this pump?")

Currently, only the following Medtronic MiniMed models allow us to remotely set temporary basal rate commands, which is required to use OpenAPS:

    512/712 (note: needs special set-up in OpenAPS)
    515/715
    522/722
    523/723 (with firmware 2.4A or lower)
    554/754 (European Veo, with firmware 2.6A or lower; OR Canadian Veo with firmware 2.7A or lower)

NOTE: For European/WorldWide users who have access to a `DANA*R` insulin pump, you may be able to use AndroidAPS, which leverages OpenAPS's oref0 algorithm but allows you to interface using an Android phone and Bluetooth to communicate directly with the `DANA*R` pump. [See here for instructions and details related to AndroidAPS](https://github.com/MilosKozak/AndroidAPS).

#### Firmware

Due to changes in the firmware, the openaps tools are only able to function in
full on the above pump models. Security features were added after the firmware
version 2.4 in the US that prevent making some remote adjustments.

To check firmware, hit Esc on the home screen and scroll all the way to the bottom. You can also go into the Utilities menu and "Connect Devices" menu and look for a PC Connect option. If that is present, the pump will not work for looping. If it’s absent, it should be able to receive temp basal commands.)

If you have one of the above mentioned pumps, but it has buttons that do not work, use the instructions found on this [Imgur photo album](http://imgur.com/a/iOXAP) to repair your pump.

#### Models

To determine your pump model, look at the back side of your pump.  There should be a sticker on the underside of the pump.  On the right hand side of the sticker, it says REF MMT-XXXXXX

![Pump](img/pump_model.jpg)

In the example above, it says the pump model is:  MMT-722NAS

    MMT         Pump Manufacturer Model (MiniMed Medtronic)
    722         Pump Model Number
    NA          Pump Region (NA=North America, CA=Canada/Australia, WW=Worldwide)
    S           Pump Color (S=Smoke, L=Clear/Lucite, B=Blue, P=Pink/Purple)

Some pumps may have an “L” or “S” or "R" before the pump region, e.g. a model number like MMT-LNAS.  This does not affect compatibility.

The difference between the Medtronic 500 series and the 700 series pumps is the size of the insulin reservoirs.  The 500 series pumps use a 180 unit reservoir, and the 700 series pumps use a 300 unit reservoir (or smaller 180 unit reservoir, if you want).

The difference between the Medtronic x22 pumps and the x23 pumps is primarily two features.  

* The x23 pumps will allow for increments of 0.025 units, whereas the x22 pumps have larger increments of 0.05 units.  OpenAPS will have the insulin delivery automatically rounded by the pump to the units available in the pump model, and any smaller adjustments (to make up for the rounding) will be made through OpenAPS’s use of temp basals.  

* The x23 series pumps are also faster at delivering large boluses (up to several times faster for boluses > 10 units).

For 512/712 pumps, certain commands like Read Settings, BG Targets and certain Read Basal Profile are not available, and requires creating a static json for needed info missing to successfully run the loop ([see example here](http://bit.ly/1itCsRl)).


#### Tips for finding a compatible pump

If you need to acquire an appropriate pump check CraigsList or other sites like
Medwow or talk to friends in your local community to see if there are any old
pumps lying around in their closets gathering dust. [MedWow](http://www.medwow.com) is an eBay-like source for used pumps. [SearchTempest](http://www.searchtempest.com) is a great tool for searching Craigslist nationally all at once. In addition to searching for listings, consider posting an offer to Craigslist or ask around local community groups.

Note: If you're buying a pump online, we recommend you ask the seller to confirm the
firmware version of the pump. (You may also want to consider asking for a video
of the pump with working functionality before purchasing.)

#### Battery usage

Repeated wireless communication with the pump drains the battery quite quickly.
With a loop running every five minutes, a standard alkaline AAA—recommended by
Medtronic—lasts somewhere about four days before the pump goes to a
"Low Battery" state and stops allowing wireless transmission. Lithium batteries
last significantly longer but do not give much warning when they are about to
die.  You can set alerts in Nightscout to provide warning about the status of the
battery. For further information on batteries, see
[this study](https://gist.github.com/channemann/0a81661b78703fcb8da6) on AAA
battery use in a looping pump.
**************

# CGM 

* Dexcom G4 Platinum System (with or without Share)
* Dexcom G5 Mobile
* Medtronic (MiniMed Paradigm REAL-Time Revel or Enlite)


The openaps tool set currently primarily supports three different CGM systems: the Dexcom G4 Platinum system (with or without the [Share](http://www.dexcom.com/dexcom-g4-platinum-share) functionality), the newer Dexcom G5 Mobile system and the [Medtronic system](https://www.medtronicdiabetes.com/treatment-and-products/enlite-sensor). Other CGM or CGM-like devices (Libre) can also be used if the data is uploaded to Nightscout and the OpenAPS rig has internet connectivity (aka on-line).

With Dexcom, the Share platform is not required, but using Share can help keep the size of the rig to a minimum.  Without Share, the receiver can be plugged in directly to the OpenAPS rig and will need a portable battery to power the receiver too.

NOTE: You can also pull CGM data from Nightscout as an alternative (including Dexcom G5 to iOS device + Nightscout Bridge plugin), or use xDrip (see below). The Medtronic CGM system communicates directly with the associated pump, so that data can be retrieved using the CareLink USB stick. The Medtronic Minimed 530g Pump's Enlite CGM Sensors CAN be used with the older OpenAPS compatible Medtronic Pumps (Despite that pump originally being offered with SoftSensor CGM Sensors).

#### Using the Medtronic CGM

Because the Medtronic pump collects data directly from the Enlite sensors, OpenAPS will retrieve CGM data in addition to your regular pump data from your pump. While you use the same OpenAPS commands to get it, the Medtronic CGM data may need a little special formatting after being retrieved. If so, it will be specified in other areas of the documentation.
********************

# The Rig

NOTE:  The Explorer Board and Edison are DIFFERENT PIECES OF EQUIPMENT.  They are not sold as a single unit.  You will be ordering them separately.  And you need to buy BOTH of them.

* **Edison** is the short name for the Intel Edison Compute Module.  Edison is the brains of your OpenAPS system.  It holds the looping code and information about your known wifi networks, too.  Most Edisons come with an operating system called Yocto.  OpenAPS needs an updated version called Jubilinux installed instead.  The process of updating the Edison is called "flashing".  You can either buy an [unflashed Edison](https://www.sparkfun.com/products/13024) or order a [pre-flashed Edison](https://enhanced-radio-devices.myshopify.com/products/intel-edison-w-jubilinux).  If you buy a preflashed Edison, you can skip the "Flash Edison" portion of these docs when you go to build your rig.</br></br>
* [**Explorer Board**](https://enhanced-radio-devices.myshopify.com/products/900mhz-explorer-block-pre-order) is a custom-designed board that allows an Edison to serve as a bridge from wifi or bluetooth to a 915MHz protocol.  Basically, it has the communications built in to talk between the Edison and your pump.</br></br>  
* [**Nuts and Bolts**](https://www.sparkfun.com/products/13187) are needed to keep your Edison attached to your Explorer Board.  Without these little nuts and bolts, your Edison will come loose, your loop will stop and you will be sad.  Don't be sad.  Check your nuts and bolts periodically after you have built your rig to make sure they stay tight.</br></br>

* **Lipo Battery** is the portable power for your rig.  If you want a mobile rig, you'll need a lipo battery.  There are smaller batteries such as this [Adafruit 2000mAh battery](https://www.adafruit.com/products/2011) or [SparkFun 2000mAh battery](https://www.sparkfun.com/products/8483) will fit in smaller cases, but will also not last nearly as long.  (The Adafruit version of the 2000mAh battery is the version that will fit in oversized tic-tac containers and is most common for people looking for smallest rig-size.)  The 2000mAh battery will last a little over 12 hours on a standard OpenAPS setup.  The [25000mAh battery](https://www.adafruit.com/products/328) will add about another 4-5 hours to the battery life for the day, which may be worth the slightly larger size it brings.  A note about lipo battery ordering...lipo batteries cannot be shipped by themselves (you must order them with some other piece of equipment, even if it is just a cable) and are very difficult to find in local stores if your battery's wires break. Plan ahead with this information in mind.  A backup battery is a great idea.</br></br>

* [**Charging block**](https://www.amazon.com/Cellet-Powered-Charger-iPhones-Smartphones-/dp/B00FE8WFCO) can be used with the cables below to charge your rig's lipo battery overnight.  You can also re-purpose an old iPhone charging block if you have one of those laying around.</br></br>

* **USB-microB cables** (two of them) are needed to complete the initial setup of your rig.  You may already have workable USB cables from other devices around your house (android phones, playstation controllers, dexcom receivers, etc). The cables don’t have to be a certain length either, [3-ft long cable](https://www.adafruit.com/products/592) or [6-inch long cable](https://www.adafruit.com/products/898) can both work fine.  You just want to make sure you get a good data cable.  Cheap cables may cause you to not be able to communicate with your rig and make you want to pull your hair out.</br></br>

****************
# Carrying case

Tally Gear

Tic Tac box

Staples box

other boxes

****************
# Pebble watch

There are two watchfaces for Pebble that integrate easily with OpenAPS.  

* SkyLoop
* Urchin
