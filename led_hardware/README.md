# Neodome lighting hardware and network infrastructure setup

Neodome uses 15 **IRA boards** that each control 5 addressable LED strips. The [IRA](https://github.com/phyx-be/IRA) is a printed circuit board with an ESP32 to control LEDs (or other lighting equipment). The PCB is designed for a 5 or 12V DC supply voltage and has outputs for WS2812-style adressable LEDs and optional DMX. Because of the size of neodome, 12V power is used.

An **IRA node** is an electrical juncion box housing an IRA PCB (to make it somewhat wheater proof). The node has a black/red wire pair for the 12V DC supply and 5 wire triplets with wheather proof connectors for connecting an LED strip. Every box is marked with the node number (926-930) on the front and back. An IRA node is mounted in the intersection of 6 trusses on the *neodome* and feeds the LED strips of 5 trusses. The LED strip of the 'missing' truss is fed by an adjacent IRA node.

By default IRA runs Micropython and NATS is used to transfer commands over wifi. For neodome the IRA boards are flashed with standard WLED firmware. Future plan is flashing WLED with the IRA_NATS usermod: https://github.com/kavers1/WLED/tree/NATS-IO

## Bill Of Materials
* LED strips: type, lengths?
* 15 IRA nodes
* 230V AC to 12V DC power supplies
* 12V DC distribution cables: lenght?
* Lots of WAGO connectors for connecting the power supplies to the distribution cables and the distribution cables to the IRA bnodes
* Wifi AP 

## Wifi
The Wifi AP is an Aruba AP-105 access point running OpenWRT. It is configured to run standalone on PoE without an ethernet uplink and supplies reserved IP-addresses to the IRA nodes.

## WLED on IRA

### Network Parameters

| IRA Node name         | IP address | ESP wifi MAC      |
|-----------------------|------------|-------------------|
| wled-Dome-Node-916    | 10.5.5.16  | C8:2B:96:8A:54:1C |
| wled-Dome-Node-917    | 10.5.5.17  | C8:2B:96:8B:15:98 |
| wled-Dome-Node-918    | 10.5.5.18  | C8:2B:96:8B:16:F4 |
| wled-Dome-Node-919    | 10.5.5.19  | C8:2B:96:8B:17:10 |
| wled-Dome-Node-920    | 10.5.5.20  | C8:2B:96:8B:17:64 |
| wled-Dome-Node-921    | 10.5.5.21  | C8:2B:96:8B:17:94 |
| wled-Dome-Node-922    | 10.5.5.22  | C8:2B:96:8B:16:D4 |
| wled-Dome-Node-923    | 10.5.5.23  | C8:2B:96:8B:16:C4 |
| wled-Dome-Node-924    | 10.5.5.24  | C8:2B:96:8B:16:D8 |
| wled-Dome-Node-925    | 10.5.5.25  | C8:2B:96:8B:15:88 |
| wled-Dome-Node-926    | 10.5.5.26  | C8:2B:96:8B:16:D0 |
| wled-Dome-Node-927    | 10.5.5.27  | C8:2B:96:8B:17:5C |
| wled-Dome-Node-928    | 10.5.5.28  | C8:2B:96:8B:15:94 |
| wled-Dome-Node-929    | 10.5.5.29  | C8:2B:96:8B:16:F8 |
| wled-Dome-Node-930    | 10.5.5.30  | C8:2B:96:8B:17:14 |

The DHCP configuration of the wifi access point has IP reservations mapping the MAC to the assigned IP address for every IRA node.
