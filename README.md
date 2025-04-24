### Fall 2023
### Final Report
### CyberTRIP
[Jump to easy to understand pictoral view](#Context-Diagram)

## Introduction
CyberTRIP, short for Cyber Triage & Response Incident Platform, is a comprehensive web-based
tool designed to simplify how cybersecurity incidents are tracked, managed, and prioritized in real-time.
Motivated by the need for an integrated environment in security operations centers, this project was
meant to simplify and optimize cybersecurity incident response. It stands out by integrating external
cybersecurity tools naturally into a single, user-friendly dashboard, offering not just real-time incident
tracking and management, but also the capability to add, save, search, and easily generate statistics on
incidents. It includes all the key features of an incident response tool, while avoiding any unnecessary or
distracting extras. The platform's ability to generate incident statistics to export data in formats like CSV
further extends its utility outside the tool.

The project was conceptualized to satisfy the needs of security operations center analysts, who
required a powerful yet intuitive tool to enhance their efficiency in responding to security incidents.
Many of these tools can be overwhelming and overly complex. The uniqueness of CyberTRIP lies in its
all-in-one solution approach, where different types of incident responses can be managed and accessed
via an integrated dashboard. This ensures that digital assets remain secure while significantly
streamlining the workflow for addressing cybersecurity incidents. CyberTRIP's design also reflects an
understanding of the complexity and uniqueness of cybersecurity incident response, which comes from
my cybersecurity internship experience. In my experience, I found that
integrated access to a variety of tools in one interface would be desirable. With this platform, the aim is to
facilitate the most common workflows that not only address basic responses but also adapt to the
evolving landscape of cybersecurity threats.



## Challenges
The development of CyberTRIP faced several challenges, especially in making sure the different
parts of the program, each using distinct technologies, worked well together. Each component needed to
be carefully created to ensure they functioned smoothly as a unified system with other components. For
example, the Mongo database stored data in BSON format, while other components needed to have the
data in JSON format. 

Another of the primary challenges faced was ensuring the security and
privacy of potentially sensitive data. Since this is a web application potentially accessible to people
outside of the desired user environment, it must be ensured that all the data was transmitted and stored
securely. This was not just a technical issue, but a requirement, given the nature of the program. To
address this, security measures were implemented including encryption at rest using bcrypt to
securely store user passwords and session management using a secret key to prevent session hijacking.
Certificates were used to encrypt data in transit for https transfer, which protects it against
eavesdropping. The Python cryptography library function was implemented to secure the data
stored in the Mongodb.

Another significant challenge was the integration of various external APIs, each with its own
unique format and authentication method. This required a careful and methodical approach, as the desire was to create a 
user-friendly experience. It began with a simple API at first, urlscan, and created a
way a user could click on any link in the incident notes to trigger the urlscan API. There were a few issues
with the event listeners and the fact that the API has a built-in wait time for responses. This was dealt with
by adding a countdown timer and had the results page load in a pop up at the correct time.

The user interface had a few of its own challenges, particularly in terms of creating a design that
was both user-friendly and capable of displaying diverse types of information. Prior knowledge of JavaScript and MongoDB was utilized 
to develop an interface that was simple to interact with. It was found that some technologies like Flask and Jinja were needed. Although
prior Python and basic web programming was known, learning flask was crucial. It was necessary to learn
because it’s fundamental tool for automated handling of web sessions, requests, and responses and
routing them to the Python code so that the correct html templates can be displayed. It was also discovered
that a tool called Gunicorn to manage web requests on the AWS server was needed.

Finally, the decision to make the platform web-based introduced issues related to development
and testing. Hosting and scalability were additional considerations beyond hosting the program on one development machine. The decision to initially
host locally and use GitHub for version control was a good approach for initial development, allowing
for controlled testing and gradual addition of features. As the basics progressed and were found to be
working as planned, it was moved to cloud services. AWS was selected for its ease of setup and scalability,
which makes it easy to demonstrate a proof of concept for a realistic multi-user tool for incident
response. There were a few problems where the exact same program functioned differently on Ubuntu on
AWS versus a single windows machine, but they were minor cosmetic issues. Environment variables were created
within the AWS server for security rather than hard code them in the application.


In summary, the challenges were handled well with a combination of existing experience with
MongoDB and JavaScript, and the willingness to learn new technologies like Flask and Jinja. The
approach took careful planning, trial and error, and clear decision-making to keep things moving.

## Highlights
The CyberTRIP project has reached significant milestones that emphasize its core purpose and
functionality. A major achievement of this project is the creation of an efficient and user-friendly
platform, tailored to simplify the management of cybersecurity incidents. One of the standout features of
the platform is its ability to integrate external cybersecurity tools into a unified dashboard using their
API. This integration plays a crucial role in streamlining the workflow for security analysts, decluttering
their workspace, and enhancing the speed and accuracy of their incident response. It is also easy to access
by simply clicking on any url in an incident.

Key functionalities of CyberTRIP include real-time tracking and management of security
incidents. Users have the capability to create, store, search, and manage a variety of incident reports,
which is fundamental for comprehensive cybersecurity analysis. The platform allows for detailed
searching across all fields of an incident report, identifying indicators of compromise and other critical
information. Additionally, it offers a feature for creating and assigning tasks related to specific incidents
to analysts, with the ability to monitor different status levels.

Another important aspect of CyberTRIP is the option to delete incidents, further maintaining the
relevance and accuracy of data within the system. Enhancing its investigative capabilities, the platform
enables users to click on any URL within a field to conduct an external search via the Urlscan site for
additional information. This feature significantly increases the platform’s capacity for proactive threat
identification.

The project also has support for multiple concurrent users through Gunicorn, with the platform
being hosted on AWS, ensuring global accessibility. Further, the ability to export incidents and related
data to a CSV file adds to the platform's versatility, which enables users to use the data in other platforms
if needed. In terms of security, CyberTRIP includes encrypted sessions and features like an invalid login
timeout, prioritizing the protection of user data and system integrity.

Throughout its development, CyberTRIP has been shaped by the need for a simple and efficient
design, influenced by ongoing feedback from stakeholders. This approach ensured that every feature
implemented was powerful and satisfied the practical needs of users. The iterative Agile development
process, combined with the flexibility in adopting new technologies such as Flask and Jinja, along
with experience with MongoDB and JavaScript, was useful in creating a platform that is both
advanced and intuitive.

In conclusion, the development of CyberTRIP shows that a compact, efficient, and
easy to use incident response platform can be created and used for basic workflows within a security
operations center.


## Top 4 Significant Project Decisions

### UI Development and Database Integration (Date: 10-12-2023)

●
Motivation: To create a user-friendly interface for creating and searching incidents.
●
Consequences: Achieved a functional UI with essential features like login/logout and
general incident creation and searching by any field .


### API Integration (Date: 10-27-2023)

●
Motivation: To provide easy clickable access to real-time data from external cybersecurity
tools.
●
Consequences: Enhanced the platform's capability to present immediate threat
assessments. Urls stored anywhere in an incident can be clicked on to trigger the API and
generate a report.


### Hosting on AWS EC2 (Date completed: 10-26-2023)

●
Motivation: To improve accessibility and reliability to multiple simultaneous users.
●
Consequences: The application became more accessible, enhancing real-world
applicability. It was also easier to test and use at the same time for developers.


### Task Management Feature (Date completed: 10-29-2023)

●
Motivation: To streamline incident response workflow by adding task information
associated with an incident.
●
Consequences: Improved the organizational aspect of incident management. Tasks can be
assigned to specific analysts with a todo list and a status attribute.

## Requirements

## User Involvement

In the development of CyberTRIP, user involvement in the design process was an important
aspect, ensuring the platform met the specific needs and expectations of its primary users – the Security
Operations Center analysts. I was a junior analyst who routinely uses similar
software, so this was very helpful when designing the interface and functionality. 
Along with the SOC managers as stakeholders, everyone played an important role in shaping the project’s
trajectory. Interactions with them through feedback sessions and prototype demonstrations were useful in
refining the platform's functionalities and user interface.

## User Needs
The primary motivation behind the stakeholders' needs was to create an intuitive, efficient
platform that not only tracks and stores incident data but also allows for simple and inexpensive access to
external cybersecurity tools. This helped lead to the creation of specific SMART user stories, detailing
user needs rather than specific technological implementations.

## Top 5 User Stories
·
1. As a Security Analyst, I want to view results from various external cybersecurity tools within 20
seconds directly from the dashboard by clicking a link, so that I can make quick decisions and use the
results efficiently.
·
2. As a Security Analyst, I need to be able to search for and update incidents in less than three mouse
clicks through a simple, uncluttered dashboard, so that response times to incidents are significantly
reduced compared to other incident response-platforms.
·
3. As an IT Manager, I want the platform to be versatile and able to handle at least 3 different types of
incidents like Phishing, DOS, and Malware using one incident interface so that the data is centralized and
I do not have to use several different solutions.
·
4. As a Security Analyst, I require the ability to search for Indicators of Compromise (IoCs) across all
incidents, so that rapid threat identification and response and separate incidents can be correlated. The
search results should be available within 5 seconds and able to be sorted by field.
·
5. As a Supervisor, I want to assign tasks within incidents to specific users, ensuring clear action steps
and accountability with progress tracking in incident management. I should be able to select the status of
the task from a list of at least 4 choices including new, in progress, and completed. I should also be able
to assign one of 4 priority types to each task.

### Problem Definition

Many modern incident response programs are large, messy, and have a steep learning curve.
Many of them have features that are rarely used which can distract from basic workflows in incident
response. Further, some incident-response platforms try to handle too many tasks and possibilities. There
are, however, some good ones which were small and efficient, like The Hive for example, which was
researched and learned from. The problem CyberTRIP aimed to solve was providing a simple, general
purpose, and efficient system to benefit cybersecurity incident management for SOC analysts and
managers. This was achieved through the development of key use cases:


Top 3 Use Cases

Use Case 1: Centralized IoC Management
User Goal: Analysts need to efficiently input, save, and search Indicators of Compromise (IoCs) within a
centralized system to enable rapid threat identification and response.

Basic Flow:
1.
The analyst logs into the unified cybersecurity dashboard.
2.
They select an existing case or create a new one, accessing the centralized IoC repository.
3.
The analyst inputs new IoCs into the case, using integrated API tools for format consistency and
accuracy.
4.
The system confirms the successful addition of IoCs and updates the case details.
5.
The analyst utilizes the search functionality to cross-reference new IoCs with past incidents or
known threat patterns.
6.
Relevant threat information, predictive insights, or statistics based on the entered IoCs are
displayed to the analyst using local data and external APIs.
7.
The analyst proceeds with formulating response strategies based on the IoCs' analysis results.


Alternative Flows:
"IoC Input Anomalies": The system detects inconsistencies or errors in the entered IoCs, prompting the
analyst for verification or correction. This could be due to invalid format etc.
*Attaches to Basic Flow: This flow occurs after Step 3 if the IoCs input meets certain error conditions
detected by the system.
"System Search Unavailability": Temporary unavailability of search function due to technical issues,
requiring system support. This could be a database error or network error for example.
*Attaches to Basic Flow: This flow comes into play if a system error occurs at Step 5, causing search
functions to fail.

Use Case 2: Enhanced Incident Response with Task Management
User Goal: Analysts and supervisors coordinate incident response strategies by associating tasks with
specific cases, ensuring clear action steps and accountability.
Basic Flow:
1. The supervisor reviews the case with IoCs and analysis results, identifying the need for specific
response measures.
2. Within the case details, the supervisor creates a list of tasks, outlining clear actions required for
incident containment and mitigation.
3. Each task is assigned to specific analysts or teams, with set deadlines and priority levels.
4. Assigned analysts receive notifications about their tasks, access them directly through the centralized
system, and view pertinent IoC information.
5. Analysts update task statuses upon completion or mark stages as they progress, keeping the supervisor
informed in real-time.
6. The supervisor monitors task completion statuses, provides additional guidance, and prepares for
post-incident reviews.

Alternative Flows:
"Incomplete Task Specifications": Occurs when tasks are created without sufficient detail, necessitating
clarification or additional input from supervisors. This happens sometimes when templates aren’t used.
*Attaches to Basic Flow: This issue arises after Step 2, where the task creation is deemed incomplete or
lacking essential details.
"Delayed Task Execution": Analysts face impediments that delay the timely execution of assigned tasks,
compromising incident response times.
*Attaches to Basic Flow: This flow becomes relevant if, after Step 4, analysts report or encounter
unforeseen delays or issues.

Use Case 3: Comprehensive Case Review and Statistical Analysis
User Goal: Users aim to conduct thorough post-incident reviews and generate detailed statistical
analyses based on saved case data and associated IoCs.
Basic Flow:
1. Post-incident, the user accesses the completed case, reviewing all associated data, IoCs, and task
outcomes.
2. The user initiates a statistical analysis feature, selecting parameters based on IoCs, response times, task
efficacy, and other relevant factors.
3. The system processes accumulated case data, generating comprehensive statistics and detailed reports.
4. The user reviews these insights, identifying successful strategies, areas needing improvement, and
patterns in threat behavior.
5. Insights from the analysis are used to update best practices, enhance future response strategies, and
inform proactive defense mechanisms.

Alternative Flows:
"Insufficient Data for Analysis": The system identifies gaps in case data, limiting the comprehensiveness
of statistical reports.
*Attaches to Basic Flow: This occurs after Step 2 if the selected parameters for analysis lack sufficient
backing data.
"Inconsistent Analysis Reports": Generated statistics or patterns appear inconsistent or unreliable,
prompting a review of the data inputs or analysis methodologies.
*Attaches to Basic Flow: This problem arises at Step 4, where users notice discrepancies or
questionable data in the reports.

Each use case was developed with the user's role, goals, and the basic workflow in mind. Each
use case also satisfies the overall objective of enhancing SOC efficiency and effectiveness. The
development of CyberTRIP was driven by an emphasis on designing with a general purpose SOC in
mind, continually modified by feedback from stakeholders which helped add and improve features over
time.

### Significant Project Design Decisions
System Overview
The system consists of the homepage where users can learn about the site, create accounts and
login and the dashboard view where users can navigate to pages for creating and viewing details of
and statistics about incidents. The main challenges of building the system were keeping the site
secure and formatting data in a way that MongoDB would recognize but was still easy to access on
the frontend.

The decision to use Flask as a framework and MongoDB as a database were the main decisions
that shaped how the system was laid out. Flask was chosen because of previous
experience using it and it is a popular framework that offered longterm support and lots of
documentation. MongoDB was chosen because it is a NoSQL database that allows high customization
of record storage. 

A consequence of the decision to use MongoDB was that some data needed to be converted to json serializable format before it was stored. A positive consequence was that the
website is not vulnerable to SQL injection because MongoDB is a NoSQL dbms. The decision to
separate normal and super users also affected the system because data had to be partitioned based on
the permissions of the user.

## Context Diagram

![Page 9 Image 1](img/page9_1.jpeg)

Architectural View

![Page 10 Image 1](img/page10_1.jpeg)

The diagram shows the flow of information for a person using the site. They will first see the home page,
then log in, then gain access to the main components of the site. From these components, they can create
incidents, view details about and add tasks to specific incidents, and view statistics to identify trends
across multiple incidents. The database provides inputs for viewing incidents and the statistics related to
them. External APIs such as URLscan.io provide input on the page to create incidents so the user can
view additional information about links or other threats.

Element Catalog
1. Homepage:
●
Responsibility: The homepage serves as the user interface entry point, providing options
for users to log in or create a new account.
2. Login:
●
Responsibility: The login component is responsible for authenticating users, ensuring
secure access to the system.
●
Significant Decisions: Separation of normal and super-user types to determine what
information is available
3. View Stats:
●
Responsibility: This component is responsible for presenting statistical information about
created incidents, offering insights into system performance or relevant metrics.
●
Significant Decisions: Used Chart JS


4. Create Incident:
●
Responsibility: The Create Incident component facilitates the generation of new incidents,
storing relevant data in MongoDB.
●
Significant Decisions: Originally users had to choose to store incidents in MongoDB but
the process was switched to automatic saving on the creation of a new incident for
prevention of accidental data loss. Incidents also needed to include enough information to
be searchable and easily sorted for statistics
5. View Incident:
●
Responsibility: This component allows users to retrieve and view information about
existing incidents, retrieving data from MongoDB.
●
Significant Decisions: This page needed to access routes to interact with mongoDB for
searching and deleting incidents
6. MongoDB:
●
Responsibility: MongoDB serves as the database element, storing and retrieving data
related to created incidents. Its responsibility includes efficient data management and
retrieval.
7. External API:
●
Responsibility: The External API component is responsible for interacting with external
services or systems, enabling the system to integrate and exchange information with
external entities.
●
Significant Decisions: Stored API key in environment variables for security and
implemented a timer to match with URL Scan.io’s security timer when making API calls,
URLs in the notes section of created incidents are automatically submitted to URL Scan
API.

4. Status


Home page

![Page 12 Image 1](img/page12_1.png)
Sign Up
![Page 12 Image 2](img/page12_2.png)
Login functionality
![Page 12 Image 3](img/page12_3.png)


Creating an Incident
![Page 13 Image 1](img/page13_1.png)
Url Scan API
![Page 13 Image 2](img/page13_2.png)

Viewing existing incidents
![Page 13 Image 3](img/page13_3.png)

Search Incidents
![Page 14 Image 1](img/page14_1.png)

Delete Incidents
![Page 14 Image 2](img/page14_2.png)


View Individual Incidents
![Page 15 Image 1](img/page15_1.png)

Add Tasks
![Page 15 Image 2](img/page15_2.png)

Edit Tasks
![Page 15 Image 3](img/page15_3.png)

Viewing statistics
![Page 16 Image 1](img/page16_1.png)

Logout
![Page 16 Image 2](img/page16_2.png)



## Architectural View

From the architectural view, the data from Create Incident is saving to the MongoDB. View Statistics
and View Incidents is correctly retrieving data from MongoDB. The External APIs are correctly
returning information to the user. Login is allowing the user to View Statistics, Create Incidents,
View Statistics, and interact with External APIs.

## Tests Run

All of the Acceptance tests as well as other tests such as multiple users on the website at
once.

## Lines of Code Written

1722 lines in html files
866 lines in css files
775 lines in python
3363 lines total. Possibly closer to 3500 with other files needed to deploy the website in
production on the EC2 instance.

