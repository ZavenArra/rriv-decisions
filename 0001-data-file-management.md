# Retrieval and Storage of Data Files

* Status: proposed
* Deciders: @ZavenArra, @jakehosen, @pleocavee
* Date: 05/02/2021

Technical Story: 
https://github.com/WaterBearSondes/rriv-cli-client/issues/1
https://github.com/WaterBearSondes/rriv/issues/48

## Context and Problem Statement

Logged sensor data exists on CSV files on the RRIV device, and we need a way to easily retreive these files.  Retrieved data should be stored locally, easily available to analysis tools, and also optionally uploaded to a remote storage. Operators also want to know which data are new, verses data that have been left on the RRIV device.

## Decision Drivers <!-- optional -->

* Users should not work directly with CSV files.
* Users should not have to work directly with transfering files from the SD card.
* Users should be able to review new data for QC purposes
* Leaving files on the RRIV device as a temporary data backup should be allowed without adding noise to future retrievals.

## Adopted Design

### Transmission
A CLI command will be implemented to retrieve data with the following specification:

**pull-data** [--all]

A RRIV device will respond to this command by streaming all data CSV files since the last retrieval to the USB serial port, following a to-be-estabilished protocol for signaling the beginning and end of each file to the CLI client, as well as the file names.  Specifying --all results in *all* data CSV files stored on the device being sent.  After completion of data transmission, the RRIV device will update a variable *last_pull* in the EEPROM with the timestamp of retrieval.  This variable is used by the next call to pull-data to identify new data files.

### Reception

After initiating pull-data, the CLI client will recieve each CSV file as it is tranmitted, and store them separately in a folder named .data, within a subfolder named by the site name set on the currently attached RRIV device.  Files will be saved using the filenames transmitted by the RRIV device.  CSV data files will be marked as read only.  All data will also be ingested into a local SQLite database, for easily retrieval by local analysis tools.

### Analysis

The RRIV client will expose an http endpoint for querying data stored in the SQLite database.  This data will be filterable by get parameters such as site name and date range. 



## Decision Outcome

Chosen option: We identified as design above as the appropriate initial design for data file management, which had no competing designs.

