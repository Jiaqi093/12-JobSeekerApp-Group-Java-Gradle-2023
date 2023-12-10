# [G29 - Job Seekers] Report

## Table of Contents

1. [Team Members and Roles](#team-members-and-roles)
2. [Summary of Individual Contributions](#summary-of-individual-contributions)
3. [Application Description](#application-description)
4. [Application UML](#application-uml)
5. [Application Design and Decisions](#application-design-and-decisions)
6. [Summary of Known Errors and Bugs](#summary-of-known-errors-and-bugs)
7. [Testing Summary](#testing-summary)
8. [Implemented Features](#implemented-features)
9. [Team Meetings](#team-meetings)
10. [Conflict Resolution Protocol](#conflict-resolution-protocol)

## Administrative
- Firebase Repository Link: <https://console.firebase.google.com/project/signup-login-bf5e6/overview?hl=en-us>
   - Confirm: I have already added comp21006442@gmail.com as a Developer to the Firebase project prior to due date.
- Two user accounts for markers' access are usable on the app's APK (do not change the username and password unless there are exceptional circumstances. Note that they are not real e-mail addresses in use):
   - Username: comp2100@anu.edu.au	Password: comp2100
   - Username: comp6442@anu.edu.au	Password: comp6442

## Team Members and Roles
The key area(s) of responsibilities for each member

| UID   |  Name  |   Role |
|:------|:------:|-------:|
| [u6358055] | [Lingpeng Xiao] | [Software Developer, Project Tester] |
| [u7581655] | [Jiaqi Zhuang] | [Software Developer] |
| [u7604844] | [Jialin Wang] | [UI designer, Software Developer] |
| [u7465735] | [Yunkai Xu] | [Software Developer] |


## Summary of Individual Contributions

1. **u6358055, Lingpeng Xiao**  I have 25% contribution, as follows: <br>
  - **Code Contribution in the final App**
    - Feature 
      - **LogIn, FB-Auth**: The Authentication functions are all based on the Firebase Authentication.
         - class: [Login.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Login.java), [Register.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Register.java)
      - **Interact-Micro:** In the MainActivity, users can click the "Turn on/off sharing" button to change their current state. When a new user has been registered, the default state will be set as "true", which means other users can share jobs with this user. The user can turn off this function by clicking the "Turn off sharing" button (on the top-right corner of the screen), so other users are **blocked from sharing jobs with this user**.
         - class: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java#134-185)
      - **Interact-Follow:** On the job details page, the users can **follow the jobs** they like by clicking the "heart" button on the bottom-left corner.
         - class: [JobDetailsActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java), [JobListActivity](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobListActivity.java)
      - **Interact-Noti:** Whenever the user logs in, the application will automatically run a function to check if the user has received greater than or equal to 2 jobs from other users. If so, the main page(MainActivity) will display a toast to notify the user, which says "You have received more than 1 job".
         - class: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
      - **FB-Persist:** All the user interactions are powered by Firebase Authentication and Realtime Database, and every change will synchronously update the Realtime Database**, and users can **instantly** see those changes.
         - related class: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java), [JobDetailsActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java), [JobListActivity](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobListActivity.java), [OffShareState.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OffShareState.java), [OnShareState.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OnShareState.java), [ShareState.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/ShareState.java), [StoreChangeObserver.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/StoreChangeObserver.java), [Share.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Share.java)
      - **UI-Test:** : I generated some UI tests (powered by espresso) to test the layout of sevral pages.
         - class: [LoginUITest.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/LoginUITest.java), [MainActivityUITest.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/MainActivityUITest.java), [RegisterUITest.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/RegisterUITest.java)
              
    - **Observer Design Pattern** 
      -  Interface: [update()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Observer.java)
      - Class: [IncreaseNumObserver: update()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/IncreaseNumObserver.java), [StoreChangeObserver: update()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/StoreChangeObserver.java)
    - **State Design Pattern**
      -Interface: [changeState(),updateData()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/ShareState.java)
      - Class: [OffShareState: changeState(),updateData()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OffShareState.java), [OnShareState: changeState(),updateData()](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OnShareState.java)

   - **Code and App Design** 
      -  State, singleton and observer design pattern

   - **Others**: (only if significant and significantly different from an "average contribution") 
      - Set up all the Firebase related functions, including building a Firebase project and connected it to the android project, set up all the firebase related dependencies, etc. 
      - Set up espresso.
      - Slides preparing.
      - Writing testing summary of report.
      - Do the presentation.
      - Create meeting notes.

2. **u7581655, Jiaqi Zhuang**  I have 25% contribution, as follows: <br>

   - **Code Contribution in the final App**  
      - **Job list on Main page**
         - **Description:** Read the data from JSON file, and then display all the data on the main page (2500 data) with job name, company name and work type.
         - **Class:** MainActivity.java

      - **Search function**
         - **Description:** User can use the search function to find the job they want based on the key word. I use tokenizer to splits the keyword and use parser to extract the useful information, where user need to input with structure i.e., Career Name, Location. Then, the new list of job will be related to the keywords in the career name which all have same location as what user search.
         - **Class:** Tokenizer.java, Parser.java, MainActivity.java

      - **detailed job list page**
         - **Description:** When user try to click one item on the front-page job list or searched page job list, (for example, click the job called Web developer), then it will bring the user to the corresponding job with detailed information (i.e., more information of this Web developer)
         - **Class:** JobDetailsActivity.java

**Code and App Design:**
- I designed the Singleton pattern on my AVL Tree in order to make sure the data storage is consistant. I also collaborate with LingPeng, Xiao on designing the Observer design pattern.
- I use AVL tree to store all the data from the JSON file with the node location and the value is an Arraylist of JSON object jobs. Make sure the tree is balanced, so I implement the rotate function which reduce the time cost of the tree search function.

3. **u7604844, Jialin Wang**  I have 25% contribution, as follows: <br>
   - **Code Contribution in the final App**  
      - **Share function**
         - **Description:** The Share function allows user to share job listings. It allows users to input an email address and verifies its validity. The function further checks whether the recipient allows job sharing and takes appropriate actions to share the job listing, providing feedback messages to the user based on the sharing status. This feature ensures effective communication of job opportunities among users while considering recipient preferences. 
         - **Class:** Share.java

**Code and App Design:**
- Data generate: Using web crawling techniques to gather data from various sources and AI tool, ChatGPT to generate, integrate 2500 job datas with necessary attributes.
- UI design
The UI design using a Designed a custom theme in Android Studio to create a visually cohesive user interface. The key design elements are defined through XML, and additional visual assets and styles are applied using a custom theme. The custom theme aims to give the app a unique and branded appearance. It allows app follow a consistent and cohesive visual style. This helps in enhancing the user experience and making the app visually appealing. Additionlly, using Adobe Illustrate to design a logo that seamlessly aligns with Jobseeker. Next, infuse Jobseeker’s identity by seamlessly swapping out the generic Android loading screen logo with our own logo. 


**Others:**
- Task allocation, meeting & meeting notes organization.

4. **u7465735, Yunkai Xu**  I have 25% contribution, as follows: <br>
**Code Contribution in the final App**
   - **Read Json file form local**
      - **Description:** Read the data from JSON file, and let it can be used by other functions.
      - **Class:** [MainActivity.java line 372-399](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
         
   - **Convert CSV file to Json file(feature [Data-Formats])**
      - **Description:** Read the data from JSON file and CSV file, merge them then write in a new Json file.
      - **Class:** [Converter.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Converter.java)

**Code and App Design:**
   - Collaborate with LingPeng, Xiao on designing the job list

**Others**:
   - Code debuging. Such as, search logic issue and job data not mactch problem in job list.
   - Fix the repreat data problem in data files.
   - Bundle app into a standalone APK.
   - Task allocation, meeting notes organization.

## Application Description

*Job Seeker is a job finding application specifically targeting young people and parents who want to share jobs with their children. It provides powerful search engines to help them find jobs. It has a share function that allows users to share a job with each other and a save function to store jobs for later use. The most important aspect is that the listed jobs are trustworthy, with no scams and detailed information, including company names, making it easy for users with no work experience to verify.*

### Application Use Cases and or Examples

*Sid, a recent computer science graduate with no prior work experience, is eager to find a job but uncertain about the requirements.*
1. *He opens the Job Seeker application and searches for related positions in the tech industry.*
2. *The application's powerful search engine helps him narrow down his options. Now, he can view clear details of job requirements.*

*Lily, a parent, is browsing job listings when she sees an teaching position. 
She knows her daughter, Sarah, is looking for such opportunities.*
1.	*Using the share function, she sends the job listing to Sarah, making it easy for them to discuss potential career choices.*

*Max, a young professional, comes across a job posting in his field of interest, marketing.*
1. *However, he's currently not in a position to apply.*
2. *He uses the save function to bookmark the job for future reference, ensuring he won't lose track of the opportunity.*

*Target Users: Those Seeking Skills-Related Jobs in Specific Cities*
* *Users can use the search function to enter job keywords and location. The application will list all matching results.*


*Target Users: Young Adults with No Work Experience*
* *Users can input job keywords to search for related jobs.*
* *Clicking on a specific job of interest reveals all job details and specific requirements.*
* *Users can save jobs for later use.*
<hr> 

## Application UML

https://app.diagrams.net/#G1hU66ZeDpgT3usKhyQBbSutgm5TbHQt2u


<hr>

## Application Design and Decisions

### Code Design and Decisions

<hr>

### Data Structures

*We used the following data structures in my project:*

1. **AVL Tree**
   * *Objective: used for storing JSON file job data for search feature.*
   * *Code Locations: the whole AVLTreeSingleton.java*
   * *Reasons:*
      * The search complexity of the AVL tree's search method is based on the height of the tree. Since it is balanced (use balance and rotate function), so the search complexity for this AVL tree is Olog(n) where n is the number of nodes in the tree.
      * By using this data structure, we will not need the index of the data anymore, so the search time complexity will be largely reduced (than a linear search).


2. **ArrayList<JSONObject>**
   * Objective: Store JSON objects which have the same "location" attribute.
   * Code Locations: AVLTreeSingleton.java -> node.java constructor
   * *Reasons:
      * Since we use the Location as the node to store the data, we still need to have further filter on the career name. Thus, we use the linear search O(n) complexity to do the keyword matching. If the data will be increasing, we can update the search function by using binary search etc. which is easy to be implemented.

<hr>

### Design Patterns

1. **Singleton Pattern**
   * Objective: Used for data consistent in AVL Tree
   * Code Location: AVLTreeSingleton.java
   * *Reasons:*
      * In order to make sure we only have one AVL Tree (to avoid multiple instances, data inconsistent, and cause confusion to the developers), so we use singleton to make sure there is only one instance for the AVL Tree.

2. **Observer Pattern**
   * Objective: Used for subscribe update notification
   * Code Location: Observer.java, IncreaseNumOvserver.java, StoreChangeObserver.java
   * Reasons: 
      * Once the user press the subscribe (heart) button, there will be auto update that the subscribe number will increase by one, and the subscribed job will be automatically added to the saved job page. These are both update method but with different behaviour, so we design the observer design pattern to notify all updates at once.

3. **State Pattern**
   * Objective: Used for receive or not receive sharing emails
   * Code Location: Share.java, ShareState.java, OffShareState.java, OnShareState.java
   * Reasons: 
      * we consider there is a scenario that parents want to share the jobs to their child where children are really annoying about this (because children only want to apply the job they want, not from their parents suggestions). So, we designed the state pattern where user can decide whether to receive the job shared by others or not, where the sharing state is a good idea of applying state design pattern.

<hr>

### Parser
Production Rules:

   * tokens_list ::= keyword, location | empty, location
   * keyword   ::=  STRING
   * location    ::=  STRING


### <u>Tokenizers and Parsers</u>

* I used tokenisers and parsers in the AVLTreeSingleton.java. Basically, when user input the search data, we want our user to follow this pattern i.e., keyword, location, so that it is easily for me to use the split method to extract the keyword and location respectively in tokenizer.java. Then, I can use location as the node to store / search the data, and use keyword for the further search data, which my search function is fully based on this gramma. The advantage of using this is, I do not need to consider varieties of different cases as we have limited software engineering experience, and we could not expect what user is going to input, this can reduce the complexity of the Programming.

<hr>

## Implemented Features
*[What features have you implemented? where, how, and why?]* <br>
*List all features you have completed in their separate categories with their featureId. THe features must be one of the basic/custom features, or an approved feature from Voice Four Feature.*

### Basic Features
1. [LogIn]. Users must be able to log in (not necessarily sign up). (easy)
   * Code: [Entire page of Login.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Login.java)

2. [DataFiles]. Description of the job data in json file. (easy)
   * Code to the Data File [job_seek_data.json](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/res/raw/job_seek_data.json), [csv_data.csv.xml](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/res/raw/csv_data.csv)

3. [LoadShowData] When a user is logged in, load data (from the file(s) and/or Firebase) at regular time intervals,
and visualise the same in the App. (e.g., If the main page contains a list of featured products, the user may see
an increased number of products; as well as receive notifications from interactions simulated from the data
stream). (medium)
4. [Search] Users must be able to search for information on your app. (medium)
The application is dependent on your app theme. E.g., search for information of products, users, by certain
criteria (e.g. #apple $1-2).
   <br>

### Custom Features
* [Link to the Firebase repo](https://console.firebase.google.com/project/signup-login-bf5e6/overview?hl=en-us)

Feature Category: Firebase Integration <br>
1. [FB-Auth]. Use Firebase to implement User Authentication/Authorisation. (easy)
   * Code: 
      - [Login.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Login.java)
      - [Register.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Register.java)

   * Description of your implementation: The Authentication functions are all based on the Firebase Authentication.

2. [FB-Persist]. Extension: Without restarting, the app should be updated synchronously as the remote database (Firebase) is updated. This means that users will be able to see the instant updates from another user/content provider. (hard)
   * Code:
      - [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
         - checkNumberOfReceivedJobs(), line 112 - 131
         - setSharingStateListener(), line: 138 -158
         - updateShareButtonLabel(), line: 165 - 171 
         - toggleShareState(), line: line: 138 - 158
      - [JobDetailsActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java) 
         - shareJobs button, line: 157 - 171
         - clear button, line:165 - 172
      - [JobListActivity, clear button, listview](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobListActivity.java)
      - [OffShareState.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OffShareState.java)
      - [OnShareState.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/OnShareState.java)
      - [ShareState.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/ShareState.java)
      - [StoreChangeObserver.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/StoreChangeObserver.java)
      - [Share.java, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Share.java)

   * Description of your implementation: **All the data sets, updating, and search are implemented by using the real-time database**. For example, when a new user successfully registers an account (powered by the Firebase Authentication), the user will also be automatically and synchronously added to the Realtime database by creating a new node under the root "users" with some default initialization such as the state of sharing. When the user successfully saves a new job, the job ID will be automatically and synchronously added to the node at root/users/"currentUser"/savedJob, and the value of root/jobs/"currentJob" will also increase (powered by Firebase Realtime Database). Whenever other users open this specific job's detail page, they will instantly find the subscriber number has already been changed. The rest functions such as the saved Job/received job list clearing, sharing state checking and updating, and job sharing all work in a similar way. In general, all the user interactions are powered by Firebase Authentication and Realtime Database, and every change will **synchronously update the Realtime Database**, and users can **instantly** see those changes.

Feature Category: User Interactivity <br>
1. [Interact-Micro]. The ability to micro-interact with items/users (e.g. like, block, connect to another user, etc.). (easy)
   * Code: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
      - setSharingStateListener(), line: 138 -158
      - updateShareButtonLabel(), line: 165 - 171 
      - toggleShareState(), line: line: 138 - 158

   * Description of your implementation: In the MainActivity, users can click the "Turn on/off sharing" button to change their current state. When a new user has been registered, the default state will be set as "true", which means other users can share jobs with this user. The user can turn off this function by clicking the "Turn off sharing" button (on the top-right corner of the screen), so other users are **blocked from sharing jobs with this user** (After clicking, the text of the button will be automatically set to "Turn off sharing"). The users can change their state whenever they hope to. User validation and state checks are implemented in this process. The users can only share jobs with other valid users who allow sharing.

2. [Interact-Follow]. The ability to ‘follow’ items. There must be a section that presents all the items followed by a user, grouped and order. (medium)
   * Code: 
      - [JobDetailsActivity.java, subscribe button](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java): subscribe button, line: 187 - 239  
      - [JobListActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobListActivity.java): 
         - clear button, line:165 - 172
         - addListenerForSingleValueEvent(), line 96 - 136  
         - decreaseSubscribeNum(), line 200 - 232

   * Description of your implementation: On the job details page, the users can **follow the jobs** they like by clicking the "heart" button on the bottom-left corner. Duplicate checking is implemented in this process, so the users cannot save the same job. After clicking, the subscriber number of that particular job will be automatically increased by one. The users can check their saved jobs by clicking the "Saved Jobs" button on the main page. After clicking the "Saved Jobs" button, the users will enter a new page that includes all the jobs the users saved before. They can access the job details by clicking the specific job in the list. Also, there is a clear button on the top-right corner. By clicking it, all the saved jobs will be removed forever, and the related jobs' subscriber number will also decrease.

3. [Interact-Noti]. The ability to send notifications for interactions (e.g., follow request, product viewed, etc.). A notification must be sent only after a predetermined number of interactions are set [e.g., when ≥2 requests have been received or 2 follow requests have been received). (medium)
   * Code: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java): 
      - checkNumberOfReceivedJobs(), line 112-131.

   * Description of your implementation: Whenever the user logs in, the application will automatically run a function to check if the user has received greater than or equal to 2 jobs from other users. If so, the main page(MainActivity) will display a toast to notify the user, which says "You have received more than 1 job".

4. [Interact-Share] The ability to share an item to another user via private message or other channels within the App. [stored in-memory]. (easy)
   * Code: [Class Share.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Share.java) and [Class JobDetailsActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java)
      - line 152-169
      
   * Description of your implementation: Whenever the user click the share button in JobDetailsActivity, the application will automatically go to share page and automatically store the jobID from the JobDetailsActivity. When user type in the email and click send, it will check whether the email is a valid user email, if it is, a toast will shown says the job is shared and the job will be sent to corresponding user, otherwise, a toast will says the share is failed. 

   <br><br>   

Feature Category: UI Design and Testing <br>
1. [UI-Test]  Complete UI tests using espresso (not covered in lectures/labs) of reasonable quality and coverage of the App. (hard)
   * Code: [LoginUITest.java, entire page](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/LoginUITest.java), [MainActivityUITest.java, entire page](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/MainActivityUITest.java), [RegisterUITest.java, entire page](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/RegisterUITest.java)

   * Description of your implementation: Some UI tests (powered by espresso) were created to test the layout of sevral pages.

Feature Category: Greater Data Usage, Handling and Sophistication <br>
1. [Data-Formats]. Read the data from local JSON file and CSV file, merge them and write in a new Json file.
   * Code: [Converter.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Converter.java)

   * Description of your implementation: When a user login, the local CSV and Json file will be merged to a new Json file and saved in local.

<hr>


### Surprised Features

- If implemented, explain how your solution addresses the task (any detail requirements will be released with the surprised feature specifications).
- State that "Suprised feature is not implemented" otherwise.

<br> <hr>

## Summary of Known Errors and Bugs

1. *Bug 1: Sharing Job Bug*
   - When share job with an incorrect email, the sharing still works. For example, if a user's exact email is abc@gmai.com, other users can use adc.@gmail.com. or a.b.c@gmail.com to share job with this user.
   - The reason is when we store the users in the Realtime Database, we use user's email as the root. While the special character such as "\\." is not allowed to be stored. So we chose to remove all the dots of user's email and then add the shorten email to the database. Therefore when we do the checking, we cannot detect the dots issues.
   - To fix this issue, we can add another data node under each user's root to store the index of dots. So when we check the email, we can use the data to re-assemble the user's email and use the correct email to do the email validation checking.   

2. *Bug 2: Low API/SDK version*
   - Due to a version problem, when following the video on bundling the app into a standalone APK, the minimum SDK version was set to 22. However, the `fromHtml()` method, which was imported in the `JobDetailsActivity.java` class, requires at least version 24. This led to errors. Nevertheless, the app can still run. 


<br> <hr>


## Testing Summary

1. UI Test with espresso

   - Code:
     [LoginUITest](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/LoginUITest.java) for the [LoginActivity, entire UI](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Login.java)
     [MainActivityUITest](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/MainActivityUITest.java) for the [MainActivity, UI of fixed content](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
     [LoginUITest](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/androidTest/java/com/example/jobseeker/RegisterUITest.java) for the [LoginActivity, entire UI](hhttps://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Register.java)
   - _Number of test cases: 5_
   - _Code coverage: The displayed content of buttons and views, the click behaviour and input behaviour._
   - _Types of tests created and descriptions:_
     - Displayed content test: use .check(matches(withHint())) and .check(matches(withText()) to test if the displayed contents are required.
     - Input test: Use .perform(typeText()) to simulate the typing behaviours and test if they work.
     - Button clicking test: Use .perform(click()) methods to simulate the clicking behaviour and test if it works.
     

2. AVL Tree Unit Test with JUnit4

   - Code:
     [AVLTreeTest](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/test/java/com/example/jobseeker/AVLTreeUnitTest.java) for the [AVLTreeSingleton, AVLtree insertion and searching function](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/AVLTreeSingleton.java)
   - _Number of test cases: 4_
   - _Code coverage: AVL Tree insertion, insert sigle data in each address and mutiple data under the same address. Search valid and invalid data._
   - _Types of tests created and descriptions:_
     - Single data insertion and search test: Insert sigle data for several different locations, and test if they can be correctly searched.
     - Multiple data insertion and search test: Test insertion of multiple jobs with the same location in the AVLTree.
     - Non-exist data search test: Test searching for a non-existent location in the AVLTree.

3. IncreaseNum Observer Unit Test with JUnit4

   - Code:
     [IncreaseNumObserverUnitTest](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/test/java/com/example/jobseeker/IncreaseNumObserverUnitTest.java) for the [IncreaseNumObserverUnitTest, entire file](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/IncreaseNumObserver.java)
   - _Number of test cases: 2_
   - _Code coverage: The all functions of this observer class._
   - _Types of tests created and descriptions:_
     - Increase the subscriber number test: Test the update method of IncreaseNumObserver by verifying if it increments the input number correctly.

...

<br> <hr>


## Team Meetings

### Meetings Records

- *[Team Meeting 1](meeting1.md)*
- *[Team Meeting 2](meeting2.md)*
- *[Team Meeting 3](meeting3.md)*
- *[Team Meeting 4](meeting4.md)*
- *[Team Meeting 5](meeting5.md)*

<hr>

## Conflict Resolution Protocol
- *[Conflict Resolution Protocol](Conflict Resolution Protocol)*
