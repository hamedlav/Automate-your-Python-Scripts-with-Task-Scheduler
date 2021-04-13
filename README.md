# Automate-your-Python-Scripts-with-Task-Scheduler

By definition, periodic tasks are tasks which are executed repeatedly along a certain time interval with no or minimum human intervention. In the period where data and technology evolve rapidly, you need to run scripts to develop database backups, Twitter streaming, etc.
Luckily, with Task Scheduler, you can now run your Python script to execute periodic tasks every day/week/month/year depending on your needs.
In this tutorial, you will learn how to run task scheduler to web scrape data from Lazada (eCommerce) website and dump it into SQLite RDBMS Database.

The Methods
In this tutorial, we will use Windows Task Scheduler to run a bat script which will trigger the Python Scripts. To execute these scripts, we have two simple steps:
1.	Create Python Executable Files (bat file)
2.	Configure Task in Windows Task Scheduler
However, if you are Linux users and do not have the Windows Task Scheduler available, you should use cron schedulers.

Creating Windows Executable bat file to run Python
A BAT file is a DOS batch file used to execute commands with the Windows Command Prompt (cmd.exe). It contains a series of line commands that typically might be entered at the DOS command prompt. BAT files are most commonly used to start programs and run maintenance utilities within Windows. — fileinfo.com
Using bat file as our executable, we would store our run script in a file then double click on the bat file to execute the command on cmd (command prompt) to run python script.
All you need to do is to create a new bat file (e.g: web-scraping.bat) and write the executable script with the format of <Your Python.exe Location> <Your python Scripts Location> . You can add the pause command to avoid closing the command prompt after the execution.

C:\new_software\finance\Scripts\python.exe "C:/new_software/Web Scraping/Web-Scraping/Selenium Web Scraping/scraping-lazada.py"
pause
Once you double click on this bat file, Windows will open your command prompt and run the web scraping tool. To schedule this double click/execution, we will hook our task scheduler to the bat file.

Configure Task in Windows Task Scheduler
Windows Task Scheduler is a default Windows Application to manage tasks in response of an event based or time based trigger. For example, you could suggest a certain click and computer actions (such as reboot) or even suggest timing like every first day of financial quarter to execute the task.
In a larger picture, this task would contain the script and metadata to define what and how the action will be executed. You can add certain security context in the argument and control where the scheduler will run the program in. Windows will serialize all of these tasks as a .job files in a special folder called Task Folder.
 

1.	Click on Start Windows, search for Task Scheduler, and open it.
2.	Click Create Basic Task at the right window
3.	Choose your trigger time.
4.	Pick the exact time for our previous selection.
5.	Start a program
6.	Insert your program script where you saved your bat file earlier.
7.	Click Finish.

Let’s get started!
1.	Click on Start Windows, search for Task Scheduler, and open it.
 
2. Click Create Basic Task at the right window.
You should put your task name (e.g: Web scraping) and description (e.g: Web Scraping and SQLite Dump automatically every day at 6 pm)
 

3. Choose your trigger time.
You will have an option to pick the time trigger in daily weekly, and even monthly. Logically, this choice depends largely on how often you want to refresh the values from your data source. For example, if your task is to scrape MarketWatch Stocks balance sheet, you should run the scripts every financial quarter.

 
4. Pick the exact time for our previous selection.
We will pick the month January, April, July, and September to indicate all early financial quarter.
 
5. Start a program
Here you will be able to start the Python Scripts, send an e-mail, and even display a message. Feel free to choose ones which you are most comfortable with. However, you should watch out as there are deprecated tasks which will be removed in the subsequent patches.
 
6. Insert your program script where you saved your bat file earlier.
This will run Task Scheduler to your Python Script for automation. Make sure you also include Start in to the location of your application folder to access all of the relevant elements (Selenium Browser executables / SQLite Disk)   address .bat file
Ex: D:\Local Disk\Python\Tamrin\Basic\Tamrin 4th session
 
7. Click Finish.
You can check your created task schedule in your front page of Task Scheduler.

Congratulations, you have set up your first automated scheduler in Windows.


Reference: https://towardsdatascience.com/automate-your-python-scripts-with-task-scheduler-661d0a40b279
