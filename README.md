# HTML Link
https://gweb22.github.io/CarSpecs_WebScraper/

# Project Overview
### Purpose
This project's main goal is to optimize parking space assignments for vehicles at The Warehouse Apartments parking lot and parking garage by providing management with a detailed report of each vehichle's dimmensional specifications. 

### Initializing Data
The data is ingested from the "WH_Fall_2023_Parking.csv" file which includes each future resident's vehicle make, model, and year (if provided). 

### Data Cleaning
Utilizing the __Tidyr__ and __Stringr__ packages, the data undergoes a meticulous cleaning process. This involves data transformations such as correcting inconsistent vehicle make and model entries, refining the model year entry, and reformatting make and model strings for consistency.

### Data Scraping
Employing the __Rvest__ and __Httr__ packages, this code chunk defines two custom-built web scraping functions:
* The __YearLookUP__ function scrapes Cars.com to gather all of the available model years.
* The __SpecLookUP__ function:
	* (1) Determines if a model year was provided.
		* (1b) If the year was not provided the YearLookUP function is run for the given make and model, thus providing a model year.
 	* (2) Using the Rvest and Httr packages the Length, Width, and Height of the vehicle are scraped from cars.com by identifying the approporiate CSS selectors and scraping the vehicle data within the specific HTML table.
  * (3) Various backups are in place if the initial web scrape is unsuccessful:
  	* (3b) Scraping surrounding CSS selectors if the HTML table returns as empty
  	* (3c) Scraping various other vehicle information sites such as Edmunds and Motor Trend.
  	* (3d) Scraping the Google Search page for the specific vehicle's dimmensions as a final catch-all

### Applying Functions to Data
Implementing the __Purrr__ package, the __SpecLookUP__ function is applied to the cleaned data, returning the same whpark data set with an added column that includes each vehicles dimmensional specificaitions.

### Cleaning and Subsetting
The new column is reformatted and divided into Length, Width, and Height columns to allow for further arrangement possibilities; I arragned the data in ascending order by width as that measure is the most pertinent for the given project. Additionally, I subset the data into 4 new data frames, organized by parking spot type.

### Exporting Files
Finally, the data is exported as an XLSX file providing the management team with a user-friendly format that facilitates seamless accessibility and utilization.
