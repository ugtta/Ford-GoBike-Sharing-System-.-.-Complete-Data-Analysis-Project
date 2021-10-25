{\rtf1\ansi\ansicpg1252\deff0\nouicompat{\fonttbl{\f0\fswiss\fprq2\fcharset0 Arial Black;}{\f1\fswiss\fprq2\fcharset0 Arial;}{\f2\fnil\fcharset0\cpg437 ArialMT;}{\f3\fnil\fcharset0\cpg437 Arial-BoldMT;}{\f4\fswiss\fprq2\fcharset0 Helvetica;}{\f5\fswiss\fprq2\fcharset0 Calibri;}{\f6\fnil\fcharset0 Courier New;}{\f7\fnil\fcharset2 Symbol;}}
{\colortbl ;\red0\green0\blue255;\red0\green0\blue0;\red255\green255\blue255;}
{\*\generator Riched20 10.0.18362}\viewkind4\uc1 
\pard\widctlpar\b\f0\fs32\lang1033 Project: Communicate Data Findings\par
\b0\f1\fs24\par
\b\fs28 Data : Ford GoBike Sharing System\par

\pard\widctlpar\qr\fs22 Date: Feb 14th, 2020\b0\fs24\par

\pard\widctlpar This project is to explore "Ford Gobike Sharing System"\par
\par
\f2            - starting with posing questions about the data\par

\pard\widctlpar\li720\b - First: Wrangling Data\par
\b0 . . . Gathering Data\par
. . . Assessing our data\par
. . . Cleaning the data\par
\b - 2nd : Visualization and Communicate Data Findings\par
\b0 - answering the questions\par

\pard\widctlpar\f1\par
\par

\pard\widctlpar\qj This data was downloaded from Kaggle website ({{\field{\*\fldinst{HYPERLINK https://www.kaggle.com/franckjay/ford-gobike-data }}{\fldrslt{https://www.kaggle.com/franckjay/ford-gobike-data\ul0\cf0}}}}\f1\fs24 ), collected by Ford GoBike System Sharing, for the period from end of June 2017 until first of July 2018 (one year). there are other data files cover all the period of complete year of 2018 and 2019, but I believe our downloaded data with (1338864) rows will do for our current study.\par
Ford GoBike runs business of bike sharing, they have huge numbers of heavy duty, durable fleet of bikes, specially designed and manufactured for this purpose. Distributed in the most important areas in California forming a network of stations in a chosen venues for public use.\par
The data consist of (1338864) rows, (16) columns. . first group of data is: start station related information such as start time, id, name, location defined by its latitude & longitude. Same information types for the end station, besides bike id, user_type, age of members, gender of members and bike share for a trip.\par

\pard\widctlpar\par
\b\f3\fs28 Posing questions\par

\pard\cbpat3\widctlpar\qj\cf2\b0\f4\fs24 1. When are the most numbers of trips taken in terms of:\par

\pard\cbpat3\widctlpar\li720\qj\fs27 - period of day (morning, afternoon, evening and night)\par
- weekdays (monday to sunday)\par
- month of year (january till december)\par

\pard\cbpat3\widctlpar\qj 2. What is the average trip duration?\par
3. What is the average trip duration in term of:\par

\pard\cbpat3\widctlpar\li720\qj - period of day (morning, afternoon, evening and night) \par
- weekdays (monday to sunday)\par
- month of year (january till december)\par

\pard\cbpat3\widctlpar\qj 4. Are the above depend on user type or not?\par
5. what other insights we may find from our data exploration & explanation?\par

\pard\widctlpar\cf0\f1\fs24\par
\b\f2\fs28\par
First: Wrangling Data\par
\b0\f1\fs24\par
\b\fs28 Gathering Data: \par

\pard\widctlpar\qj\b0\fs24 Duly downloaded from the above-mentioned website, the data consist of multiple files (7 csv format files). So after reading the data in pandas, it concatenated together in pandas into one csv format file.\par

\pard\widctlpar\b\par
\par
\fs28 Assessing Data:\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720\b0\fs24 the collected data covers the the period: \par

\pard{\*\pn\pnlvlcont\pnf7\pnindent0{\pntxtb\'B7}}\li720 (from '2017-06-28 09:47:36.3470', till '2018-06-30 23:58:48.2930')\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720 the trip duration is the very important variable in our project:\par

\pard{\*\pn\pnlvlcont\pnf7\pnindent0{\pntxtb\'B7}}\li720 - mean trip duration time = about 16 minutes\par
- minimum trip duration time= about 1 minute\par
- maximum trip duration time= about 1440 minutes= one day\par
\par
other information about trip duration time:\par
\par
- trip duration time median         =  9.5 minutes\par
- trip duration time first quantile  = about 6 minutes\par
\-- trip duration time third quantile = about 15 minutes\par
\par

\pard           - mean of member birth year        = 1981\par
          - minimum of member birth year  = 1932\par
          - maximum of member birth year = 2000\par
\par
          - median of member birth year         = 1984\par
          - first quantile of member birth year  = 1976\par
          - third quantile of member birth year = 1989\par
\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720 the data contains some outliers: such as some persons (members) has birth year before 1900. this means that we have some persons who are participating in this activity have more than 120 years age \par
{\pntext\f7\'B7\tab}user types consist of two categories: customer and subscriber\par
{\pntext\f7\'B7\tab}start_station_id, start_station_name, end_station_id and end_station_name contains cells with null values\par
{\pntext\f7\'B7\tab}total numbers of stations = 308\par

\pard\widctlpar\par
\par
\b Quality Issues:\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720\b0 reindex the dataset (as our dataset consists of multiple data sets, need for reindexing after concatenating them together ).\par
{\pntext\f7\'B7\tab}drop null rows in the dataset\par
{\pntext\f7\'B7\tab}modifying data type for some variables (columns):\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li1080 start_time (from string (object) to datetime)\par
{\pntext\f7\'B7\tab}end_time (from string (object) to datetime)\par
{\pntext\f7\'B7\tab}start_station_id (from "float" to "int" then to "string" type)\par
{\pntext\f7\'B7\tab}end_station_id (from "float" to "int" then to "string" type)\'b6\par
{\pntext\f7\'B7\tab}bike_id (from "int" to "string" type)\par
{\pntext\f7\'B7\tab}member_birth_year (from "float" to "int" type)\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720 drop incorrect data values in member_birth_year\par

\pard{\*\pn\pnlvlcont\pnf7\pnindent0{\pntxtb\'B7}}\par
\b Tidiness Issues\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720\b0 Creating columns from other columns with multiple variables are stored in one column.\par

\pard{\*\pn\pnlvlcont\pnf7\pnindent0{\pntxtb\'B7}}\par
\par
\b\fs28 Cleaning:\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720\b0\fs24 creating a copy dataframe during the cleaning process\par
{\pntext\f7\'B7\tab}do the necessary to correct the quality and tidiness issues above-mentioned. using the standard steps in cleaning processes (\b Define\b0  the problem or dirty/untidy data, \b Code\b0  the proper coding to correct the issues then finally \b Test\b0  our action to see if the issue has been corrected) \par

\pard\widctlpar\par
\par
\par
Data structure: our original data consist of the following variables\par
Number of Columns= 16 columns\par
Number of Rows     = 1338864 rows\par
\par
\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720 duration_sec: duration of each trip in second               \par
{\pntext\f7\'B7\tab}start_time: trip start time                  \par
{\pntext\f7\'B7\tab}end_time: trip end time                   \par
{\pntext\f7\'B7\tab}start_station_id: start station ID number            \par
{\pntext\f7\'B7\tab}start_station_name: start station name          \par
{\pntext\f7\'B7\tab}start_station_latitude      \par
{\pntext\f7\'B7\tab}start_station_longitude     \par
{\pntext\f7\'B7\tab}end_station_id: end station ID number                \par
{\pntext\f7\'B7\tab}end_station_name: end station ID number              \par
{\pntext\f7\'B7\tab}end_station_latitude        \par
{\pntext\f7\'B7\tab}end_station_longitude       \par
{\pntext\f7\'B7\tab}bike_id: Bike ID number                     \par
{\pntext\f7\'B7\tab}user_type: divided into two categories: Customer & Subscriber                   \par
{\pntext\f7\'B7\tab}member_birth_year:           \par
{\pntext\f7\'B7\tab}member_gender: divided in three categories: Male, Female and Other               \par
{\pntext\f7\'B7\tab}bike_share_for_all_trip: Yes or No     \par

\pard\widctlpar\par
after the wrangling and cleaning process 5 other columns were added: all the following added columns were derived from start_time column\par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720 year: year at which any trip start (2017 or 2018)\par
{\pntext\f7\'B7\tab}month: month of year the trip start ( of course we have 12 months Jan, Feb ... till Dec)\par
{\pntext\f7\'B7\tab}day: day of week the trip start ( 7 days, start from Mon, Tue .... till Sun)\par
{\pntext\f7\'B7\tab}hour: the hour of day that any trip start (start from 00, 01, 02 ... till 23)\par
{\pntext\f7\'B7\tab}period of day: it consist of 4 categories (Morning, Afternoon, Evening and Night\par

\pard\widctlpar\par
the total size of our data now after complete wrangling and cleaning will be:\par
Number of Columns= 21 columns\par
Number of Rows     = 1210333 rows\par
\par
\b\fs28 Exploration of Data\par
\fs24  \par

\pard{\pntext\f7\'B7\tab}{\*\pn\pnlvlblt\pnf7\pnindent0{\pntxtb\'B7}}\fi-360\li720\b0 the most numbers of trips are taken in June month then May, the least numbers of trips are taken in July.\par
{\pntext\f7\'B7\tab}most member birth year lying between 1982 and 1992 (member ages of about 26 to 36 year: base year is 2018).\par
{\pntext\f7\'B7\tab}most numbers of trips taken are in May and June and the least number of trips are taken in July.\par
{\pntext\f7\'B7\tab}most numbers of trips are taken in Tuesdays, Wednesdays and Thursdays, the least Number of trips are taken in Sundays\par
{\pntext\f7\'B7\tab}most number of trips are taken in morning and afternoon times the least number of trips are taken at night.\par
{\pntext\f7\'B7\tab}users type are distributed between subscribers 89.2% and customers 10.8%.\par
{\pntext\f7\'B7\tab}member gender consist of male: 74.9%, female: 23.7% and other: 1.4%.  \par
{\pntext\f7\'B7\tab}bike share for all trip: yes: 9.1% and No: 90.9%\par

\pard\widctlpar\par
\par
\b\fs28 Explanatory Visualization:\par
\b0\fs24\par

\pard\widctlpar\qj Now it is time to answer our questions, and summarize the main findings:\par
1. When are the most numbers of trips taken in terms of:\par
     - period of day (morning, afternoon, evening and night)\par
     - weekdays (monday to sunday)\par
     - month of year (january till december)\par
\par
starting with the first term (period of day):  most trips are taken at the afternoon and morning times, the percentage of trips that are taken at afternoon time is about 43%, we may give the following percentage for each period of day:\par
  - afternoon time: about: 43%\par
  - morning time: about  : 42%\par
  - evening time: about   : 14%\par
  - night time: about        : 1%\par
 in the other hand the most trips are taken at weekdays are in Tuesday, Wednesday and Thursday (about 17.5% plus / minus, the peak value is on Tuesdays) then it descends gradually till it reachs to the undermost values (about 8.5% and 7.5%) on Saturdays and Sundays respectively (or on weekends)\par
\par
 in term of month of years: the maximum numbers of trips are taken in June month with about 15.2% then May with about 14% of the total trips. the least number of trips are taken in July with only about 3%.\par
\par
 2. What is the average trip duration:\par
\par
 the average trip duration takes about 16 minutes. though our minimum trip duration is only about one minute, the maximum trip period is about 1440 minutes this equals 24 hours or one entire day. \par
\par
 3. What is the average trip duration in term of:\par
     - period of day (morning, afternoon, evening and night)\par
     - weekdays (monday to sunday)\par
     - month of year (january till december)\par
\par
 the average trip duration regardless of any constraints of time is 16 minutes\par
 in term of period of day, the longest average trip duration are on mornings and afternoons, the average trip durations are:\par
 - morning time  : about 13.5 minutes\par
 - afternoon time: about 13.0 minutes\par
 - evening time  : about 11.5 minutes\par
 - night time       : about 10.0 minutes\par
 in case of weekdays, the longest average trip duration are on Sundays and Saturdays (or on weekends)\par
 the distribution of average trip duration on the weekdays has its maximum value of about 17 minutes on Sundays then about 16 minutes on Saturdays (the maximum average is in weekends) then the value line goes down to the least value of about 11 minutes on Mondays\par
\par
 in case of months of year, the longest trip duration is in July with about 18.25 minutes then November and September with about 15 minutes, the least average trip duration is in June and December with about 11 minutes.\par
\par
 4. Are the above depend on user type or not\par
\par
 the answer is yes,\par
 the average trip duration in minutes for each user type are as follows:\par
 - period of day\par
     -- in case of subscribers:the average trip duration at morning and afternoon times will be about 11.5 minutes, this value will come down at evening and night to about 10 minutes.\par
     -- in case of customers: the average trip duration will be at its peak in the morning time of about 35 minutes, then it goes down in afternoon time to about 27 minutes then to 23 minutes at evening time and finally to about 13 minutes at night period.\par
 - weekdays: the same scenario is noted on weekdays, as the average trip duration for the subscribers are more balanced scale (almost constant or not changing much from day to day) and further less than the customers average trip duration. the subscriber average trip duration in its heighest level in Sundays for about 13 minutes then Saturdays in 12 minutes then it goes to its minimum at Wednesdays about 10 minutes. \par
 in the contrary the customer average trip duration have a maximum value of about 33 minutes on Sundays, 32 minutes on Saturdays, 31 minutes in Tuesdays and it goes down to its minimum in Mondays with average trip duration equals about 18 minutes.\par
 - going to month scale: the same pattern will continue in case of subscribers with average trip duration of about 10 minutes for all months of year with a rise in this value to about 13 minutes in November. \par
 in case of customers: our peak value of the average trip duration is in July with a value of about 80 minutes, then it goes down dramatically to about 38 minutes in April and it reaches its bottom value in June and November with average trip duration equal to about 20 minutes.\par
\par
 5. what other insights we may find from above.\par
 we can conclude from above results that although the least number of trips are taken on Saturdays and Sundays (or on weekends), but the average trip duration has its maximum on weekends (Saturdays and Sundays). this means that there is a limit numbers of members will hire these bikes on weekends (so the number of trips are at its minimum value) but they will keep the bike for a longer time and maybe for daylong (they may need these bikes in having fun and in their weekend various activities) and this will make the average trip duration has its utmost value on weekends. \par
 in the contrary the number of trips are taken on other days (working days) epecially on Tuesdays, Wednesdays and Thurdays is much higher from these taken on Weekends, but the avearge trip duration on these days (working days) is much less or limit. apparently members use the bikes to reach their work locations.\par
 in a bar plot (in univariate section) for proportion of bike hiring during the hours of day (along 24 hours): the maximum proportion (about 12%) is on 8 o'clock, morning and 5 o'clock afternoon. this means that the most bike sharing activities are used in going to work (8 o'clock in the mornings) and back home (5 o'clock in the afternoons) at rush hours. the second position (9.5%) goes to the period of (9 am) and (6 pm) each of them is time after the rush hour, going work time (8 am + 9 am) then back home (5 pm + 6 pm). accordingly the total proportion for these four hours (12% + 12% + 9.5% + 9.5%= 43%). and this a nother clue of using the bikes in reaching work locations and back home.  \par
\par
\b Mohamed Makki\par

\pard\widctlpar\sa160\sl252\slmult1\qj\b0\f5\fs22\par

\pard\qj\f6\par
}
 