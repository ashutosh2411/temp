# Inter-Planetary University Ranking System
## Requirement Specification
### Informative Ranking Criterion
* Rank Universities based on criterions listed by the user. 
* The criterion can be one or more of the following
	* Region: 
		* planet, 
		* continent, 
		* country, 
		* state, 
		* district.
	* Facilities: 
		* Area: min, max _(in acres)_
		* available branches: (languages, CSE, EE, etc.)
		* available degrees: (bachelors, honors, masters, phd, etc)
	* Academics:
		* Strength of students: min, max
		* teacher student ratio
		* Faculty strength: min, max
	* International Relations:
		* ratio of international students
		* international faculty proportion
	* Placement and Industry:
		* placement details (per department)
		* Industry collaborations
	* Research:
		* no of papers per year
		* citations per faculty
	* Others:
		* Awards
		* other rankings

### Crowdsourced reviews and ratings
* People will get a link to review the universities to their email ID. 
* Same link can be used to review any number of universities. 
* One review per University per email ID. 
* No sign up required. 
* People can rate colleges on a scale of 1 to 10.
* Following criterions can be rated
	* Placement
	* Academics
	* Research
	* Interaction
	* Industry Relation
	* Facilities (Hostel, Sports, Clubs, Medical)
* An option to include or exclude these ratings while ranking. 
* A general review of the university in 600 words or less. 

## Design Documents

### The Database
* The database will be hosted on the cloud. 
* The Information table has the following signature.
```
UniversityInfo::<*ID, Name, Address, Planet, Continent, Country, State, District, Website, Contact, Wikipedia, 
  Area, Strength_of_students, Faculty_strength, ratio_of_international_students, list_of_available_streams, 
  placement_details, no_of_papers_per_year, citations_per_faculty, international_faculty_proportion, 
  teacher_student_ratio, list_of_available_degree, etc>
```
* The Crowdsource table has the following signature.
```
CrowdSourcedInfo::<*ID, *email, Placement, Acads, Research, Interaction, IndustryRelation, Facilities, etc>
```
`*ed` attributes form the primary key. 
* There will be views which can be used to address a particular section of the table
```
LocationView::<*ID, Address, Planet, Continent, Country, State, District>
AcademicsView::<*ID, FacultyRation, etc>
```
### The UI

#### Search UI
* On the left there will be a filter side bar where you can assign min, max pairs or values for search. 
* Each value will be prefilled with default values. 
* All the options will be classified into fields, and there will be a drop down menu to reveal all fields. 
* Refer diagram. 

<pre>
                                               sort by option
</pre>
![UI](searchui.png)
Search UI design _hand-drawn_
![UI](searchUI.png)
Search UI design 

#### Review and Rate UI
* When person opens the link from his email, he will be able to rate universities. 
* He will firstly be taken to list of universities, from there he can select the university he wants to rate. 
* The UI looks like the following. 

![Rate UI](rateui.png)
Slider based UI for rating Universities _hand-drawn_
![Rate UI](rateUI.png)
Slider based UI for rating Universities

### Connecting Backend and Frontend
* Appropriate functions will be provided by backend team which will be used by the frontend team to query. 
* Appropriate outputs will be provided by the the functions which will be displayed accordingly to the ui.
## Risk Management
This was not necessary to submit, but here is a brief summary of the same. 
* Manage requirement change issues
* Manage Lack of Knowledge issues
* Manage Management issues
* Manage monetary issues

## Software Design
* Include as much abstraction as possible. 
* Modular design. Easily amendable and easily modifiable. 
* There should be functinal independence in the modules. 

## Testing Documents

### Database Testing
* Unit testing of all search functions provided by the database. 
* Unit testing of all insertion functions provided by the database. 
* Attempt to modify UniversityInfo table without proper authentication. 
* SQL injection attempt

### UI Testing
#### Search part testing
* Unit testing for each filter. 
* Unit testing for combinations of filters.
* Resizing window testing
#### Crowdsourcing part testing
* Try to use an invalid link to review. 
* multiple reviews to same university by the same person
* on inserting new ratings, check if average rating updates or not
-----------
A more detailed testing scenario is as follows. 
### Software Verification
We need to verify if we are building the software correctly. We have to do following testings to verify the product. 
* Functional Testing
* Integration and Interface testing
* System Testing
* Acceptance testing
* regression testing

### Validation testing
We also need to ensure that we are building the right thing. This is called validation. This can be done by following: 
* peer reviews
* technical reviews
* certification demonstration

### Unit testing
* For UI and for Database
* Test all Database functions
* Test UI functionalities
* Keep individual module size small. 

### Integration Testing
* Integrate the UI and the Database functions step by step. 
* Start by integrating UI and Database for searching and ranking. 
* Next up integrate UI and Database for crowdsourced reviews. 

### System Testing
* Test by running on real systems
* Database is on cloud so test from different platforms like curl, browser, etc

### Performance Testing
* Test queries from slow and fast networks. 
* check time required to search in database and time required to send data over internet. 
* find bottleneck time constraint. 

### Security testing
* Check for server overloading
* check for sql injection errors
* check for various attacks on the network and database
* check for backup of data on system  crash
