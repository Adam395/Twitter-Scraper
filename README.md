# Twitter Scraper and Exporter  
  
## Overview
The Twitter Scrape applet was designed by Beta Group from the DSI11 NYC cohort (Max Mazel, Najiha Boosra, and Adam Cohen) to automate multiple Twitter queries to expedite data collection.
  
The applet is called as a single line, 'get_dataset()' with no input, and either pulls a pre-defined dictionary or list, or generates all required variables internally.
  
To use the applet, the user **MUST** define either of the following:  
  
1) A list called "query_list" composed of strings (a sample is included in the code cell)  
**OR**  
2) A dictionary called "custom_params" in the same format as the sample in the code cell.  
  
The applet will otherwise prompt you for any additional information.  
  
It will automatically generate the export directory for the .csv if you opt to export.

## CHANGE LOG:  
## V.1.05:  
Optimized master function to run through fewer if-else statements and not present prompts in illogical order. Query_start output column is now a datetime object instead of a string.
  
### V.1.04:  
Added custom date configuration switch and support for multiple custom start points in parameter dictionary.

### V.1.03:
Revised input order when function is initally run, added file overwrite checks and flow. 

### V.1.02:
Turned off limiters used for faster debugging.

### V.1.01:  
Simplified some loops and corrected a typo in the output dataframe.  
  
### V.1.00:
Initial implementation.  
  
## Special Thanks
Danielle Medellin of DSI11 NYC, who implemented the inital version of the custom parameter dictionary code and provided substantial testing help.
