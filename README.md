# Sierra-Clancy-request-export

These scripts may be used as a two part process using Sierra APIs to identify items requested from off site repository (Clancy) and create a file containing item barcodes for submission to the Caiasoft API.  

<b>Parts</b>
* Part 1: getOffsiteRequests.py generates a JSON file with hyperlinks referencing Sierra item ids
* Part 2: getItemBarcodes.py generates a pipe-delimited text file containing barcodes for the items

The complete setup would be to create a cron job that calls these scripts, and then executes a system command to submit the file of barcodes to Caiasoft via their API. 

<b>Usage: </b>
<pre>
$ python getOffsiteRequests.py
$ python getItemBarcodes.py JSONfilename AM|PM
</pre>
* Run these at some point during the day and again at the end of the day to capture all requests for that day. 
* Submit the resulting file of barcodes to Caiasoft via their API

<b>To re-use this code</b>
* Download the two python scripts and local_config.template 
* Rename the local_config.template as local_config.cfg 
* Edit local_config.cfg:
* ... insert valid entries for [sierra] stanza: Sierra Host Name, API Key, and API_SECRET
* ... insert valid paths in [filepaths] stanza. Change institution prefix as appropriate.
* Edit the path to local_config.cfg in getItemBarcodes.py and getOffsiteRequests.py
* Change the location id number in the JSON query section of getOffsiteRequests.py to match the desired location
  
Full paths are stored in a config file to accommodate running the shell scripts that invoke these Python script as cron tasks. Shell scripts, logging, file management, and the Caiasoft API are outside the scope of this repository.

Sierra is an integrated library system from Innovative Interfaces. (https://www.iii.com/)
Caiasoft is an off-site inventory management system (http://www.caia-solutions.com/?serv=caiasoft)
