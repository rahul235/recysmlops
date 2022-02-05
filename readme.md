conda env list 
##Create a virtual env named mlopslab with python 3.8 version 
conda create --name mlopslab python=3.8 
conda activate mlopslab

## change the directory to recysmlops and initialise git in it.
cd /Users/Rahul/Documents/Rahul\ Office/IIMB/Concepts/Python/recysmlops
## To record the log of all the commands issued in terminal
script screen.log

git init
git status

## create a file in recysmlops
touch readme.md
git status 

## add the file in version control
git add .  
git status
git commit -m "added readme file”
git status 
ls -al 

## Initialise dvc in recysmlops to manage the data file
dvc init
git status
git add .
git commit -m "Initialize DVC”

## make a folder in recysmlops and add shoes.zip file to it.
mkdir data

## add shoes.zip to dvc for version control
dvc add data/shoes.zip

git status
git add .
git commit -m "added first version of the dataset”

##create a folder in google drive and set the access to the folder to anyone with link. Copy the folder link and set it as default remote dir for dvc
dvc remote add -d gdremote gdrive://1pOgfejXYZzretZjbGLpdQbgwj-yoF7H3    

git add .
git status
git commit -m "configured google drive storage location”

## This will push the data file from data folder to the google drive. I link will come in terminal. Paste that in URL and follow steps to get the authentication
dvc push -r gdremote  


##Create a folder in GitHub with the same name as recysmlops and then follow below steps:
git branch -M main
git remote add origin git@github.com:rahul235/recysmlops.git
git push -u origin main

dvc list https://github.com/rahul235/recysmlops.git ## to see what got listed in github	

##To download the file from google drive to local machine
cd /Users/Rahul/Documents/Rahul\ Office/IIMB/Concepts/Python/

## Pull the data file from google drive to Python folder. I link will come. Paste that in URL and follow steps to get the authentication
dvc get https://github.com/rahul235/recysmlops data/shoes.zip 

## To update a file:
git diff (to check the updated files)
git status (to check the status of GitHub repository)
git add <file name> (e.g. git add "ML_Concept/Data_Science_Advanced_Lesson03_Logistic Regression_using_Gradient_Descent.pdf”)
git commit -m “updated comment”
git push -u origin master

## To exit the log 
exit