# Election_Analysis
Python practice 

## Project Overview

A Colorado board of Elections employee has given you the following tasks to complete the election audit of a recent local congressional election.

* 1. Calculate the total number of votes cast.
* 2. Get a complete list of candidates who received votes.
* 3. Calculate the total number of votes each candidate received.
* 4. Calculate the percentage of votes each candidate won.
* 5. Determine the winner of the election based on popular vote.
## Resources
-Data source: election_results.csv
-Software Python 3.6.1 Visual Studio Code. 1.38.1

## Summary

The analysis of the election show that:



| Total votes  |
| ------------- |
| 369,711|

| Candidates  |
| ------------- |
| Charles Casper Stockham|
| Diana DeGette |
| Raymon Anthony Doane |

The candidates results were:

| Candidate  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Charles Casper Stockham | 23.0%  | 85,213  |
| Diana DeGette | 73.8%  | 272,892  |
| Raymon Anthony Doane | 3.1%  | 11,606  |

### The winner of the election was:

| Candidate  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Diana DeGette | 73.8%  | 272,892  |

### Challenge Overview

Specifically for the challenge the election commission has requested some additional data to complete the audit:

* The voter turnout for each county
* The percentage of votes from each county out of the total count
* The county with the highest turnout

This information will provide the insights to the Colorado Board to validate the results of this election.

### Challenge Summary

After running the analysis, it is pretty clear that the county with the highest turnout is Colorado.

Results are displayed has follows:

* How many votes were cast in this congressional election?


| Total votes  |
| ------------- |
| 369,711|

This question gets answer with a "for" loop that goes through all the rows in the file (excepting the headers)

with open(file_to_load) as election_data:
    reader = csv.reader(election_data)

    # Read the header
    header = next(reader)

    # For each row in the CSV file.
    for row in reader:

        # Add to the total vote count
        total_votes = total_votes + 1

* Provide a breakdown of the number of votes and the percentage of total votes for each county in the precinct.


| County  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Jefferson | 10.5%  | 38,855  |
| Denver | 82.8%  | 306,055  |
| Arapahoe | 6.7%  | 24,801  |

To answer this question we must declare certain variables that will help us store the data for each county.
This will get answered with a "for" loop that will  calculate the participation of each county in this election.

    for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        cvotes = county_votes.get(county_name)
        # 6c: Calculate the percentage of votes for the county.
        cvote_percentage=float(cvotes)/float(total_votes)*100

         # 6d: Print the county results to the terminal.
        county_results=(
            f"{county_name}: {cvote_percentage:.1f}% ({cvotes:,})\n")
        print(county_results)

* Which county had the largest number of votes?


| County  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Denver | 82.8%  | 306,055  |

In this case we use conditionals to compare which county has the largest participation in the election.

        if (cvotes>largest_county_count) and (cvote_percentage>largest_county_percentage):
            largest_county_count=cvotes
            largest_county=county_name
            largest_county_percentage=cvote_percentage

    # 7: Print the county with the largest turnout to the terminal.
    largest_county_summary=(
        f"-------------------------\n"
        f"Largest County Turnout: {largest_county}\n"
        f"-------------------------\n"
    )
    print(largest_county_summary)

* Provide a breakdown of the number of votes and the percentage of the total votes each candidate received.


| Candidate  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Charles Casper Stockham | 23.0%  | 85,213  |
| Diana DeGette | 73.8%  | 272,892  |
| Raymon Anthony Doane | 3.1%  | 11,606  |

As per the activity answered before this information gets concentrated in this summary.

* Which candidate won the election, what was their vote count, and what was their percentage of the total votes?

| Candidate  | % of the vote | Number of votes |
| ------------- | ------------- | ------------- |
| Diana DeGette | 73.8%  | 272,892  |

Contratulations to Diana DeGette who won this election by a significant majority!

### Election Audit Summary

This information could have been showed with a simple analysis even in an excel file but the solution we are offering goes beyond Colorado and can be used in any Election at any level (with a similar structure).

A few things might be changed in order to use this code for future elections. Some of this are:

* Origin of votes, we might want to know if all voters voted through mail, virtually or on the election day, in order to get this answer we can repeat the exercise but obviusly will need the data to analyze it.

* Presidential Elections, what if we want to use this code for presidential elections. The logic is the same, maybe we want to know who won in each state, for this, we'll need a new column that has this level of detail, going to a county-state relationship. And following the same logic we can perform that level of analysis.

As we already said, this information for this exercise could have been easily performed by an excel file, but having the code we can face biggest data challenges that won't run in an excel file due to the amount of data gathered. This kind of exercises helps us to think in a general way without having specific solutions but rather general solutions!
