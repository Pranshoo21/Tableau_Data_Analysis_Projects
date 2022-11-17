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
* Creating another new field [Bonus] with formula =
    IF SUM([Sales])>5000 THEN SUM([Sales])*0.30
    ELSEIF SUM([Sales])>=2000 AND SUM([Sales])<=5000 THEN SUM([Sales])*0.20
    ELSE SUM([Sales])*0.10
    END)

* We have done the calculaton part that was reuquired as per the bussiness problem, now we will create the desired chart.

####  Creating data visulaization

* Creating a bar chart based on reigon and names of employees. 
* Order in descending order of bonus amount in all the reigons.
* Adding data labels and formatting the number as currency.

  ![image](https://user-images.githubusercontent.com/115392900/202396309-e7a2ac0a-910f-48a5-8a06-7293e0b065aa.png)




