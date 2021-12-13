# perfserver
This is a simple JSON Server, that delivers pseudo performance data. It used to test programming capabilities

1) The Simulator
The first thing is a simulator, that simulate providing Performance data.

It can be startet with java -jar perfserver-[....].jar or is found as the responsible maven project.
This launches a webserver with the folliwng functions on http://127.0.0.1:8001

/hello  -> This answers with Hello World
/getdata ->  This shall be called with the following parameter ?time=[unix timestamp in seconds]

http://127.0.0.1:8001/getdata?time=1639062504

This delivers a CSV file in the folling format

Timestamp|Duration|Key|[Name of values|]*




2) Requirements for the program.

The programm shall retrieve for a given 5 minute slice the performance data from the server.
The unix timestamp shall be the timestamp at the beginning of the time interval.
If the start time of the program is smaller than current time - 5 minutes another time slice shall be retrieved.
After successful retrieving a time slice the start date of the timeslice shall be written to a file on the disk.

If the program is started again the file shall be read and retrieving of data shall start with the next time slice.
The date/time in the file shall be in a human understandable format.

The output shall be one or more valid JSON files with the following format

- each line is a valid JSON format
- {starttime:"|ISO 8601 Format|",duration:|duration in minutes|,key:{key:"|Value of Key|"},value:{|Name-Val1|:|val1|,|Name-Val2|:|val2|,...}}


Hint: One of easiest JSON formating libraries is Google GSON:  https://github.com/google/gson

