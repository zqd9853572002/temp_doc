# task 6

## (1)determine how to effectively clean the data set

- The overall quality of the data set is very good, but still have some issues need to be addressed. We may solve some problems with data cleaning or need to deal with during the data analysis process

- below are our first impression for the data set

  - all the data are structured data
  - data is not involved with any individual privacy, so we do not need to pay special attention to privacy issue
  - The data variables could be categorized
  - Some variables are duplicated, they could be removed in the data cleaning process
  - Some variables are useless, such as incident\_id and ObjectId, which are the sequence number by call time, they could be removed in the data cleaning process
  - Some variables&#39; meanings are not cleared, we may eliminate them (refer the suggestions in proposal)
  - Some variables will not be used in this analysis, but just in case, we will keep them at this moment
  - Some variables might need to separate into different variables when doing the data analysis (separated variables will reflect original one variable&#39;s different aspects), such as the call\_timestamp could be separated as call date and specific time slot
  - Some data have spelling errors, or same meaning (should be categorized into one group apparently), such as the data in category and calldescription. This part is the main address in the data cleaning process
  - There are some null value or 0 value in the data set, which need to be cleaned or processed. The potential solving methods include abandon, filling by other variables and etc.
  - We could guess some quantitative relationship between different variable, we may consider remove the variable that could be calculated by other variables and just retain them. For example,

    - traveltime = intake time + dispatch time + travel time
    - totaltime = totalresponsetime + time_on_scene

- below is a quick summary

  | category    | variable          | duplicate | can be removed         | mark                                                      |
  | ----------- | ----------------- | --------- | ---------------------- | --------------------------------------------------------- |
  | location    | X                 | Y         |                        |                                                           |
  | location    | Y                 | Y         |                        |                                                           |
  | location    | longitude         | Y         | Y                      | equals x                                                  |
  | location    | latitude          | Y         | Y                      | equals y                                                  |
  | location    | incident_address  |           |                        |                                                           |
  | location    | zip_code          |           |                        |                                                           |
  | location    | neighborhood      |           |                        |                                                           |
  | location    | block_id          |           |                        |                                                           |
  | location    | council_district  |           |                        |                                                           |
  | report      | agency            |           |                        |                                                           |
  | report      | priority          |           |                        |                                                           |
  | report      | calldescription   |           |                        |                                                           |
  | report      | category          |           |                        |                                                           |
  | report      | precinct_sca      |           |                        |                                                           |
  | report      | respondingunit    |           |                        |                                                           |
  | report      | officerinitiated  |           |                        |                                                           |
  | time point  | call_timestamp    |           |                        |                                                           |
  | time period | time_on_scene     |           |                        |                                                           |
  | time period | intaketime        |           |                        |                                                           |
  | time period | dispatchtime      |           |                        |                                                           |
  | time period | traveltime        | (Y)       | need clean data to see | nearly equals (intake time + dispatch time + travel time) |
  | time period | totalresponsetime |           |                        |                                                           |
  | time period | totaltime         | (Y)       | need clean data to see | totaltime = totalresponsetime + time_on_scene             |
  | other       | callcode          |           |                        |                                                           |
  | other       | ObjectId          |           |                        | might not be useful in data analysis                      |
  | other       | incident_id       |           |                        | might not be useful in data analysis                      |

## (2)using automated tools, if possible.

- we used Openrefine to clean the data
- Openrefine is a data cleaning tool which could provide efficiently method to deal the the large data set

## (3)Be sure to discuss with your group and determine HOW MUCH cleaning the data requires. Remember, only clean if it will provide a better model and better insight at the end and the extra effort is worth it!

- considering the overall quality of the data set is good, so we decide not spend lots of time on data cleaning, however, some essential and required cleaning process are still needed
- The problem we proposed in the proposal is where to set the three pertinent, we think this issue is related to the location and time, so we decide the main focus of data cleaning should be on the location and time related variables

  - location related variables will be directly benefit to our question
  - time related variable will help us in determining the pertinent location

# task 7

## (1) Provide a brief extract of &quot;before data&quot; and &quot;after data&quot; as an appendix to your project

Is this asking us to provide a screenshot of the data before cleaning and after cleaning?

## (2) Explain how you cleaned the dataset and the decisions you made. Be particularly clear about outliers,eliminating data points, unstructured data uncertainties, etc.

- Some variables are duplicated, they could be removed in the data cleaning process

  - at this time, we didn&#39;t do anything for the duplicated variables. We will ignore them in the data analysis process

- Some variables are useless, such as incident\_id and ObjectId, which are the sequence number by call time, they could be removed in the data cleaning process

  - We delete the useless variables in the data set

- Some variables&#39; meanings are not cleared, we may eliminate them (refer the suggestions in proposal)

  - at this time, we didn&#39;t do anything for the unmeaning variables. Instead, we will ignore them in the data analysis process. As the analysis process going, we may acquire more knowledge or information, which might provide us some information to these variables

- Some variables will not be used in this analysis, but just in case, we will keep them at this moment
- Some variables might need to separate into different variables when doing the data analysis (separated variables will reflect original one variable&#39;s different aspects), such as the call\_timestamp could be separated as call date and specific time slot

  - we have separated the variable into two variables, such as separated &quot;call-timestamp&quot; into &quot;call\_times&quot; and &quot;stamp&quot;, which might be easier when analyze time related questions

- Some data have spelling errors, or same meaning (should be categorized into one group apparently), such as the data in category and calldescription. This part is the main address in the data cleaning process

  - we used Openrefine to do that. The main related function is &quot;text facet&quot; and &quot;cluster and edit&quot; in dealing with nonnumerical variable, such as &quot;category&quot; and &quot;calldescription&quot;

- There are some null value or 0 value in the data set, which need to be cleaned or processed. The potential solving methods include abandon, filling by other variables and etc.

  - we used the &quot;N/A&quot; to fill the blank value or 0 value in the data set
  - For the time duration blank or 0 value, we are considering to use the similar instance&#39;s average value to fill. However, this method could be very time-consuming. Also, considering the &quot;N/A&quot; only account less than 5% within the variable, so we will not deal with that and decide to ignore them in analysis. However, if possible, we could find data scientist to deal with this problem.

- Some cases&#39; category are wrong, they are happened mainly in the &quot;category&quot; and &quot;description&quot; variable

  - We used Openrefine cluster function to fix this problem.
  - We only focus on the case number in a category greater than 100, which will let us save lots of time in this process (compared with 80,000+ instance, case number less than 100, could have limited impact to our result)

- We could guess some quantitative relationship between different variable, we may consider remove the variable that could be calculated by other variables and just retain them. For example, traveltime = intake time + dispatch time + travel time, totaltime = totalresponsetime + time_on_scene

  - for the blank value and 0 value, we used the formula to generate the target value and fill the blank value/ 0 value

## (3) Comment generally on the data quality of your dataset and any specific issues which arose.

- The problems in data cleaning

### 1) there are lots of instance value that we do not understand.

- for example, there are lots of similar value in variable &quot;category&quot;, but we have no idea of what it is. In variable &quot;description&quot;, the description is not very cleared. Although we could use cluster function in Openrefine to fix, but there are still some value that we have to guess.
- suggested solution

  - we could invite domain expert/ business expert to get involved into the program to provide some in-depth knowledge based on their real world experience.
  - Also, we could invite database specialist and the person who made the input rules to involved, they could all provide us opinion and suggestions
  - we could search open information on the internet
  - in dealing with location information, especially street and neighborhood information, we could use Google map to gain knowledge and correct any inconsistency, if any

### 2) there are some outliers in the data set (especially in the time-related value)

- we are not very sure why some time value are extremely high, and some value are very low (0 minutes in travel time), also there are lots of blank value
- suggested solution

  - Also, we could invite database specialist and the person who made the input rules to involved, they could all provide us opinion and suggestions

### 3) we are not sure what the abbreviations&#39; meanings are

- For example, in some instance, the category value is &quot;park&quot;, but the description value is &quot;parking complain&quot;
- suggested solution

  - we may need to change some value based on the context, which will make the analysis easier

### 4) the value in &quot;incident\_address&quot; might be inter-exchangeable, this cause the data cleaning problem

- suggested solution

  - we need data scientist to get involved to fix this problem

### 5) we do not need extremely high data accuracy for some variable

- For example, we do not need extremely high data accuracy for longitude and latitude, although high accuracy give us much better details, in this program, we do not need to specify the exact position of the call coming from, we just need to know the approximate neighborhood or zip code. We have to consider this issue when we analyze our analysis target
- suggested solution

  - based on the program requirement, we will short the longitude and latitude digit as needed.

### 6) Using cluster function to clean data might not enough to clean all data

- suggested solution

  - after cleaning data by cluster, we should review the data again, we could filter the data by alphabetical order or by count, to find out the uncleaned data with large portion (large percentage) and clean by human. For the small portion, we could just ignore them (they won&#39;t impact the result significantly)
  - we could invite domain expert/ business expert to get involved into the program to provide some in-depth knowledge based on their real world experience.

### 7) Some variable&#39;s value have lots of blank, and some values need to be filled

- suggested solution

  - for the blank data, we could use other information in the data set to fill (such as using &quot;longitude&quot; and &quot;latitude&quot; to fill &quot;neighborhood&quot; value)
  - when filling the data, we need the data scientist and domain expert to help
  - we also need map on this issue

### 8) other concerns and thinking during the data cleaning process

- we should save the data and process as the project going

  - Openrefine provides the function of history log, through which we could restore to the previous step in dealing with large data set.
  - The history log could help us to review and cross-check the whole process
  - We also need to take note when we clean the data

- For the instance or variable that we are not sure, we should keep them in the data set, in case of future use

## (4) Describe the tools used and explain why they were selected. Did they perform satisfactorily?

- We used Openrefine in data cleaning process, the main reason are listed below

  - Compared with Excel, we can use the method of cluster to deal with text within the cells
  - Openrefine supports to edit the cell in a bulk, which is much faster than Excel
  - Openrefine supports the sorting function, which is much faster than Excel in dealing with lots of data instance
  - Openrefine has high efficiency, which save lot of time
