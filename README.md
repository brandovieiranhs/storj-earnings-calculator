# storj-earnings-calculator
Earnings calculation script for Storj V3 storagenodes

Prerequisites

Python 3.2 or newer is required to run this script.

This script was tested on Windows 10 and Linux, with Python 3.7. Other OS's and versions will likely also work.

Some NAS systems may have versions of python 2 and 3 installed on the same system, try running the script with python3 instead of python. On QNAP systems you may need to install Python 3 from the store and run /etc/profile.d/python3.bash before running the script. For Synology it should default to python 3 if you run DSM 7 or higher.
Warning

Never access node databases over a network connection like SMB, NFS etc. SQLite uses file locking to prevent database corruption and isn't reliable over these types of connections. So run this script locally or over iSCSI. If you want to run it on a different system anyway, stop the node and copy the satellites.db, bandwidth.db, storage_usage.db, piece_spaced_used.db, reputation.db, heldamount.db and pricing.db to your local system, and run the script from there. If you are running Docker on Windows or MacOS, this implementation uses network storage in the backend. To use the script with such a setup, stop the node, copy the satellites.db, bandwidth.db, storage_usage.db, piece_spaced_used.db, reputation.db, heldamount.db and pricing.db to a different location and run the script from there. Running the script on docker nodes on these OS's while the node is using it could lead to corruption of the database, which will kill the node.
Usage

Earnings for current month:

python earnings.py /path/to/storj/data

Note: If you omit the path it will look in the current working directory.

Earnings for previous months:

python earnings.py /path/to/storj/data 2023-03

This is based on ReneSmeekes storj_earnings python script: https://github.com/ReneSmeekes/storj_earnings
