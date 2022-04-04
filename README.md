# Election Results analysis with Python

## Overview of Project

In this project, using a Python script we will read a CSV file that has election voting results. By using a text editor or Excel we can see that the election_results has 3 columns: Ballot ID,County,Candidate.
Election results can be challenging to audit given the large amount of data (based on population of the regions or even countries).

By using the programming language we can code an algorythm that can with one click perform all the actions in the proper order to read the voting results, process the information and generate an accurate summary and audit of the values of this specific election.

### Purpose

From the previous sections we had already had instructions on how to read the election_results.csv and obtain the following data:
- Total number of votes cast
- A complete list of candidates who received votes
- Total number of votes each candidate received
- Percentage of votes each candidate won
- The winner of the election based on popular vote

Here are the results obtained for the candidate values
![image of candidate vote values](/resources/CandidateResults.png)

We are now to retrive additional data:

- The voter turnout for each county
- The percentage of votes from each county out of the total count
- The county with the highest turnout

## Results:

Deliverable 1: The Election Results Printed to the Command Line
![image of Election results to the command line](/resources/Terminal_ScreenShot.png)

Deliverable 2: The Election Results Saved to a Text File
![image of Election results saved to a text file](/resources/election_results.png)

Election-Audit Results: 

- How many votes were cast in this congressional election?

Election Results
-------------------------
Total Votes: 369,711
-------------------------

The total number of votes casted in this election were equal to the total number of rows present in the elections_results.csv file minus the first row that in this case included a header. I validated the total votes by browsing the file in excel:

![image of total lines preview](/resources/excel_preview_csv.png)

- Breakdown of the number of votes and the percentage of total votes for each county in the precinct.

By creating a list candidate_options[] that was added every distinct county name encountered when reading row by row from the CSV file

```
 # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

        # Get the candidate name from each row.
        candidate_name = row[2]

        # 3: Extract the county name from each row.
        #county name is in the second coulumn of each row index value 1
        county_name = row[1]

        # If the candidate does not match any existing candidate add it to
        # the candidate list
        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1

        # 4a: Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in county_options:

            # 4b: Add the existing county to the list of counties.
            county_options.append(county_name)

            # 4c: Begin tracking the county's vote count.
            county_votes[county_name] = 0


        # 5: Add a vote to that county's vote count.
        county_votes[county_name] += 1

```

3 counties were found to have received votes during this election


Jefferson: 10.5% (38,855)

Denver: 82.8% (306,055)

Arapahoe: 6.7% (24,801)


- County had the largest number of votes? 

Based on the comparaison of the percentages the county with the largest number of votes is Denver with 306,055 votes

- Breakdown of the number of votes and the percentage of the total votes each candidate received.

Charles Casper Stockham: 23.0% (85,213)

Diana DeGette: 73.8% (272,892)

Raymon Anthony Doane: 3.1% (11,606)


- Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

from the results sabed in the election results.txt file and the output printed to the terminal

-------------------------
Winner: Diana DeGette
Winning Vote Count: 272,892
Winning Percentage: 73.8%
-------------------------

Election-Audit Summary: 

The benefits of using this Python script to process or audit the results of this congressional election are:

- Reducing the Human Error factor of having hired personel reading and counting row by row. 
- Reduction of the time spent to perform and provide complete results of the audit.

It is important to have an efficient audit sytem that doesn't require a large number of election official employed and paid overtime to perform such audits.
If more than one file would be provided it could be useful to have the audit official introduce the name of the file to be processed by prompting the user for the name of the file to process 

example

```
# Modules
import os
import csv

# Prompt user for video lookup
inputAuditFile = input("Type in the filename for the election audit( filename.csv ): ")

# Set path for file
csvpath = os.path.join( "resources", inputAuditFile)


```
