					    INSTRUCTIONS FOR "Variable and Reference Star Locator (VaRSL)"					
         				 		          -By Caleb Derochea						
																
The work in this code is based on the paper "Differential Ensemble Photometry by Linear Regression" by Kevin Paxson, published in 2010 in JAAVSO Volume 38.

INTRODUCTION:

	The purpose of this code is to allow amateur astronomers to find possible variable stars using raw data via ensemble photometry. The code was initially made with the program MaxIm DL in mind, but there is a workaround for people who use other programs (which I'll go over later in this readme file). This code will not only aid those doing research on variable stars but will also aid those who wish to do photometry in a patch of sky where AAVSO has no listed reference stars. This can be helpful in research such as candidate exoplanets, reference stars, variable stars, quasars, etc.

	In this file, I'll be giving you a step-by-step process on how to set up a CSV file from raw ensemble photometry data to find reference stars--and possibly variable stars--among the stars you chose within the field. But first, I'll let you use files of my own, courtesy of the Bridgewater State University Observatory, so that you may gain a better understanding of how you can utilize this code. 

As a side note, my email is provided at the end of this document if there are any questions about anything I go over in this file.



BEFORE WE START => INSTALLATIONS:
																
	Before we start, it is important to install PyCharm if you have not already. The community version should be sufficient. 

	You should also install the packages we'll be using for this data analysis. If you have not yet installed this to your computer, please use the following URL to help in setting it up for your device:

LINK: https://packaging.python.org/en/latest/tutorials/installing-packages/

There are also more resources to look up for help if the contents on the website are not helpful.

The following is the list of packages that need to be installed:

	+ numpy
	+ scipy
	+ matplotlob
	+ json
	+ pandas
	+ tkinter
	+ statistics
	+ math
	+ seaborn

Once you have the packages installed, we can start running the code!



HOW TO RUN THE CODE:
																
	Before you have the VaRSL file opened in PyCharm, you want to make sure that the CSV files are in a file location that is easy for you to find. From then, you may then start by running the code by clicking the green play button in the upper right-hand corner. 

	(Note for Mac and Linux users: you may have to replace the lines of code for the GUI that is being used. If I get emails regarding this issue, I will provide another .txt file with the lines of code needed to replace it.)

	After a few seconds of running the code, a GUI should pop up with a similar layout to File Explorer. If the GUI does not appear, look for a new icon in your Taskbar and click it to open the GUI. Then, navigate through it to get to the CSV files I provided. Open up the "All Nights In One" file.
	
	If the "All Nights In One" file takes too long for your computer to process, then try selecting any of the other nights provided. 
	
	After a few seconds, the GUI will allow you to select another file. For this one, select "Vizier Mags." That is a file of the cataloged magnitudes of each star from VizieR which can be found using the Aladin software... which I'll go into more detail about later.
	
	A plot of the data should pop up. (Keep in mind that this sort of data analysis in Excel would probably take a few hours for a person to do with this amount of data, and we have just done it IN SECONDS!) Analyze the graph. You'll notice that you can move it around and zoom in. While you're looking at it, you'll notice that the point labeled "1" seems to be the farthest away from the line of best fit. THAT is the data from the variable star TZ Aurigae. Let's just focus on that star for the time being. 

	Now, exit out of the GUI. You'll notice that there were a few things printed in the counsel area. You may browse through it to see what it is we just did with the original CSV file. At the very bottom of the counsel, you'll notice that there is a prompt for a user input. This input allows you to omit as many of the stars you feel are variable from how far they are from the line of best fit, and then it asks you which stars you feel should be omitted. Type the number "1" for TZ Aurigae and then press the Enter key.

	You'll get another plot without the points labeled. This is to check to see if the other plot points are a reasonable distance from the line of best fit. The distance will depend on a potential error in the equipment as well as a variation in the magnitude of a star either throughout the observation period (or since the magnitude was cataloged), along with a few other things. We want the stars as close to the lines of best fit as possible.

	Now exit the GUI.

	Another graph like the first one will appear, but this time with small error bars. Zoom in until you can see the error bars clearly. Move along the line of best fit and see if there are any outliers beyond the error bars. Jot down (or type in a .txt file) the numbers of the points which have error bars that do not cross the line of best fit. Then exit out of the GUI and rerun the code.

	Follow all of the steps again up to the user input. Instead of inputting "1" like last time, you will be inputting the numbers of the data points you wrote down with a space in between each number (e.g., "5 11 12 1 7 9 10" [excluding the quotation marks]). For this, the order does not matter.

	After hitting enter, the GUI of the graph will pop up and you'll see that all of the points you entered have been omitted. A quick look at the R^2 value in the counsel should be a lot closer to a value of 1 than it originally was, which means there are fewer outliers in the data. By writing the whole list of numbers for the stars down on a sheet of paper and crossing out the numbers you have omitted, you'll be left with the numbers for the most stable stars you've picked. This will allow for your next run-through of ensemble photometry of the same field (with only using these stable stars) to result in a more accurate light curve of your data as well as a higher percentage of certainty in your analysis.

	Viola! You have now successfully used The Reference Star Finder! I am aware this is a lot of information, so please feel free to reach out to me via my email at the bottom of this file for any comments, questions, or concerns. 


Please look at the guide for the Aladin software below so that you may find cataloged star magnitudes for your own research.



ALADIN SOFTWARE... HOW TO GET CATALOGED MAGNITUDES OF STARS:

	The way I was able to find out the magnitudes for the stars I wanted was through a program called Aladin (not to be confused with Aladin Lite, which is an online version of the same software, but with a different layout). 

	Use the link below to download Aladin to your computer.

	LINK: https://aladin.u-strasbg.fr/java/nph-aladin.pl?frame=downloading

	Once you have Aladin installed and opened, you'll notice that there's a file navigator system on the left side of the screen. This is what you want to navigate for the files:

Collections => Catalog => VizieR => II-Photometric Data => APASS - AAVSO Photometric All Sky Survey (APASS) DR9 (Henden+, 2016)

NOTE: APASS is the catalog that worked best for me when I tested this for TZ Aurigae, but this may not be the same for the field you may be studying. This would then require some searching through the different possible catalogs. I'd suggest staying within the "II-Photometric Data" file when looking for a catalog since the photometric data is what you want. 

	In the "Command" tab at the top of your screen, you want to put the Right Ascension and Declination of your target. This will bring you to your location of interest. From there, locate the main target you are looking for, and then select the reference stars you used for your photometric data. The RA and Dec should be in the following format: 07:11:35.02325 +40:46:37.1480.

	Once you click on one of the stars, you'll notice that below the main interface is a table. Each row corresponds with each star that you pick. To find the magnitude that you want, look for the column that says "Vmag." (You may have to use the scrolling feature at the bottom to find the column you want.) Jot down these numbers either in a .txt file or on a piece of paper.

	One thing to keep in mind when doing your own data is that the CSV file that contains expected (cataloged) magnitudes should:

	A) Have the exact number of stars that you used in your photometric calculations, including the target star.

	B) You need to start from column A like how it is in the "VizieR Mags" file

	C) You have to only have it in the second row or else it will not be read by the code. 

	D) Absolutely nothing else should be in the CSV file or else the code will not read it properly.

(Basically, make sure none of the stars you are using are missing and use the "VizieR Mags" file as a reference.)


	With that being said, if you feel confident enough at this point, you may start using this code for your own data! Otherwise, you may go through the instructions again to attempt to have a better understanding of what's going on. Feel free to go back to this whenever you need to (life is open notes anyway). Also, feel free to reach out to me via email if you have any other questions which were not answered here in this ReadMe file. HAPPY OBSERVING!



My Personal Email: calebderochea280@gmail.com

My School Email: cderochea@umassd.edu

