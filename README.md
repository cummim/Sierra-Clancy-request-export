# Sierra-Clancy-request-export

These scripts may be used as a two part process using Sierra APIs to identify items requested from off site repository (Clancy) and create a file containing item barcodes for submission to the Caiasoft API.  

<b>Parts</b>
* Part 1: getOffsiteRequests.py generates a JSON file with hyperlinks referencing Sierra item ids
* Part 2: getItemBarcodes.py generates a pipe-delimited text file containing barcodes for the items

The complete setup would be to create a cron job that calls these scripts, and then executes a system command to submit the file of barcodes to Caiasoft via their API. 

<b>Usage: </b>
<pre>
$ python getOffsiteRequests.py
$ python getItemBarcodes.py JSONfilename
</pre>
* Run this at the end of the day to capture all requests for that day. 
* Submit the resulting file of barcodes to Caiasoft via their API

<b>To re-use this code</b>
* Download the two python scripts and local_config.template 
* Rename the local_config.template as local_config.cfg and insert valid entries for Sierra Host Name, API Key, and API Secret.
* Edit in code file name prefixes in getItemBarcodes.py so they are appropriate for your institution
* Change the location id number in the JSON query section of getOffsiteRequests.py to match the desired location
  
  
Sierra is an integrated library system from Innovative Interfaces.
