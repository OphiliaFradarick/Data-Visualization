Power BI Analysis
 

We have selected the dataset to evaluate video game sales worldwide, mainly focusing on North America, Europe, and Japan. 
The analysis questions are as follows:
1.	Which genres contribute the most to global sales?
2.	Are older games still popular compared to newer releases?
3.	Which publishers dominate sales in specific regions?
4.	Which publishers have the most games in the top rankings?
5.	How has the gaming industry’s total sales grown over decades?
6.	Do games released on multiple platforms perform better in global sales?

The initial transformations applied to the dataset are as follows:
1)	Removed errors from the column years and publisher
2)	Created a new column named Regional Sales to find out the percentage of sales in North America to the global sales
3)	Applied a conditional column to check whether the game is popular
4)	Created another column named Decade. I clicked on Add column  Custom column  and wrote the following code
Text.From(Number.RoundDown([Year] / 10) * 10) & "s".
 
STAR SCHEMA
For the further purpose of evaluation, we decided to create a star schema. We split the entire dataset into different tables.
Fact Table: Contains quantitative data (e.g., sales figures, ranks) and foreign keys linking to dimension tables.
Dimension Tables: Contain descriptive data (e.g., platform details, game genres) that provide context for the facts.
Facts or measures: The facts that we are trying to analyze are the sales, profit, and customer preferences. 
Dimensions: The dimensions that we are mostly going to use are the location. 
1)	We are going to analyze which country, or region has the most sales 
2)	We are also going to analyze the top 10 games on a global scale 

Information of Dimension Tables
1)	Sales_Fact
Rank: Unique identifier or a primary key.
Global_Sales: Measure for global success.
NA_Sales, EU_Sales, JP_Sales, Other_Sales: Regional sales measures.
Foreign keys linking to dimension tables (e.g., Game_ID, Platform_ID, Genre_ID).
 
To code used to create the Game_Id is as follow
 
2)	Games_Dim
3)	Platforms_Dim
A new column is added by clicking on add column  index column  merged Platform and index column to create platform_id
 


4)	Genre_Dim
For creating Genre_ID, I selected the column Genre and deleted the other columns. I created an index column. Followed by that created an index column by writing the following code
 
The organized data with a star schema is as follows:
 

1. Which genres contribute the most to global sales?
The analysis revealed that the Action Genre has the most sales in the global economy
 

Included slicer for gathering more information based on the publisher. For Nintendo, the best genre is Platform games, which is a subdirectory of action.
 
2. Are older games still popular compared to newer releases?
To evaluate this, I created a new conditional column. First, I added a custom column in Power Query 
I created a line chart and noticed that the sales of older games diminished, and overall, the sales of games plummeted after 2015. There was a significant increase in sales from 1990 to 2010. North America contributed the most to video game sales.  
Older games do not have that much popularity, and we came to know that video games are mostly sold in the North American regions.

3. Which publishers dominate sales in specific regions?
I used the decade column as the slicer to find out which publisher sustained in each region across the decade. I added the publisher in the x-axis and then in the Y-axis, I added the data for sales in Europe, in Japan, and then in North America.
The result is as follows:
For four decades, Nintendo and Electronic Arts dominated video game sales. Nintendo's main markets were North America and Japan, while EA focused on North America and Europe. In 2020, Ubisoft took the lead, with Japan as its primary sales region.
Decade	Publisher with the most Sales	Region of Sales
1980	Nintendo	North America and Japan
	Electronic Arts	North America
1990	Nintendo	North America and Japan
	Electronic Arts	North America
	Sony	North America
2000	Nintendo	North America, Japan, and Europe
2010	Nintendo	North America, Japan, and Europe
	Electronic Arts	North America and Europe
2020	Ubisoft	North America and Europe
	Konami	Japan and North America
	Sega	Japan and North America
	Sony	North America and Europe
 
4. Which publishers have the most games in the top rankings?
To find the top-ranking game, I created a new column using DAX. I clicked on the Sales_Fact column and then created a new column. I wrote the DAX formula as follows:
 
 
Created a New Measure as follows:
 
 
I added a tabular column and Pie chart to evaluate this question across the different decades based on Ranking and sales across different regions. In the total sales column, I included conditional formatting to the background color.
 
I included a slicer to specify the rank. This analysis allowed me to evaluate that throughout the decade, Nintendo had the best games in the top rankings. The top-selling games by Nintendo in the 1980s included Duck Hunt, Super Mario Bros., and Tetris. In 2020, the lead was shared between Activision and Nintendo, with Call of Duty: Black Ops and Call of Duty: Advanced Warfare being the standout games.
 
 
5. How has the gaming industry’s total sales grown over decades?
1980s
 	1990s
 
2000s
 	2010s
 

The gaming industry has experienced significant sales growth over the decades, highlighting its expanding market and opportunities. This growth underscores the importance of learning programming languages and new technologies, as they pave the way for a promising career in this thriving industry.

