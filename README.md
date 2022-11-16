# Tableau_Data_Analysis_Projects

# **Bussiness Case -01** Assigning bonus to employees based on their sales

* **Objective** - Create a report where management will able to see the bonus amount for employees based on the regions and the name of the employees should be like if the first name is Rahul Tiwari then it should be displayed as R.Tiwari in report.
* **Software Used** - Tableau Prep and Tableau Desktop
* **Datasets** - The datasets used for this case https://github.com/Pranshoo21/Tableau_Data_Analysis_Projects/blob/340502297fce5f2f623cfb6dc1de17d84d5ff07e/OfficeSupplies.csv

### Approach

* On looking the datasets, we observe that we don't have sales table and the first and last name of emp are in different columns.
* We will apply data manipulation techniques and use calculated field and functions to get the desired output.

####  Creating calculated field
* Creating a 'Sales' field (Units* Unit Cost) against each employee using Tableau Prep.

![Sales Field](https://user-images.githubusercontent.com/115392900/202212189-4ae38ad3-8e9e-4194-8be8-3948821ae052.png)

* Creating another field 'Name' to concatenate first character from 'First Name' and 'Last Name'.
* ![Combined name](https://user-images.githubusercontent.com/115392900/202217361-418c2ebe-6660-4618-a348-947d0265164f.png)
