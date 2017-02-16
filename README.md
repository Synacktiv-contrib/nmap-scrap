# nmap-scrap

`nmap-scrap` is an HTTP exploration utility based on Nmap XML outputs. This tool aims to address discovering issues when dealing with large scopes by parsing Nmap XML outputs and extracting only required information.


# Installation

## Python dependencies

Please not at the time of writing this file, a feature only available on python-requests upstream was required but not provided with pypy bundled version.

	pip install -r requirements.txt

## massws

	TODO

# Usage

A typical workflow looks like:

	$ nmap -oX google.fr.xml google.fr
	$ ./nmap-scrap http google.fr.xml 
	[*] Parsing file /tmp/google.fr.xml
	[*] Found 6 http services
	[!] Launching 20 threads
	[=======================] 100%
	HTTP 404
	========

	  * http://par21s05-in-f131.1e100.net/ (1557 bytes)

	HTTP 301
	========

	  * http://google.fr/ => http://www.google.fr/ (218 bytes)
	  * http://216.58.204.131/ => http://www.google.com/ (219 bytes)

`nmap-scrap` provides some nice options for saving output and taking screenshots:

	$ ./nmap-scrap http -h
	usage: Nmap helper http [-h] [--start START] [--screen] [--save]

	optional arguments:
	  -h, --help     show this help message and exit
	  --start START  The start HTTP page
	  --screen       Takes a screenshot of each http service
	  --save         Persistent output

