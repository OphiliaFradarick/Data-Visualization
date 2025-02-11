## Power BI Analysis on Video Game Sales
 

I have selected the dataset to evaluate video game sales worldwide, mainly focusing on North America, Europe, and Japan. 
## The analysis questions are as follows:
1.	Which genres contribute the most to global sales?
2.	Are older games still popular compared to newer releases?
3.	Which publishers dominate sales in specific regions?
4.	Which publishers have the most games in the top rankings?
5.	How has the gaming industry’s total sales grown over decades?
6.	Do games released on multiple platforms perform better in global sales?

## The initial transformations applied to the dataset are as follows:
1)	Removed errors from the column years and publisher
2)	Created a new column named Regional Sales to find out the percentage of sales in North America to the global sales
3)	Applied a conditional column to check whether the game is popular
4)	Created another column named Decade. I clicked on Add column  Custom column  and wrote the following code
Text.From(Number.RoundDown([Year] / 10) * 10) & "s".
![image](https://github.com/user-attachments/assets/3d93666e-88c6-44cc-ad83-9cb7fe514421)

## STAR SCHEMA
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
 ![image](https://github.com/user-attachments/assets/fca3f370-5982-4ef3-8441-94769634da25)

To code used to create the Game_Id is as follow
 ![image](https://github.com/user-attachments/assets/aedfa85e-86ba-4e13-b732-d2b1fe1c0f44)

2)	Games_Dim
3)	Platforms_Dim
A new column is added by clicking on add column  index column  merged Platform and index column to create platform_id
 ![image](https://github.com/user-attachments/assets/081deac6-2904-4336-9e50-f0e0c00e4a33)



4)	Genre_Dim
For creating Genre_ID, I selected the column Genre and deleted the other columns. I created an index column. Followed by that created an index column by writing the following code
 ![image](https://github.com/user-attachments/assets/da5bb749-21de-4c99-bef5-4ad0c0cf556b)

The organized data with a star schema is as follows:
 
![image](https://github.com/user-attachments/assets/50ee2765-1543-4078-b9aa-bd0c6a525dec)

## 1. Which genres contribute the most to global sales?
The analysis revealed that the Action Genre has the most sales in the global economy
 
![image](https://github.com/user-attachments/assets/9c108fde-e63f-45b1-9e54-093e01f8b26d)

Included slicer for gathering more information based on the publisher. For Nintendo, the best genre is Platform games, which is a subdirectory of action.
![image](https://github.com/user-attachments/assets/7dbf6547-d609-458e-b633-bc324c283fe4)

## 2. Are older games still popular compared to newer releases?
To evaluate this, I created a new conditional column. First, I added a custom column in Power Query 
![image](https://github.com/user-attachments/assets/37be7854-8583-4c70-9bbc-84657724c4af)

I created a line chart and noticed that the sales of older games diminished, and overall, the sales of games plummeted after 2015. There was a significant increase in sales from 1990 to 2010. North America contributed the most to video game sales.  
Older games do not have that much popularity, and we came to know that video games are mostly sold in the North American regions.
![image](https://github.com/user-attachments/assets/de806f89-44e1-4ad7-b4b7-2eb463ed84be)

## 3. Which publishers dominate sales in specific regions?
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
 ![image](https://github.com/user-attachments/assets/77086fc5-41a6-4b16-856b-be7a0592b66e)

## 4. Which publishers have the most games in the top rankings?
To find the top-ranking game, I created a new column using DAX. I clicked on the Sales_Fact column and then created a new column. I wrote the DAX formula as follows:
 
 ![image](https://github.com/user-attachments/assets/b5576476-47a5-419a-b6a3-17e85c68340d)

Created a New Measure as follows:
 
 ![image](https://github.com/user-attachments/assets/ef620c69-8d4e-490f-97c5-32be9d48356f)
![image](https://github.com/user-attachments/assets/33d88bdf-37b1-4ea3-8933-6719f566a135)

I added a tabular column and Pie chart to evaluate this question across the different decades based on Ranking and sales across different regions. In the total sales column, I included conditional formatting to the background color.
 ![image](https://github.com/user-attachments/assets/dfa661b4-c0ac-44c5-82d9-8b4d4298630f)

I included a slicer to specify the rank. This analysis allowed me to evaluate that throughout the decade, Nintendo had the best games in the top rankings. The top-selling games by Nintendo in the 1980s included Duck Hunt, Super Mario Bros., and Tetris. In 2020, the lead was shared between Activision and Nintendo, with Call of Duty: Black Ops and Call of Duty: Advanced Warfare being the standout games.
 ![image](https://github.com/user-attachments/assets/f047c538-9900-40b2-b3bc-840586884887)

 ![image](https://github.com/user-attachments/assets/e5f7c4c8-e724-4fd1-b22d-4bc0f6f15eea)

## 5. How has the gaming industry’s total sales grown over decades?

 ![image](https://github.com/user-attachments/assets/bda59a2c-8d30-4a26-b03d-74c85922eb0f)


The gaming industry has experienced significant sales growth over the decades, highlighting its expanding market and opportunities. This growth underscores the importance of learning programming languages and new technologies, as they pave the way for a promising career in this thriving industry.


## Conclusion
Action games attract the most customers, with Platform games—a subgenre of action—being the best for Nintendo.  

 Older games are less popular, and video game sales are highest in North America.  
 
 For four decades, Nintendo and Electronic Arts dominated sales. Nintendo focused on North America and Japan, while EA targeted North America and Europe. By 2020, Ubisoft became the leader, with Japan as its main market.  
 
Nintendo consistently had top-ranked games, including classics like Duck Hun, Super Mario Bros, and *Tetris* in the 1980s. By 2020, Nintendo shared the spotlight with Activision, known for hits like *Call of Duty: Black Ops* and *Advanced Warfare.  

The gaming industry’s significant growth over the years highlights the importance of programming and new technologies, offering great career opportunities in this dynamic field.

