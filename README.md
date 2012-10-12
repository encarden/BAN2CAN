BAN2CAN
=======

This objectis is 4 feed Canvas LMS from Sungard Banner 

Installing Canvas-Banner Integration

This package is running on banner 8, Oracle 11g and in a sun Solaris server, if the environment is different minimal changes will needed to work fine.
You should have a ban2can user on your server in our case the home of this user is /users/ban2can.
Create a /users/ban2can/data folder.

Then create a /users/ban2can/product folder an copy tar file on this folder and then untar it.
To install the package use the following command using baninst1 user (first on your devel instance).
sqlplus baninst1@DEVL @install
Password: XXXXXXX 

Create following Web Tailor Parameters on SSB:
LMS_ACT  87654
LMS_AT	XXXXXXXXXXXXXXXXXXXX
LMS_GS	0
LMS_URL	https://your.test.instructure.com
 
where

LMS_ACT is your account number
LMS_AT is your access token
LMS_GS is the time in minutes between sync processes, we use 5 in production and for test you can use 0.
LMS_URL is the canvas url, I recommend use test instance first.

To start the daemon on sqlplus or toad use:
Call ban2can.canvas_banner_int.p_start_d();

To see the status:
Call ban2can.canvas_banner_int.p_status_d();

To stop the daemon,
Call ban2can.canvas_banner_int.p_start_d();

That is it, enjoy your Canvas feeding.
