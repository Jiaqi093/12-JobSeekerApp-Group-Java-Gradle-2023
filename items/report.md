# [G29 - Job Seekers] Report

The following is a report template to help your team successfully provide all the details necessary for your report in a structured and organised manner. Please give a straightforward and concise report that best demonstrates your project. Note that a good report will give a better impression of your project to the reviewers.

Note that you should have removed ALL TEMPLATE/INSTRUCTION textes in your submission (like the current sentence), otherwise it hampers the professionality in your documentation.

*Here are some tips to write a good report:*

* `Bullet points` are allowed and strongly encouraged for this report. Try to summarise and list the highlights of your project (rather than give long paragraphs).*

* *Try to create `diagrams` for parts that could greatly benefit from it.*

* *Try to make your report `well structured`, which is easier for the reviewers to capture the necessary information.*

*We give instructions enclosed in square brackets [...] and examples for each sections to demonstrate what are expected for your project report. Note that they only provide part of the skeleton and your description should be more content-rich. Quick references about markdown by [CommonMark](https://commonmark.org/help/)*

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
| [uid] | [name] | [role] |
| [uid] | [name] | [role] |


## Summary of Individual Contributions

Specific details of individual contribution of each member to the project.

Each team member is responsible for writing **their own subsection**.

A generic summary will not be acceptable and may result in a significant lose of marks.

*[Summarise the contributions made by each member to the project, e.g. code implementation, code design, UI design, report writing, etc.]*

*[Code Implementation. Which features did you implement? Which classes or methods was each member involved in? Provide an approximate proportion in pecentage of the contribution of each member to the whole code implementation, e.g. 30%.]*

*you should ALSO provide links to the specified classes and/or functions*
Note that the core criteria of contribution is based on `code contribution` (the technical developing of the App).

*Here is an example: (Note that you should remove the entire section (e.g. "others") if it is not applicable)*


1. **u6358055, Lingpeng Xiao**  I have 25% contribution, as follows: <br>
  - **Code Contribution in the final App**
    - Feature 
      - **LogIn, FB-Auth**: The Authentication functions are all based on the Firebase Authentication.
         - class: [Login.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Login.java), [Register.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/Register.java)
      - **Interact-Micro:** In the MainActivity, users can click the "Turn on/off sharing" button to change their current state. When a new user has been registered, the default state will be set as "true", which means other users can share jobs with this user. The user can turn off this function by clicking the "Turn off sharing" button (on the top-right corner of the screen), so other users are **blocked from sharing jobs with this user** (After clicking, the text of the button will be automatically set to "Turn off sharing"). The users can change their state whenever they hope to. User validation and state checks are implemented in this process. The users can only share jobs with other valid users who allow sharing.
         - class: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java#134-185)
      - **Interact-Follow:** On the job details page, the users can **follow the jobs** they like by clicking the "heart" button on the bottom-left corner. Duplicate checking is implemented in this process, so the users cannot save the same job. After clicking, the subscriber number of that particular job will be automatically increased by one. The users can check their saved jobs by clicking the "Saved Jobs" button on the main page. After clicking the "Saved Jobs" button, the users will enter a new page that includes all the jobs the users saved before. They can access the job details by clicking the specific job in the list. Also, there is a clear button on the top-right corner. By clicking it, all the saved jobs will be removed forever, and the related jobs' subscriber number will also decrease.
         - class: [JobDetailsActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobDetailsActivity.java), [JobListActivity](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/JobListActivity.java)
      - **Interact-Noti:** Whenever the user logs in, the application will automatically run a function to check if the user has received greater than or equal to 2 jobs from other users. If so, the main page(MainActivity) will display a toast to notify the user, which says "You have received more than 1 job".
         - class: [MainActivity.java](https://gitlab.cecs.anu.edu.au/u6358055/ga-23s2/-/blob/main/JobSeeker/app/src/main/java/com/example/jobseeker/MainActivity.java)
      - **FB-Persist:** **All the data sets, updating, and search are implemented by using the real-time database**. For example, when a new user successfully registers an account (powered by the Firebase Authentication), the user will also be automatically and synchronously added to the Realtime database by creating a new node under the root "users" with some default initialization such as the state of sharing. When the user successfully saves a new job, the job ID will be automatically and synchronously added to the node at root/users/"currentUser"/savedJob, and the value of root/jobs/"currentJob" will also increase (powered by Firebase Realtime Database). Whenever other users open this specific job's detail page, they will instantly find the subscriber number has already been changed. The rest functions such as the saved Job/received job list clearing, sharing state checking and updating, and job sharing all work in a similar way. In general, all the user interactions are powered by Firebase Authentication and Realtime Database, and every change will **synchronously update the Realtime Database**, and users can **instantly** see those changes.
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

**Others:**
- Task allocation, meeting & meeting notes organization.

-
-
-
-
-
3. **UID2, Name2**  I have xx% contribution, as follows: <br>
  - ...


-
-
-

## Application Description

*[What is your application, what does it do? Include photos or diagrams if necessary]*

*Here is a pet specific application example*

*PetBook is a social media application specifically targetting pet owners... it provides... certified practitioners, such as veterians are indicated by a label next to their profile...*

### Application Use Cases and or Examples

*[Provide use cases and examples of people using your application. Who are the target users of your application? How do the users use your application?]*



*Sid, a recent computer science graduate with no prior work experience, is eager to find a job but uncertain about the requirements.*
1. *He opens the Job Seeker application and searches for related positions in the tech industry.*
2. *The application's powerful search engine helps him narrow down his options. Now, he can view clear details of job requirements.*
*Lily, a parent, is browsing job listings when she sees an teaching position. 
She knows her daughter, Sarah, is looking for such opportunities.*
1.	*Using the share function, she sends the job listing to Sarah, making it easy for them to discuss potential career choices.*

*Max, a young professional, comes across a job posting in his field of interest, marketing.*
1. *However, he's currently not in a position to apply.*
2. *He uses the save function to bookmark the job for future reference, ensuring he won't lose track of the opportunity.*



*Here is a map navigation application example*

*Target Users: Those Seeking Skills-Related Jobs in Specific Cities*

* *Users can use the search function to enter job keywords and location. The application will list all matching results.*


*Target Users: Young Adults with No Work Experience*

* *Users can input job keywords to search for related jobs.*
* *Clicking on a specific job of interest reveals all job details and specific requirements.*
* *Users can save jobs for later use.*


*List all the use cases in text descriptions or create use case diagrams. Please refer to https://www.visual-paradigm.com/guide/uml-unified-modeling-language/what-is-use-case-diagram/ for use case diagram.*

<hr> 

## Application UML

https://app.diagrams.net/#G1hU66ZeDpgT3usKhyQBbSutgm5TbHQt2u


<hr>

## Application Design and Decisions

### Code Design and Decisions

<hr>

### Data Structures

*I used the following data structures in my project:*

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
1. [LogIn]. Description of the feature ... (easy)
   * Code: [Class X, methods Z, Y](https://gitlab.cecs.anu.edu.au/comp2100/group-project/ga-23s2/-/blob/main/items/media/_examples/Dummy.java#L22-43) and Class Y, ...
   * Description of feature: ... <br>
   * Description of your implementation: ... <br>

2. [DataFiles]. Description  ... ... (...)
   * Code to the Data File [users_interaction.json](link-to-file), [search-queries.xml](link-to-file), ...
   * Link to the Firebase repo: ...

3. ...
   <br>

### Custom Features
Feature Category: Privacy <br>
1. [Privacy-Request]. Description of the feature  (easy)
   * Code: [Class X, methods Z, Y](https://gitlab.cecs.anu.edu.au/comp2100/group-project/ga-23s2/-/blob/main/items/media/_examples/Dummy.java#L22-43) and Class Y, ...
   * Description of your implementation: ... <br>
     <br>

2. [Privacy-Block]. Description ... ... (medium)
   ... ...
   <br><br>

Feature Category: Firebase Integration <br>
3. [FB-Auth] Description of the feature (easy)
   * Code: [Class X, entire file](https://gitlab.cecs.anu.edu.au/comp2100/group-project/ga-23s2/-/blob/main/items/media/_examples/Dummy.java#L22-43) and Class Y, ...
   * [Class B](../src/path/to/class/file.java#L30-85): methods A, B, C, lines of code: 30 to 85
   * Description of your implementation: ... <br>

<hr>

### Surprised Features

- If implemented, explain how your solution addresses the task (any detail requirements will be released with the surprised feature specifications).
- State that "Suprised feature is not implemented" otherwise.

<br> <hr>

## Summary of Known Errors and Bugs

*[Where are the known errors and bugs? What consequences might they lead to?]*
*List all the known errors and bugs here. If we find bugs/errors that your team does not know of, it shows that your testing is not thorough.*

*Here is an example:*

1. *Bug 1:*
   - *A space bar (' ') in the sign in email will crash the application.*
   - ...

2. *Bug 2:*
3. ...

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
*[Write a well defined protocol your team can use to handle conflicts. That is, if your group has problems, what is the procedure for reaching consensus or solving a problem?
(If you choose to make this an external document, link to it here)]*

This shall include an agreed procedure for situations including (but not limited to):
- e.g., if a member fails to meet the initial plan and/or deadlines
- e.g., if your group has issues, how will your group reach consensus or solve the problem?
- e.g., if a member gets sick, what is the solution? Alternatively, what is your plan to mitigate the impact of unforeseen incidents for this 6-to-8-week project? 
