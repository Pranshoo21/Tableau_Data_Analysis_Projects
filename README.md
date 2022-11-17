# Tableau_Data_Analysis_Projects

# **Bussiness Case -01** Assigning bonus to employees based on their sales



* **Objective** - Create a report where management will able to see the bonus amount for employees based on the regions and the name of the employees should be like if the first name is Rahul Tiwari then it should be displayed as R.Tiwari in report. The bonus for each employee shall be based on following conditions:

  ![image](https://user-images.githubusercontent.com/115392900/202388553-2c34b47b-c92c-4e99-be29-8aa0b85895c1.png)

* **Software Used** - Tableau Prep (trial version) and Tableau Public 
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/blob/340502297fce5f2f623cfb6dc1de17d84d5ff07e/OfficeSupplies.csv

### Approach

####  Creating calculated field

* On looking the datasets, we observe that we don't have sales table and the first and last name of emp are in different columns.
* We will apply data manipulation techniques and use calculated field and functions to get the desired output.
* Creating a new field [Sales] to calculate the sales dones by each employee with formula = ([Units]*[Unit Cost])
* Creating another new field [Name] with formula = LEFT([First Name],1) + '.' + [Last Name]
* Creating another new field [Bonus] with formula = IF SUM([Sales])>5000 THEN SUM([Sales])*0.3 ELSEIF SUM([Sales])>=2000 AND SUM([Sales])<=5000 THEN SUM([Sales])*0.20
    ELSE SUM([Sales])*0.10 END
* We have done the calculaton part that was reuquired as per the bussiness problem, now we will create the desired chart.

####  Creating data visulaization

* Creating a bar chart based on reigon and names of employees.
* Order in descending order of bonus amount in all the reigons.
* Adding data labels and formatting the number as currency.

  ![image](https://user-images.githubusercontent.com/115392900/202396309-e7a2ac0a-910f-48a5-8a06-7293e0b065aa.png)

# **Bussiness Case -02** Extract vs Live and Union
* **Objective** - One of the retail chains in USA looking to implement Tableau as its business intelligence needs. 
However, they have following requirements which they want to know if that is possible or not using Tableau. The requirements are as follows:

  1. Business looking for a quick reporting solution and as per them their data will get refresh on daily 
     basis but that refresh will happen after 15 hours after the previous load. Now the requirement is 
     that they does not want to have the connection with the live data and they want some snapshot 
     which can be used while reporting.

  2. One of the requirements is they need to filter the data at the very start so that there will be 
     different reports for different types of user, lets say if you are a manager of East region you should 
     connect to the report where only we help you see east data. (As of now we are not talking about 
     row level security). Also in these reports they want the live data to be connected

  3. Also next year they are planning to expand the business to Europe so they want a solution which 
     can take care of both the locations data for analysis.

* **Software Used** - Tableau Prep (trial version) and Tableau Desktop Public  
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/tree/main/Business%20case%20-02

### Approach

####  For our first objective -
  * Importing the data [US Data] and [EU Data] into tableau desktop.
  * Setting the connection types as Extract as per our use case, we can add filters to extract specific type of data from data source.
  * Setting up the refresh rate as 15 hours.
  * Saving the file as .hyper file since we have created a snapshot of the original datasource for our analysis.

####  For our second objective -
*  Importing the data [US Data] and [EU Data] into tableau desktop.
*  Setting the connection type as Live
*  Since we want that the file should be based on specific region , we can put data source filter (since we are apllying filter at the datasource level) in the starting only while importing data.
*  Applying filter for Central, East, South and West and saving the file respectibely for each reigon.

####  For our third objective -
*  Here we want the data from both US and EU to be combined as one (both have same schema).
*  Since both US and EU have same reigons name (Central, East, South and West) we need to differentiate b/w reigons of US and reigons of EU.
*  Creating Union of US Data and EU Data.
*  Creating a calculated field [Reigon1] with formula = ( IF [Country]= 'United States' THEN [Region]+ '_' + 'US' else [Region] + '_' + 'EU' END ) to get the table as shown below

   ![image](https://user-images.githubusercontent.com/115392900/202427818-c894b9c5-f6b0-4cee-8237-629643289ee4.png)

* As per our objctive we have now the the combined data of both US and EU country segregated by their reigons.

# **Bussiness Case -03** Data Blending
* **Objective** - The Project requirement is to deliver a visualization which will have details about the actual sales and the target sales by Categories.The data will be of diferent granualarity and normal data joining will not help. With the functionality of data blending create a visualization which will show the above requirements. Also create a view in the same vsualization which will help the business to understand how much the difference is from the actual sales and the target sales.
* **Software Used** - Tableau Desktop Public  
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/tree/main/Business%20case%20-02

### Approach
