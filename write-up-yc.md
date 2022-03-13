## Datasets 
###  <a href="https://data.cdc.gov/Case-Surveillance/United-States-COVID-19-Cases-and-Deaths-by-State-o/9mfq-cb36">United States COVID-19 Cases and Deaths by State over Time</a>
 
 Aggregated by CDC according to jurisdictions' timely and accurately reports. The dataset contains new cases, total cases, new deaths, total deaths per day by state. 
 
 The dataset is mainly used in table `CovidCase`. Here are attributes in `CovidCase`:
 
| Attribute_name | data_type| Comments         |
| -------------- |----------| -----------------|
| id             | int    |id of record, used as a primary key
| submission_date| date   |Date of record
| state          | char(2)|State of record, used as foreign key
| tot_cases      | int    |Total number of cases
| tot_death      | int    |Total number of deaths
| new_case       | int    |Number of new cases
| new_death      | int    |Number of new deaths
 
* Citation: Centers for Disease Control and Prevention, COVID-19 Response. COVID-19 Case Surveillance Public Data Access, Summary, and Limitations.

## Functional Dependencies
### Table `State`(??)
![image](https://user-images.githubusercontent.com/91283368/158063725-375a0ea1-90d8-49b0-a7e5-e5bf0224ae72.png)
OR
![image](https://user-images.githubusercontent.com/91283368/158063740-46899abf-cf29-4a37-9745-4ffba84d31ad.png)

### Table `County`
![image](https://user-images.githubusercontent.com/91283368/158061908-220a3d70-241b-450f-8146-98214b131244.png)

### Table `CovidCase`
![image](https://user-images.githubusercontent.com/91283368/158060299-3fa883d8-6937-46b2-8e78-0427afcbdd0d.png)
### Table `Vaccination`
![image](https://user-images.githubusercontent.com/91283368/158063860-6351f836-396e-4504-84e3-3f73066f5ab8.png)

### Normal Form
Every "cell" has a single data -- 1NF

There's no partial dependency.--2NF
 
Every non-prime attributes is nontransitively dependent on the primary key -- 3NF

## Canned Queries
### [function] getDeathRate(cur date, state char(2))
Return the covid-19 death rate of a state in a particular day.
#### Parameters
* cur: a 'YYYY-MM-DD' format date.
* state: abbreviation of the state.

### [procedure] KMAXinNdays @startDate date, @n int, @k int
Return states with top-@k covid-19 cases during @n days starting from @startDate.
#### Parameters
* startDate: a 'YYYY-MM-DD' format date.
* n: an positive integer.
* k: an positive integer. Will return top-k states.

### [procedure] KMAXRatioinNdays @startDate date, @n int, @k int
Return states with top-@k covid-19 infection rates during @n days starting from @startDate.
#### Parameters
* startDate: a 'YYYY-MM-DD' format date.
* n: an positive integer.
* k: an positive integer. Will return top-k states.


### [procedure] KMAXDeathRatioinNdays @startDate date, @n int, @k int
Return states with top-@k covid-19 death rates during @n days starting from @startDate.
#### Parameters
* startDate: a 'YYYY-MM-DD' format date.
* n: an positive integer.
* k: an positive integer. Will return top-k states.
#### Use case
Death rate somehow reflects people's ability to handle the pandamic. If patients could receive better treatment, the death rate would be lower. 
On the other hand, we can search which states are struggling with the pandemic and assist them.
