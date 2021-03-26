<h1 align="center"> 

![Slips_logo](slips_logo.png)
<br>
Slips v0.7.1
</h1>


<h3 align="center"> 
Behavioral based Intrusion Prevention System<br><br>

Slips documentation is [here](https://stratospherelinuxips.readthedocs.io/en/latest/) <br>

[Features](#features) — [Slips in action](#slips-in-action) — [Running Slips in a Docker](#running-slips-in-a-docker) — [Authors](#authors) - [How to contribute](#how-to-contribute)
</h3>

## Features

Stratosphere Linux IPS, shortly Slips, is a Python-based intrusion prevention system that uses machine learning to detect malicious behaviors in the network traffic. Slips was designed to focus on targeted attacks, to detect of command and control channels and to provide good visualisation for the analyst. Slips is able to analyze real live traffic from the device and the large network captures in the type of a pcap files, Suricata, Zeek/Bro and Argus flows. As a result, Slips highlights suspicious behaviour and connections that needs to be deeper analyzed. 

Slips is a modular software. Each module is designed to perform a specific detection in the network traffic. Current version of Slips contains following modules:

|   module  |   description | status |
| ---| --- | :-: |
| asn | loads and finds the ASN of each IP |✅|
| geoip | finds the country and geolocation information of each IP |✅|
| https | training&test of RandomForest to detect malicious https flows |✅|
| port scan detector | detects Horizontal and Vertical port scans |✅|
| threat Intelligence | checks if each IP is in a list of malicious IPs  |✅|
| timeline |  creates a timeline of what happened in the network based on all the flows and type of data available  |✅|
| rnn-cc-detection | detects command and control channels using recurrent neural network and the stratosphere behavioral letters |✅|
| VirusTotal | module to lookup IP address on VirusTotal |✅|
| flowalerts | module to find malicious behaviour in each flow. Current measures are: long duration of the connection, successful ssh |✅|
| blocking | module to block malicious IPs connecting to the device |⚠️|


Slips has its own console graphical user interface called Kalipso. Kalipso summarizes the detections performed by Slips in colorful graphs and tables.

Complete documentation of Slips internal architecture and instructions how to implement a new module is available here: https://stratospherelinuxips.readthedocs.io/en/latest/

## Slips in action

![](slips-kalipso.gif)


## Running Slips in a Docker

The easiest way to run Slips is inside a docker. Current version of Slips docker can analyze network captures (pcap, Zeek flows, Argus flows, etc.), but it is not able to analyze real live traffic. How to use Slips docker from DockerHub:

	mkdir ~/dataset
	cp <some-place>/myfile.pcap ~/dataset
  	docker run -it --rm --net=host -v ~/dataset:/StratosphereLinuxIPS/dataset stratosphereips/slips:latest
  	./slips.py -c slips.conf -f dataset/myfile.pcap
  	./kalipso.sh


## Authors

**Main author:** Sebastian Garcia. sebastian.garcia@agents.fel.cvut.cz, eldraco@gmail.com. 

**Contributors:**

- Kamila Babayeva
- Ondrej Lukas
- Alya Gomaa
- Veronica Valeros
- Frantisek Strasak
- Dita Hollmannova
- Elaheh Biglar Beigi
- Maria Rigaki 
- kartik88363
- arkamar
- Alya Gomaa

## How to contribute
All contributors are welcomed! How you can help?

- Run Slips and report bugs and needed features, and suggest ideas
- Pull requests with a solved GitHub issue and new feature
- Pull request with a new detection module. The instructions and a template for new detection module [here](https://stratospherelinuxips.readthedocs.io/en/latest/).
