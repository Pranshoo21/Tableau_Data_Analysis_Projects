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
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/tree/main/Business%20case-03

### Approach

####  For our first objective -
  * We will import the .xlsx file into tableau desktop.
  * Our datasource which is coming from the excel file has three tables ListOfOrders, OrderBreakdown and SalesTarget.
  * Apllying Inner Join on [OrderID] from table ListOfOrders and OrderBreakdown (renaming as Actual Sales)

  ![image](https://user-images.githubusercontent.com/115392900/202517044-0712c987-7901-4d37-894f-58b0186b62f6.png)
  * This will give me the sales done against each orderID at different period of time.
  * Now to get the target sales we will do data blending.
  * For this we will again improt the .xlsx file as new data source and import the SalesTarget table (renaming as Target).
  * Now in order to get the target sales data we need to define relationship b/w categories of Actual Sales and Target (keeping Actual Sales as primary table).
  * To get the target sales data for different time period we need to define relationship b/w Order date of Actual Sales and Target (keeping Actual Sales as primary table).
  * We will create the visuals for our first objective
  
  ![image](https://user-images.githubusercontent.com/115392900/202522500-1b55a6bb-33a8-4cd1-9dea-ed13a579aa2b.png)
  
  ####  For our second objective
   * In order to calculate the difference b/w Actual sales and target sales we will create a calcualted field with formula = SUM([Sales])-SUM([Target].[Target]).
   * We will update our visual by adding the calculated field to show the difference in Actual sales and target sales.
    
   ![image](https://user-images.githubusercontent.com/115392900/202523554-c4bae1cd-5203-4e25-8152-ac6465a32691.png)

# **Business Case -04** Creating Dashboard using bins,parameter and donuts (Dashboard and Story)

* **Objective** - To create a customer segmentation dashboard with various visuals. The first visual is a map view which will give us the idea about the customers by state. What is the age range of our customers and what balance they have in their account, we need to create a dynamic histogram to achieve this particular visuals.
Business is also interested in finding the male and female count and for that they are looking for donut chart. Which jobs the customers are in that will give lot of understanding to the business about how to go about the offers so they need more insights about the job profile of customers. Create an interactive dashboard which will help business to take quick decisions in no time.

* **Software Used** - Tableau Desktop Public  
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/tree/main/Business%20Case%20-04

### Approach

####  For our first objective -
  * We will import the datasets into tableau.
  * To create a map view we need to have a geographic dimension. Since our field Reigon is string we will chnge the data type to geographic.
  * We will then create a map chart , and edit the location to United Kindom since the reigons are of UK, if we do don't do this tableau will not be able to mark the locations on map ( by default tableau takes the server country).
  * Putting a coutn distinct measure on Customer ID to get number of customers in each reigon.
    
 ![image](https://user-images.githubusercontent.com/115392900/202642442-601b098e-76bf-427d-9f0f-f162211c937c.png)
    
 ####  For our second objective -  
   *  In order to know the age groups of customers , we will create bins on field [Age] with bin size to 4.
   *  Then we will create histogram chart b/w Age bins and disctinct count of [Customer ID].
     
   ![image](https://user-images.githubusercontent.com/115392900/202656476-baf43d85-6931-4013-873f-774b6c334204.png)
     
   *  We can also add a dynamic bin size which gives the user flexibitly to change the bin size as per theri need.
   *  For that we will create a new parameter by using Create Parameter and going in the range section.
   *  There we will set the minimum as 5 and maximum as 30 ( that means bin size can range from 5 to 30).
   
   ![image](https://user-images.githubusercontent.com/115392900/202658404-d9647bc1-21f7-49ac-aec8-487df931c52c.png)  
     
   * Once we have created the Age bin parameter , we will link it to the field [Age(bin)] by going in edit section.
   * There we will select Size of bins as Age Bin Parameter instead of fixed value.
   * Then we will slect show parameter from the Age Bin parameter.
   * Now we can change the size of bins as per our use case with the help of slider.
   
   ![image](https://user-images.githubusercontent.com/115392900/202661869-e055abe8-e992-4b19-a9dc-801e336aebb1.png)
   
   * Now we will create another histogram for Balance by customer. This chart will give us the idea about the number of custumers falling in different amount of balance groups.
   
   ![image](https://user-images.githubusercontent.com/115392900/202665111-ad1438ee-ae20-402f-b26e-e22331db4785.png)

 ####  For our third objective - 
   *  Since our business case requires donut chart (but donut chart is not available by default in tableau) therefore we will first make a pier chart b/w [gender] and  distinct count to customers.
   *  Then we will create a calculated field with zero calculation and create the chart as shown below
   
   ![image](https://user-images.githubusercontent.com/115392900/202668422-6e3cb677-3f69-47f6-b45e-6f2e0d9d7c8d.png)

   * Then we place the below pie chart in dual axis and remove all marks for that pie chart and increase the size of first pie chart.
   * We will change the color of below pie chart to white, this will give us the required donut chart.
   
   ![image](https://user-images.githubusercontent.com/115392900/202670031-35e99a57-5fcf-427c-a409-c83fafe77203.png)

   ####  For our fourth objective -
   * We will make the chart as shown below
     
   ![image](https://user-images.githubusercontent.com/115392900/202671852-3fb39061-d0ab-4ca9-9436-a56b845bfb80.png)

   ####  For our fifth objctive  - 
   * Here we have to create a dashboard from all the charts we have created above.
   
   ![image](https://user-images.githubusercontent.com/115392900/202682434-0637f276-df8c-45fd-b694-d1ca8619ea98.png)

   # **Business Case -05** Sets and Parameters

* **Objective** - You are working in a company and you have got the data from internet where we will have our competitor's financial information. We nee to analyze where we are standing. Are we really doing well as compare to our competitors. First - Create a dynamic scatter plot with the help of sets and parameters so that user will be able to select the values as per his requirements. Second- Create the report as dynamic as possible with the help of parameters.

* **Software Used** - Tableau Desktop Public  
* **Datasets** - The datasets used for this case 


# **Business Case -06** Animations
* **Objective** - Create a dashbaord to deliver an animated report showing how populations of countries acrss the world have been developing over the last 50 years.The stakeholders of this assignment are interested to see overall trends in fertility , life expectency and population . In addition to overall tredns they would like to be able to drill into individual countries.

* **Software Used** - Tableau Desktop Public  
* **Datasets** - The datasets used for this case 

### Approach

####  Data preparation -
* Since we have data coming rom multiple tables we will do some data prep in tableau prep with following flow

![image](https://user-images.githubusercontent.com/115392900/202846213-e0d4fa81-2f2b-43f4-adf1-bc9739fc5f47.png)






   
   

   

  

