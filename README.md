# Brockton_911_Data_Analysis
An analysis of 911 calls in the city of Brockton, MA for the years 2015 - 2020.

# Data Gathering

Every 911 Call placed is recorded and uploaded to the [Brockton Police Department Website](http://www.brocktonpolice.com/category/police-log/page/1). To access the data the "Download Brockton PDFs" file was created. The URL structure of the website looks like this:

http://www.brocktonpolice.com/category/police-log/page/1

The page/n format at the end of the URL is used to iterate through the pages and collect the initial links which contain secondary links to the PDF URLs. Once the URLs have been gathered the PDFs are downloaded. The "Convert PDF to Text" file is used to take the downloaded PDFs and convert each of them into a text file. The format of the PDF changes sporadically so python packages like [PDFMiner](http://www.unixuser.org/~euske/python/pdfminer/index.html) return inconsistent data. The most consistent way to extract the text is to open each file, select all (CTRL + A) of the text in the PDF, copy the text, and save the clipboard to a text file.

The final step is to extract each of the files into a single CSV file using the "Text to CSV" file which looks at each 911 call and extracts the necessary columns:

Date, Call_Number, Reference_Call_Number, Call_Time, Action, Call_Reason, Call_Taker, Location, Num_Officers, Officers, Num_Arrests, Num_Arrest_Charges, Arrests_Raw_Data, Num_Summons, Num_Summons_Charges, Summons_Raw_Data, Fire_Unit_Data, EMS_Unit_Data

One point to note is that there are some missing days. January and February 2017, along with a handful of days (usually the last day of the month) are missing from the police logs.

# Analysis

## Average Time To Dispatch

When someone calls 911, what is the average time it takes before someone is dispatched? Does it change based on the reason the 911 call was placed?

|HH:MM:SS|         Call Reason|
|--------|--------------------|
04:07:00|         Missing People
03:05:06|         Liquor Law Violation
01:09:25|         Traffic Control
01:08:16|         Vandalism
01:03:45|         Malicious Damage Investigation
01:02:54|         Serve Summons
01:02:51|         Larceny Investigation
01:02:23|         Code Enforcement
01:01:36|         Larceny Of A Bicycle
01:00:35|         Runaway Investigation
00:59:10|         B & E Mv Investigation
00:58:12|         Shoplifting Investigation
00:57:11|         Annoying Phone Calls
00:56:28|         Cdbg Proactive Patrol
00:56:11|         Threats See The Complainant
00:55:11|         Malicious Damage Motor Vehicle
00:54:48|         B & E, Attempted
00:53:47|         Check Mv Abandoned
00:53:39|         Arson Invest
00:53:37|         Larceny Of A Motor Veh Plate
00:53:29|         Motor Vehicle Abandoned
00:52:29|         Parking Violation
00:52:17|         Arson & Bombing
00:52:09|         Check Abandoned Building
00:51:12|         Code License Violation
00:50:47|         B & E Investigate
00:49:50|         Disturbance, Fire Works
00:48:25|         Abuse Of 911 System
00:48:18|         Parking Violation - Snow Emrg
00:48:10|         Hit & Run Investigate
00:47:42|         See The Complainant
00:45:39|         Missing Person
00:44:54|         Pickup A Prisoner On A Warrant
00:44:45|         Tree Limbs Down
00:42:45|         Larceny Of A M/V Investigation
00:41:10|         Larceny /Forgery/ Fraud
00:38:59|         Disturbance Loud Music
00:36:41|         Keep The Peace
00:35:58|         Motor Vehicle Blocking Drivewy
00:35:18|         Animal Complaint Barking(Dist)
00:31:28|         Parking Violation Winter Ban
00:31:26|         Check Mv Poss Stolen
00:31:07|         Trespassing
00:29:56|         Down Wires
00:29:55|         Soliciting
00:29:38|         Housing Investigation
00:29:16|         Motor Vehicle Stop
00:28:42|         Community Police Call
00:27:35|         Missing Person Invest
00:27:26|         Recovered M / V Out Of Town
00:27:06|         Tow Private Request
00:26:54|         Check Property
00:26:42|         Recovered Stolen Mv
00:23:52|         Suspicious Package
00:23:51|         Check Motorist Suspicious
00:23:41|         Check Dirt Bike Drive Erratic
00:23:38|         Stalking
00:23:00|         B & E Motor Vehicle
00:20:40|         Robbery Investigation
00:20:40|         Injured Animal
00:20:37|         Animal Complaint
00:20:21|         Sex Offenses
00:19:51|         Check Motorist Disabled
00:19:46|         Suspicious Mv
00:19:41|         Narcotic Violation In Progress
00:19:39|         Motor Vehicle Blocking
00:19:36|         Assist Citizen
00:19:35|         Larceny Of A Motor Vehicle
00:18:49|         Assist Other Agency
00:18:17|         Road Rage
00:18:11|         Check Motorist Drive Erratic
00:18:04|         Accosting
00:17:20|         911 Verify Call
00:17:20|         Suspicious Activity
00:17:06|         Animal Control Dog Complaint
00:16:12|         Escort
00:16:07|         Disturbance Drag Racing
00:16:02|         A & B Dangerous Weapon Invest
00:16:00|         Hit & Run In Progress
00:15:43|         Gang Of Youths
00:15:34|         Shoplifting - In Custody
00:15:29|         Suspicious Person
00:15:23|         Check Motorist Drunk
00:15:07|         Prostitution
00:15:00|         Disturbance/Dirt Bikes
00:14:21|         Open And Gross
00:13:12|         Malicious Damage - In Progress
00:12:53|         Disturbance
00:12:29|         Community Police Foot Patrol
00:12:18|         Police Off Has A Prisoner
00:12:08|         911 False Call
00:12:06|         Shoplifting In Progress
00:11:45|         Disturbance Loud Noise
00:11:13|         Serve Warrant
00:10:50|         Larceny In Progress
00:10:29|         M V A - No Pi
00:10:23|         Homicide
00:10:23|         Alarm Audible
00:09:19|         Community Police
00:09:02|         Unwanted Guest Family
00:08:33|         911 Hang Up
00:08:33|         Disturbance By A Drunk
00:08:20|         M V A Pedestrian
00:08:20|         Suspcious Motor Vehicles
00:07:37|         Carjacking
00:07:35|         Unwanted Guest Disturbance
00:07:28|         Sex Offender Investigation
00:07:08|         Unwanted Guest Drunk
00:07:06|         Kidnapping
00:06:48|         Investigate Dangerous Weapon
00:06:42|         Prowler
00:06:39|         Disturbance Mc
00:06:26|         M V A With Property Damage
00:06:17|         M V A
00:06:15|         Alarm Telephone
00:06:13|         Alarm, Burglar
00:05:56|         911 Unknown Emergency
00:05:50|         Unknown Emergency
00:05:50|         Overdose
00:05:42|         Assist Fire Or Ambulance
00:05:29|         Man With A Gun
00:05:28|         Party Unconscious
00:05:22|         Bomb Scare
00:05:15|         M V A With Injuries
00:05:15|         Burglary, Invest
00:05:15|         Robbery
00:05:11|         Tow Snow Removal
00:05:06|         Gun Possession Incident
00:05:06|         B & E In Progress
00:05:04|         Alarm, Panic
00:05:03|         Fire, Other
00:04:34|         Assist Fire And Dpw
00:04:34|         A & B Dangerous Weapon Knife
00:04:26|         Disturbance - School, Daycare, Child Facility (Weapon)
00:04:21|         Alarm, Hold-Up
00:04:20|         Home Invasion
00:04:19|         Sex Offender Violation
00:04:13|         Loud Music
00:04:11|         Vehicle Fire
00:04:02|         A & B Dangerous Weapon Gun
00:04:01|         Repossess
00:04:00|         Structure Fire
00:03:59|         Tow Repo/Trespass
00:03:52|         Motor Vehicle Pursuit
00:03:50|         Escort/Transport
00:03:44|         Gunshots Call
00:03:38|         Assist Foxboro Pd
00:03:34|         Traffic Control Fire
00:03:32|         Burglary, Armed
00:03:24|         Fire Investigation
00:03:20|         Gunshot Call By Shotspotter
00:03:18|         Code Safety Violation
00:02:56|         Assist Fire
00:02:56|         Suspicious Party
00:02:48|         911 Transfer To Ambulance
00:02:44|         Blown Transformer/Fire
00:02:32|         Prisoner Booked
00:02:22|         Foot Patrol
00:02:21|         Assist Animal Control
00:02:13|         Serve Revocation Notice
00:02:10|         Tow Next In Line
00:01:46|         Recovered M / V Parts
00:01:45|         Recovered M / V Plate
00:01:43|         Road Race
00:01:42|         Foot Pursuit
00:01:12|         Water Ban Violation
00:01:00|         Disturbance Panhandler
00:00:59|         Community Police Bike Patrol
00:00:49|         Recovered Plate Out Of Town

There are some points to note here. The first is that this data still includes outliers so actual numbers will, in most cases, be lower. For example, the average time between when a call is placed and an officer is dispatched for a "Gunshots Call" is 3 minutes and 44 seconds. However, there are several outliers where the time it takes an officer to be dispatched is 20+ hours. This is obviously either not correct or extremely unlikely to happen. Further analysis will look into these events more thoroughly and correct for outliers in the data.


## Distribution of Age for Arrests

What does the distribution of ages look like for arrests? 

![Frequency of ages for all arrests](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Age_Arrests.png)

This may not come as a surprise but generally 25-30 y/o are most likely to be arrested followed closely by 20-25 y/o and then by 30-35 y/o. There is no noticeable trend in the ages of people who are arrested increasing or decreasing over time.

![Age and arrests over time](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Age_Over_Time_Arrests.png)

## Frequency Counts of Charges for Arrested Individuals

Is there some underlying relationship for why people are arrested? Do people who are arrested for Possession of a Schedule I substance also get charged with possession of an illegal fire arm? The top 20 most frequent charge pairs are listed below and the details really aren't too shocking. We have pairs like uninsured and unregistered motor vehicle, no inspection sticker and unlicensed operation of a motor vehicle, A&B on a police officer and resisting arrest.


|Charge 1| Charge 2| Number of Occurrences
|--------|---------|----------------------
DISORDERLY CONDUCT | DISTURBING THE PEACE | 564
UNINSURED MOTOR VEHICLE | UNREGISTERED MOTOR VEHICLE | 350 
DISTURBING THE PEACE | RESIST ARREST | 264 
DISORDERLY CONDUCT | RESIST ARREST | 253 
STOP/YIELD, FAIL TO / /CAUSING OR CREATING GRIDLOCK | UNLICENSED OPERATION OF MV | 240 
DISTURBING THE PEACE | TRESPASS | 199 
ATTACHING PLATES TO MV | UNREGISTERED MOTOR VEHICLE | 169 
DISORDERLY CONDUCT | TRESPASS | 147 
MARKED LANES VIOLATION | UNLICENSED OPERATION OF MV | 147 
ATTACHING PLATES TO MV | UNINSURED MOTOR VEHICLE | 146 
WARRANT, FOREIGN | WARRANT, LOCAL | 130 
RECKLESS OPERATION OF MOTOR VEHICLE | STOP FOR POLICE, FAIL | 129 
UNLICENSED OPERATION OF MV | UNREGISTERED MOTOR VEHICLE | 129 
STOP FOR POLICE, FAIL | STOP/YIELD, FAIL TO / /CAUSING OR CREATING GRIDLOCK | 116 
LICENSE SUSPENDED, OP MV WITH | STOP/YIELD, FAIL TO / /CAUSING OR CREATING GRIDLOCK | 115 
WARRANT, DEFAULT | WARRANT, FOREIGN | 115 
WARRANT, DEFAULT | WARRANT, LOCAL | 113 
REGISTRATION SUSPENDED, OP MV WITH | UNINSURED MOTOR VEHICLE | 110 
UNINSURED MOTOR VEHICLE | UNLICENSED OPERATION OF MV | 106 
RESIST ARREST | TRESPASS | 101 

Just dumping out the most common occurrences might not be the best way to go about this. We can instead select a specific charge like A&B on a police officer and see what the most frequent pairings are.

Charge 1|Charge 2| Number of Occurrences
--------|--------|----------------------
A&B ON POLICE OFFICER | RESIST ARREST | 99
A&B ON POLICE OFFICER | DISTURBING THE PEACE | 79
A&B ON POLICE OFFICER | DISORDERLY CONDUCT | 77
A&B ON POLICE OFFICER | Interfering with Police Officer in Performance of Duty | 20
A&B ON POLICE OFFICER | TRESPASS | 20

This gives us something a little more concrete where we can say we have examples of 79 incidents where someone was disturbing the peace and then also assaulted a police officer. In the event that police arrest a new person for disturbing the peace, this information could be useful simply by increasing awareness. This may be useful for other things as well like when a person has a weapon. If we examine firearm charges we can see that there is some frequency with which drug charges and firearm charges overlap. This information may be useful to know when searching a vehicle or person.

## Number of Arrests and Calls Over Time

Looking at the number of arrests over time shows an interesting drop in arrests in 2020.

![Arrests by year](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Arrests_Per_Year.png)

If we also examine the calls placed in 2020 we would expect to see a similar decrease. However this is not the case.

![Calls per year](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Calls_Per_Year.png)

Does COVID have something to do with the decrease in calls? Is there some strangeness happening in the details? Lets examine the second question first. Perhaps the month to month data will show something more interesting?

![Arrests per month](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Arrests_Per_Month.png)

![Calls per month](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Calls_Per_Month.png)

No, nothing remarkable there. There just seems to be fewer arrests. Let's take a look at a break down of the most common types of calls that resulted in arrests in 2019 and compare these to 2020.

![2019-2020 arrest comparison](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/2019_2020_Arrest_Comp.png)

The vagueness of the calls is not helpful for assessing the situation but it seems like arrests that are controllable by police such as "Pickup a Prisoner on a Warrant" have decreased. This may be due to some change in policy due to COVID-19. It is interesting to note that other calls tend to result in fewer arrests. Further analysis will examine the relationship between total calls for a given arrest and the number of arrests between 2019 and 2020.

## Drug Charges Over Time

While we do not have specific information about the type of drug that a person is caught with when arrested we have general information about the schedule of the drug (Schedule I to Schedule V). We can look into the rate of arrests for each type of drug over time.

![Drug Charges by type over time](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Charges_By_Drug_Type_Over_Time.png)

Each schedule of drug seems to stay within its own frequency lane except for schedule I and IV which occasionally switch second and third highest frequency. We can break this down further based on if the charge was for possession of a drug or possession with intent to distribute.

![Distribution and Possession of different schedules of drugs over time](https://github.com/Vinnie-Singleton/Brockton_911_Data_Analysis/blob/main/Pics/Charges_By_Drug_Type_and_Charge_Over_Time.png)

