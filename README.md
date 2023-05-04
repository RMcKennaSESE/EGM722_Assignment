# EGM722_Assignment
Repository for the purposes of the EGM722 assignment



1.	Installation guide
Repository for the code can be found here: https://github.com/RMcKennaSESE/EGM722_Assignment 
Navigating to the repository should display a screen like the one in figure 3.
 
Contents of repository and description
Name	Description
Charts 
	Folder which will contain any images of charts saved when running the code.
Data-files 
	Location of all data files used for this code, including shapefiles, .csv files and GEOJSON files.
Maps 
	Folder which will contain any maps saved when running the code.
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
In order to run the code on your own machine, you will first need to fork the repository and clone it to your own directory.
 
Make sure that on the next screen the option for Copy the main branch only is unchecked, then click Create fork.
 
Once the repository is forked it will need to be cloned to your computer. To do this open up github desktop version.
 
Go to File->Clone repository or Ctrl+Shift+O to open the clone repository menu. 
 
Select a path to save the repository to, remember where, as it will be needed for the next step. Click Clone to clone the repository. Once the repository is finished cloning, select the option For my own purposes when asked how you are planning to use this fork, this will create an independent, local version of the repository that will not contribute to the upstream branch if done correctly.
Now that you have a local copy of the repository saved to your computer the next step is to open this as a jupyter notebook. Open up anaconda navigator and make sure you are in your egm722 environment.

The simplest way to launch notebook from here is by clicking on the Launch button below the jupyter notebook icon. If that doesn’t take you to the correct directory, jupyter can be opened from a command line prompt. Open a command window and enter the following line:

jupyter notebook --notebook-dir={your drive here}:/
 
 
If you get an error here, check your syntax and make sure the command is entered correctly. Successfully running this command will open jupyter in your default browser, from here navigate to where your cloned repository is and select the file named ‘Arena_Map_Project.ipynb’ to begin running the code.

2.	Code guide
Start at section one and work your way through the notebook. 

3.	Troubleshooting
Repeatedly running section 4 (charts) can cause jupyter notebook to stop outputting displaying information like print statements and .head(). The most straightforward solution is to clear cell outputs, close the notebook totally and open it up again.



