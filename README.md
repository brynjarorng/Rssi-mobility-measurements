# Real world mobility RSSI dataset (2.4GHz)
This is a cleaned dataset containing received packets with RSSI, sequence numbers and time of reception. It contains a total of 49047 usable packets over a duration of 247 minutes.

## Data collection
The radios used in this data collection were a pair of Texas Instruments CC2650 Launchpad MCUs. The radios were configured to use the 2.4GHz band in IEEE 802.15.4 mode using the Smart RF studio 7 software from TI. All collection was done using IEEE channel 11 which has the freequency of 2.405 GHz.

The transmitting radio was always stationary and facing the same direction while the receiver was carried and kept pointing towards the transmitter at all times. Line of sight was maintained all times between the two radios.

The transmission power of the transmitter was altered in order to record packets that dip under the -80DB threshold, where previous research has shown the PRR rate drastically falls, while not running out of space to move in.

The mobility patterns were simple as the receiver was moved towards and away from the transmitter with intermitten stops. The change in direction was done as randomly as humanly possible in order to collect as diverse data as possible. The maximum distance between the radios was approximately 60m while the minimum distance was around 0.1m. The speed of the mobility of the receiver varied between being stopped and at maximum 5km/h. 

The surface material in the copenhagen measurements is grass and can be seen below **ADD FIG** while the surface material in the data collected in iceland is mostly sand with small rocks.

A detailed description of the dataset and data collection methods can be seen in **Link example of the usage of the data to the thesis**.

## Data
All failed receptions as well as data received from other radios such as wifi networks and bluetooth has been removed to ensure privacy and to keep the dataset clean.

The data is stored in folders by the date of capture. The filenames of each file represent the exact configuration of the transmission power. Each file begins with `log_` and then follows one of three cases:

* `pXX` - transmission power increased by `XX` db
* `mXX` - transmission power decreased by `XX` db
* `0` - transmission power offset set to 0db

Each file then contains the following content which is separated by the ` | ` symbol:

* Timestamp of capture using the local time
* Decimal length of the packet, always `08`
* sequence number of packet captured
* Custom packet payload, always `aa bb cc dd ee ff`
* Received RSSI value

An example: `13:41:34.783 | 08 | 0011 | aa bb cc dd ee ff  |  -39`

There can also be found a short capture containing the measured background RSSI that was taken just before each data capture session. This was recorded by the transmitter in the same position as the transmission was done.

