# CS598: Theory and Practise of Data Cleaning Final Project
## End-to-End Data Cleaning Workflow

##### For MCS-DS
##### Summer 2017

## Team


- [Gitika Jain](mailto:gitikaj2@illinois.edu?Subject=CS598Project)
- [Apurva Hari](mailto:vhari22@illinois.edu?Subject=CS598Project)
- [Alok K. Shukla](mailto:alokks2@illinois.edu?Subject=CS598Project)


## Project Goal

The goal of the final project is to use various tools and techniques covered in this course together in a small end-to-end data cleaning workflow.

### 1. Overview and initial assessment

Here we describe the structure and content of the dataset and quality issues that are apparent from an initial inspection. We also describe a (hypothetical or real) use case of the dataset and derive from it some data cleaning goals that can achieve the desired fitness for use. In addition: Are their use cases for which the dataset is already clean enough? Others for which it well never be good enough? 

### 2. Data cleaning with OpenRefine

In this hands-on part of the project, we use [OpenRefine](openrefine.org) to clean the chosen dataset — as much as needed for the use case. We also document the result of this phase, both in narrative form and with supplemental information (e.g., which columns were cleaned and what changes were made?). We also quantify the results of our efforts along with provenance information from OpenRefine. 

#### *Optional* We may use other tools like R, Python for data cleaning tasks that couldn't be completed by OpenRefine.

### 3. Developing a relational database schema

We identify the *logical integrity constraints* (ICs) here after loading the data into a SQLite database with a target schema. Use SQL queries to profile the dataset and to check the ICs that we have identified.

### 4. Creating a workflow model

Here we used [YesWorkllow](https://github.com/yesworkflow-org) to create a workflow model of entire project: what are the key inputs and outputs of workflow? What are the dependencies?
We also create a visual version of your workflow using the YesWorkflow tool.

## The Data

The New York Public Library is digitizing and transcribing its [collection of historical menus.](http://menus.nypl.org/) The collection includes about 45,000 menus from the 1840s to the present, and the goal of the digitization project is to transcribe each page of each menu, creating an enormous database of dishes, prices, locations, and so on. As of early June, 2017, the transcribed database contains 1,332,726 dishes from 17,545 menus.

This dataset is split into four files to minimize the amount of redundant information contained in each (and thus, the size of each file). The four data files are Menu, MenuPage, MenuItem, and Dish. These four files are described briefly here, and in detail in their individual file descriptions below.

### Menu
The core element of the dataset. Each Menu has a unique identifier and associated data, including data on the venue and/or event that the menu was created for; the location that the menu was used; the currency in use on the menu; and various other fields.

Each menu is associated with some number of _MenuPage_ values.

### MenuPage
Each MenuPage refers to the Menu it comes from, via the menu_id variable (corresponding to Menu:id). Each MenuPage also has a unique identifier of its own. Associated MenuPage data includes the page number of this MenuPage, an identifier for the scanned image of the page, and the dimensions of the page.

Each MenuPage is associated with some number of _MenuItem_ values.

### MenuItem
Each MenuItem refers to both the MenuPage it is found on -- via the menu_page_id variable -- and the Dish that it represents -- via the dish_id variable. Each MenuItem also has a unique identifier of its own. Other associated data includes the price of the item and the dates when the item was created or modified in the database.

### Dish
A Dish is a broad category that covers some number of MenuItems. Each dish has a unique id, to which it is referred by its affiliated MenuItems. Each dish also has a name, a description, a number of menus it appears on, and both date and price ranges.

## Inspiration

What are some things we can look at with this dataset?

*How has the median price of restaurant dishes changed over time?* Are there particular types of dishes (alcoholic beverages, seafood, breakfast food) whose price changes have been greater than or less than the average change over time?
*Can we predict anything about a dish's price based on its name or description?*
- There's been some work on how the words used in advertisements for potato chips are reflective of their price; is that also true of the words used in the name of the food? 
- Are, for example, French or Italian words more likely to predict a more expensive dish?

### Data Acknowledgments

This dataset was downloaded from the [New York Public Library's What's on the menu?] (http://menus.nypl.org/) page. The What's on the menu? data files are updated twice monthly, so expect this dataset to go through multiple versions. The version we used was released on June 17, 2017, here's a [link to its backup.](https://d1b10bmlvqabco.cloudfront.net/attach/j29ig2ca7rxkr/iz0l1mgxmqg6g9/j58nqqqyoly2/NYPL_Dataset.zip) 