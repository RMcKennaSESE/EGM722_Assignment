EGM722 – Programming for GIS & Remote Sensing

NBA Map- How-to guide
Ronan McKenna
B00907678

1.	Introduction

Geography and basketball are two subjects which find themselves surprisingly intertwined. One of the more notable inspirations for this project was the work of Kirk Golsberry, a cartographer and data visualization specialist who has gone on to write for major publications such as ESPN and Grantland as well as publishing a book, Sprawlball (2019), on how space has driven change in how the game is played in the last decade. While the specifics of shot charts and what True Shooting % means aren’t explored here, it’s nice to give a nod to past work. The other main influence on this project is the work of Joey Loose (u/jloose128 on reddit) who has produced maps of the NCAA tournament each year. These maps, which display the closest US county to each team, at each stage in the tournament are the biggest source of inspiration for the work done here.
This code in this repository is a Jupyter notebook intended to create and display a map of the USA containing point data for teams from the National Basketball Association. Data from US counties will also be incorporated and displayed according to the nearest NBA team. The last section of the code in this notebook will create and save bar charts to your working directory. Running this code will create a map displaying all 30 teams in the NBA as of writing this document.
 

The code will then use functions that will modify the data used and recalculate the map, essentially eliminating teams from the title race.
 

To briefly explain this new map, teams still in contention have a red marker with a basketball on it, teams that have been eliminated are displayed with a blue marker with a fish on it (they’ve gone fishing).


2.	Installation guide

Repository for the code can be found here: https://github.com/RMcKennaSESE/EGM722_Assignment 

 

Table 1 is a description of the contents of the repository.


Table 1 Contents of repository and description
Name	Description
Charts 
	Folder which will contain any images of charts saved when running the code. Contains example charts.
Data-files 
	Location of all data files used for this code, including shapefiles, .csv files and GEOJSON files.
Maps 
	Folder which will contain any maps saved when running the code. Contains example maps.
.gitignore - 
	Standard file telling git which files to ignore.
Arena_Map_Project.ipynb 
	Notebook containing the code needed to run this project.
LICENSE 
	Licence file for github code. The licence used for this project is an open MIT licence.
README.md 
	Setup/installation guide for software.
Scribbles.txt 	Plain text file containing notes taken while coding.
		
Installation instructions will be written presuming user has already set up git and a conda environment (in this case, the egm722 environment).

Step 1. In order to run the code on your own machine, you will first need to fork the repository and clone it to your own directory.

 





Step 2. Make sure that on the next screen the option for Copy the main branch only is unchecked, then click Create fork.

 















Step 3. Once the repository is forked it will need to be cloned to your computer. To do this open up github desktop version.
 
















Go to File->Clone repository or Ctrl+Shift+O to open the clone repository menu. You should see something like.
 

Select a path to save the repository to, remember where, as it will be needed for the next step. Click Clone to clone the repository. Once the repository is finished cloning, select the option, For my own purposes when asked how you are planning to use this fork, this will create an independent, local version of the repository that will not contribute to the upstream branch if done correctly.








Step 4. Now that you have a local copy of the repository saved to your computer the next step is to open this as a jupyter notebook. Open anaconda navigator and make sure you are in your egm722 environment.

 

Step 5. The simplest way to launch notebook from here is by clicking on the Launch button below the jupyter notebook icon. If that doesn’t take you to the correct directory, jupyter can be opened from a command line prompt. Open a command window and enter the following line:
 
Note: replace E:/ with the location of your working directory.

 

If you get an error here, check your syntax and make sure the command is entered correctly. Successfully running this command will open jupyter in your default browser.
Step 6. From here navigate to where your cloned repository is and select the file named ‘Arena_Map_Project.ipynb’ to begin running the code.
 


3.	Methods/code guide

This section will walk through the code and explain the processes and the methodology. The notebook is written with the intent of being straightforward to read and interpret and should be considered the better source of information.  There is no complex analysis undertaken here, this code is meant to produce a map that is fun to pore over.

3.1.	Recalculating the map

The maps produced by this code can be modified and changed to reflect the current state of the NBA regarding which teams are still in contention for the NBA title. Contender status was checked by appending a column to the Arenas dataframe called ‘In Contention’ with a boolean value of ‘True’ or ‘False’. This status was then altered by calling the function cancun().
 

The function takes a string argument of a team name which must be an exact match to one in the dataframe already, otherwise it won’t work. The main thing this function does is replace the value of ‘True’ with one of ‘False’ before calling another function that will update the map.
 

This function filters out any teams with their contention status reading false and then repeats the spatial join of the counties layer to the nearest arena. It then converts the distance column from metres to kilometres. These functions were created as it is possible to run this code 29 times to ‘eliminate’ teams from contention and doing these steps manually is time-consuming.

3.2.	Creating charts

The second set of functions created for this notebook control the collation of data, both numeric and non-numeric and plot those in a bar chart to be displayed in your browser and saved as an image file to the charts folder (there are example charts in the folder in the github repository). 

 

The arguments this function take are all string arguments, with the first one (col_head) needing to be a match to one of the column headers in the Counties dataframe. The other arguments are for labelling purposes and should be made as descriptive as necessary in order to make reading the chart simpler. As an example, the for loop will cycle through the dataframe for each team in the ‘Closest Team’ column (this will be 30 cycles), summing the population counts of each county and adding them to a dictionary called ‘collector’. The second part of the function will rearrange the data before calling a second function called create_chart() that will control the plotting of the data.

 

The purpose of this function is to control the style of the plots produced by this notebook. It sets a defaults chart style and controls the figure size, resolution, type, font sizes, and bar colours. The charts are best viewed by opening the saved images from your working directory.
 


4.	Troubleshooting

•	Repeatedly running section 4 (charts) can cause jupyter notebook to stop outputting displaying information like print statements and calling column headers. The most straightforward solution is to clear all cell outputs, close the notebook totally and restart from anaconda navigator.
•	Clearing outputs and beginning the code from the start will cause progress to ‘reset’ when running the cancun() function to change the map, e.g., running code to eliminate 5 teams, clearing and starting again will ‘reinstate’ those teams.
•	Running the cancun() function by calling it more than one at a time appeared to cause an issue where maps wouldn’t be updated correctly. The workaround for this is to run the function and wait for the saved map to appear in the directory and for the output message to display on notebook before running it again for another team.

5.	References

NBA on TNT. Inside the NBA. Available at: https://www.youtube.com/watch?v=MrfLBx5N62s (Accessed 02/05/2023)
Loose, J., (2023). Closest 2023 NCAA Tournament Team to Each US County https://www.reddit.com/r/CollegeBasketball/comments/11psc4h/closest_2023_ncaa_tournament_team_to_each_us/ [Accessed: 17/04/2023]
Goldsberry, K. (2019). Sprawlball: A Visual Tour of the New Era of the NBA. New York, Ny: Houghton Mifflin Harcourt.
