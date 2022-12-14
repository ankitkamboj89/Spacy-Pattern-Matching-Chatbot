# Spacy-Pattern-Matching-Chatbot
The project is to create a rule based, job seeker chatbot to assist a user through conversation with as they look for a job.

The Task:
The project is to create a rule based, job seeker chatbot to assist a user through conversation with as they look for a job.

This project's dataset includes job descriptions written in natural language, as well as structured data on the city, job categories, and salary scale. The job descriptions will be processed as part of the project.

A user can enquire about various jobs, filter based on input information and review those jobs that match their description. Due to the complexity, the chat bot possesses the ability to handle multi-turn discussion.

Data:
The data provided is from the the job searching website Seek.com where many companies post looking for future employees.

The csv for Australian job listings from Seek job board has 30,000 observations and 12 variables.

category
city
company_name
geo
job_board
job_description
job_title
job_type
post_date
salary_offered
state
url
Many of these have issues in the data such as character artifacts from text encoding and missing data.

Job description field is the variable of interest, however, giving the various ways in which people write job descriptions there are many issues in this column. Luckily, where the job description lacks the information, the structured fields can work to combine the information and make it usable.

Data Processing
TF-IDF Implemenetaiton
Document Frequency (dft) is defined as the number of documents in the collection that contain a term.

Inverse Document Frequency (IDF) gives a bonus to words that appear frequently in a document but not across the full document collection. Essentially, a higher document frequency works against a word's rating.

The TF-IDF allows as to remove stop words and make similarity comparisons between documents. This can be used in ranking the users outputs or in classifying a piece of text across different categories.

Remove Stop Words & Place in Column
I am using the TF-IDF process to remove stop words and words that provide little meaning to text differentiation. The remaining words are then stored in a column within the dataframe.

Feature Engineering
Creating Salary Range Extract salary values and normalize the communication. For example, convert 70k into 70,000.

Creating Required Experience Column Extract information about the required experience for a role. This also involved converting titles such as junior, graduate, and senior into values for searching filters.

Rule Based Matching Functions
Chat Bot Setup
Bot Process:
Greet the user and await input
Parse input and determine input fields and values.
if fields found:
filter based on fields
If many items found:
Ask user for more data and filter again
if yes:
prompt user to add a filter
if no:
got to showing jobs
if neither but filter detected:
go back and apply filter if cannot determine:
ask the user what they want to do
If a reasonable amount is returned:
Ask the user to go through results
if yes:
go to showing jobs
if no:
ask what they want to do
if neither but another filter detected:
go back and apply filter
if cannot determine:
ask the user what they want to do
If no matches found:
Tell the user to broaden search
else
Ask the user to rephrase
Once user has confirmed they wish to see results, show top 5 and await input
if input is 'next'
show the next five matches
if the user enters a number
Show the job description to the user and await response
if back, return to jobs
If at any time the user says "reset", "end" or other variant:
clear values and start again.
Chatbot Outcome
Instead of typing into telegram again and again, this functions simulates the user inputs and can therefore run tests much more effectively.

These functions could be extracted to formalized tests however, I did not have time to implement this. The logs show all the information required though.

Example process & outcome.

For more see the output in the notebook.

![image](https://user-images.githubusercontent.com/110649581/190499096-8136cfc3-47bf-4133-a9bc-50484dcf570c.png)

![image](https://user-images.githubusercontent.com/110649581/190499122-1921ea8e-19b4-4fc4-b507-ad9cf791cb37.png)

![image](https://user-images.githubusercontent.com/110649581/190499138-35ba5fe2-30dc-4dcb-a876-be68728ce187.png)
