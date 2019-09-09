# Simple-Time-Clock
A simple time clock made using PHP and MYSQL on a Debian server to automate the rather archaic process of having employees punch in with physical cards and then having to manually calculate the hours each week. The page will be mostly resizable and usable on a variety of devices. Primarily aimed towards mobile users. My test machine being a Samsung Galaxy S9. 

CSS has been updated to allow easier use on smaller or bigger screens. This timeclock also has logic that only shows pertinent buttons after punching in. (It wont allow you to punch in after punching out. ETC.) This is by no means perfect. But is a great base to build on for your own projects.

Time Clock login page.
https://i.imgur.com/s6MN0oF.png

Employee punch in/out page.
https://i.imgur.com/HSv5qmB.png


The MYSQL database contains two tables:

1. Employees. Which houses your names, and their respective login ID's. 
``create table Employees (ID VARCHAR(20), Name VARCHAR(20), EmployeeID VARCHAR(20));``

2. TimeClock. Which houses the actual punch information for your week.``create table TimeClock (ID VARCHAR(20), Timestamp VARCHAR(20), Date VARCHAR(20), Name VARCHAR(20), `MON-IN` VARCHAR(20), `MON-L-OUT` VARCHAR(20), `MON-L-IN` VARCHAR(20), `MON-OUT` VARCHAR(20), `TUE-IN` VARCHAR(20), `TUE-L-OUT` VARCHAR(20), `TUE-L-IN` VARCHAR(20), `TUE-OUT` VARCHAR(20), `WED-IN` VARCHAR(20), `WED-L-OUT` VARCHAR(20), `WED-L-IN` VARCHAR(20), `WED-OUT` VARCHAR(20), `THU-IN` VARCHAR(20), `THU-L-OUT` VARCHAR(20), `THU-L-IN` VARCHAR(20), `THU-OUT` VARCHAR(20), `FRI-IN` VARCHAR(20), `FRI-L-OUT` VARCHAR(20), `FRI-L-IN` VARCHAR(20), `FRI-OUT` VARCHAR(20), `SAT-IN` VARCHAR(20), `SAT-L-OUT` VARCHAR(20), `SAT-L-IN` VARCHAR(20), `SAT-OUT` VARCHAR(20), `SUN-IN` VARCHAR(20),`SUN-L-OUT` VARCHAR(20), `SUN-L-IN` VARCHAR(20), `SUN-OUT` VARCHAR(20));``

You will need to fill the table with 0's before using any login information. To enter information into these tables you have 2 major commands.


1. ``insert into Employees (ID, Name, EmployeeID)  values ('ID NUMBER', 'EMPLOYEE FULL NAME', 'EMPLOYEE ID NUMBER');``
That is to enter in a new employee. 

2. ``UPDATE `TimeClock` SET `FRI-IN`='0000-00-00 00:00:00' WHERE Name='EMPLOYEE FULL NAME';``
AFTER CHANGING DAY AND TIME. This will allow you to modify punches if need be. 

You will have to actually LOG IN with the user ID before it populates on any of the reports. 

I have not tested any of the following first hand. It is left over documentation from the original project. 


(To create a fresh set of records for each new payweek (in this case, on every Thursday morning at 3am), edit crontab for user 'www-data':

user@hostname:~$ sudo crontab -e -u www-data

0 3 * * 4 python /var/www/scripts/create-new-payweek.py)
