## Data Cleaning with OpenRefine

### Menu.csv
##### Gitika Jain

**sponsor** :

	1.	Trim leading and trailing white spaces.
	2.	Collapse consecutive white spaces.
	3.	Convert column values to upper case
	4.	Remove the special characters - *% @  # ! \ [ ] ( ) ? '*
	5.	Replace ; with a space and then trim leading and trailing white spaces and collapse consecutive white spaces. 
	6.	Make a facet and perform the cluster operation using the *key-collison* method and *fingerprint* function. Merge the relevant clusters. 
	7.	Repeat the step 6 with *n-gramfingerprint, metaphone3, cologne-phonetic* methods. 
	8.	Make a facet and perform the cluster operation using the *nearest neighbor method* and *levestein distance* function . Merge the relevant clusters. 
	9.	Make a facet and perform the cluster operation using the nearest neighbor method and *PPM distance* function. Merge the relevant clusters. 
	

The above transformation steps has been followed for **event, venue, place, occasion** and **location** columns. 

**physical_description** :

	1.	Split the column values using *semicomon (;)* as separator, we get 7 columns as a result. 
	2.	Rename the first column as *physical_description_type*.
	3.	Using the GREL function, join only the separated columns *physical_description 2*, *physical_description 3*, and *physical_description 4* into one column, separate the value using a *dash ( - )* character, 
		and name the column as *physical_description_additional*. Left the respective value as blank space if the column is null or blank. 
		In case, if the *physical_description 2* column is empty, then made *physical_description_additional* empty as well.

**date** :

	1.	Create a new column *date_clean* which is a copy of *date*. 
	2.	Convert the *date_clean* column values to *date format YYYY-MM-dd*. Also, get rid of outliers where the year is *less than 1851 and more than 2017.* 
		Replace the outliers with empty charaters. 









