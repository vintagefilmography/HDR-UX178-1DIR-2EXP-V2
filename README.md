# HDR-UX178-1DIR-2EXP-V2

This is the release build for HDR 2 exposures and one directory.
The High Definition HDR app was made specifically to work with the Imagingsource UX178 camera.  
This particular camera has a double trigger requirement i.e. the trigger has to be applied twice to set the new exposure.  
Thus, for HDR, 4 triggers are required to get the low and high exposure images.  
The rest of it is the same as reqular Hawkeye HDR posted in the repositories here.  
Note: Hawkeye board V12 or higher and MSP FW mod are required for proper HDR operation to provide four camera triggers for a single external trigger. 
https://github.com/vintagefilmography/msp430/blob/master/freq_gen_12_hdr_turbo_ux178_v1.zip  
This is the windows software that runs hdr on the Wolverine scanner that has the Hawkeye mod.  
The software is written in Visual Basic and it connects to the camera and waits for the image ready event.  
After the event is receied the sw stores the first image at normal exposure then lowers the camera exposure for the second image.   
When the second event is received it stores the second image.   
The process then repeats.  
This single directory version stores the images into a single directory in oppose to two.  
The directory path is set by the Path button.   
The image numbering will be sequential. Odd numbers for bright images and even for the dark images.
The hawkeye MSP430 firmware has a mod to trigger the camera 4 times for each external trigger.  
To run the sw go to the  
.../bin/Release 
dir and run the HDR1.exe file.  
The Device Settings window will pop up.  
Select the device and resolution as required and click OK.  
The Device Window will close and the app window will pop up.  
Select the destination directory  clicking on the Path button.    
Then click on Trigger buton a few times.  
It will go from red to white. Leave it white for free run.  
Click Start.  
The camera preview will be displayed in the preview window.  
Click on ZoomIn and ZoomOut buttons and set the zoom as needed.
Click on Start button.
Click on Settings button.  
The familiar camera settings will pop up.  
Set the color, partial scan etc  
Turn auto exposure on the exposure tab.
Set auto reference on the exposure tab for bright image. Should be overexposed for HDRto work properly.  
Turn auto exposure off. 
Click on OK.  
The window will close. 
Click again on the Start button.
It should go white.  
Click on SaveConf button to save the device settings.  
Make sure the Start buttoon is not active, otherwise an exception will pop up.  
The next time when you run the app you can use the LoadConf to retrieve the settings.  
The settings are stored in device_state.txt file in the same directory where the app resides.  
Select the bit depth by clicking the Bit64 button. Do not do this if you want to leave the default 32 bit.
The Bit64 button will turn red indicating 64 bit mode.  
Make sure that the Start button is not active when you are doing this otherwise teh app will crash.  
Essentially the start botton starts the live display and the bit depth and soem other camera critical settings can not be changed in Live mode.
Hit Load Exp to load the exposure value from the camera to the app.
Hit Disp Exp to see the actual exposure. This can be done at any point during scan.
Most of other settings can be changed in Live mode however.  
The SaveTiff button also can be set in Live mode.  
If active it will switch from default Jpeg format to Tiff.  
Click on Exp Dec arrows to set the exposure decrement in F stops. You can also enter it directly by typing in a  
decimal number. For example 3.1 translates into 3.1 stops  exposure decrement or 1/(2^3.1) multiplier.      
Around 3 stopsseems to work good.  
Click on Trigger button to activate external trigger.  
Click on ImgSave.  
It should turn red.(Keep an eye on this button when testing.  
It could flood your drive with images if trigger is left on FreeRun.  
Click on Start Button.  
The app is now ready for images.  
Run the scanner.  
Note, once the scan process is complete you can use an app to convert the high and low images into HDR.  
The app that seems to work very can be obtained from the following site: http://enblend.sourceforge.net/ Download enfuse and use the enfuse-hdr.bat (included here in the repository) script to run combine the images.  
Alternatively, use the enfuse GUI. It is easier to use and it accepts many images.
There is also a GUI version of it that is easier to use.
http://software.bergmark.com/enfuseGUI/Main.html
There is also another app that might be worth looking into.
https://skylum.com/aurorahdr  

Additional notes:  
If tiff file transfer, is unreliable (occasional dropped frames), switch to jpeg. The difference is not perceptible not even on a large screen.The jpg files can be converted to a combined HDR tiff file, if needed, with Enfuse.

Can use basic script batch file to process 2 exposure HDR files in separate folders using Enfuse v4.2.
http://enblend.sourceforge.net/index.htm  
   
To process the files/frames use EnfuseGUI v2.1.3, this gui uses Enfuse v4.0 and makes the process very simple.
http://software.bergmark.com/enfuseGUI/Main.html

If one wanted to use the later command line Enfuse v4.2, there are included Droplets v0.2.1 by Erik Krause, there is also a newer v0.4.2 available, with added extra options like EXIF copy feature (not needed for this simple application). Because some changes have been made to Enfuse over time, these Enfuse droplets no longer function as they are, but with a very minor one line change, they still work.  
Change line from:- set enfuse_additional_parameters= --wExposure=1 --wSaturation=1 --wContrast=0  
To :- set enfuse_additional_parameters= --exposure-weight=1 --saturation-weight=0.2 --contrast-weight=0 --hard-mask  
http://www.erik-krause.de/enfuse_droplet.zip  
https://groups.google.com/g/hugin-ptx/c/3VuXOjVqZPk  

The TestBW button can be used to gather the image transfer process stats. If the stats show dropped transfers then  
your system is probably slow or you have a USB speed issue or poor quality USB cable or a few cables patches together.
Try running the performance tests on your computer. If it all fails then try to scan with Jpeg instead of Tiff.  
Possibly switching from 64 to 32 bit may help. 

