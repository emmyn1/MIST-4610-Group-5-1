## Team Members (Group 5)
1. Catherine Lusick (https://github.com/cl95728/MIST-4610-Group-5-Project-1)
2. Emmy Nguyen (https://github.com/emmyn1/MIST-4610-Group-5-1)
3. Diyaa Patel (https://github.com/Diyaa-P13/MIST4610---Project-1-Group-5.git)
4. Caleb Rivers 

## Scenario Description
The purpose of this relational database is to model a music group that distributes songs and albums from a variety of different artists that are signed to various different subsidiary record labels. The model tracks artists, albums, songs, record labels, contracts, and revenue generated through both streaming and unit sales, with the central entity being the artists, as their products are the source of revenue.  Managers can use the system to assess artist performance, identify high-performing genres and locations, and make strategic choices about talent acquisition, contract management, and marketing. Through querying the database, our team aims to prove that our database is both reliable and useful for helping the executive team gain insight into the current operations of the music group, as well as ensuring that it can be used to make decisions about the future of the firm.

## Data Model
<img width="1192" height="806" alt="DataModelProj1" src="https://github.com/user-attachments/assets/fa321764-ce20-42be-b435-b8e67da91c53" />

### Explanation of Data Model
The database features the entities Artist, Artist Group, Album, Song, Producer, Song Producer, Song Record Label, Location, Sales, Total Units, and Streams Total. 

Record Label represents the subsidiary that each artist is signed to. It is the child table of location, as a location could include many record labels. Other attributes include the albums unique identifier, it’s name, the city in which it is headquartered in, and the year it was founded 

Location represents the relevant areas that house producers, record labels, and artists. Since none of these entities can have more than one location, the entity has no foreign keys. state 
  - Each Artist has a single Record Label and a single Location 
  - An Artist may put out more than one Album 
  - There are several Songs on each Album 
  - Songs generate streaming data through the Stream Total table 
  - Unit Total and Sales tables are how albums make money 
  - A junction table links Producers to Songs  

## Data Dictionary

### Artist Table
| Column Name | Data Type | Description |
|------------|----------|------------|
| artistID | INT | Unique identifier for each artist |
| legalName | VARCHAR | Artist's legal name | 
| stageName | VARCHAR | Artist's stage name |
| debutDate | INT | Year that artist debuted | 
| artistAge | INT | Current age of the artist | 
| locationID | INT | References the artist's location | 
| recordLabelID | INT | Foreign key referencing the record label associated with the artist |

### Artist Group
| Column Name | Data Type | Description |
|------------|----------|------------|
| groupID | INT | Unique identifier for a collaboration group involving multiple artists on a song |
| artistID | INT | Foreign key referencing an artist participating in the group | 
| songID | INT | Foreign key referencing the song associated with the group collaboration | 
| groupName | VARCHAR | Name of the artist group or collaboration | 

### Location
| Column Name | Data Type | Description |
|------------|----------|------------|
| locationID | INT | Unique identifier for each location | 
| state | VARCHAR | State abbreviation where the location is based | 
| city | VARCHAR | City name of the location | 
| zipCode | INT | ZIP code associated with the location | 

### Contract
| Column Name | Data Type | Description |
|------------|----------|------------|
| contractID | INT | Unique identifier for each contract | 
| startDate | DATE | Date the contract begins | 
| endDate | DATE | Date the contract ends | 
| royaltyRate | DECIMAL | Percentage of revenue paid to the artist | 
| advanceAmount | DECIMAL | Upfront payment given to the artist | 
| albumQty | INT | Number of albums required under the contract | 
| artistID | INT | Foreign key referencing the artist associated with the contract | 

### Record Label
| Column Name | Data Type | Description |
|------------|----------|------------|
| recordLabelID | INT | Unique identifier for each record label | 
| labelName | VARCHAR | Name of the record label | 
| hqCity | VARCHAR | City where the laebl is headquartered | 
| yearFounded | INT | Year the record label was established | 
| locationID | INT | Foreign key referencing the location of the record label | 

### Album 
| Column Name | Data Type | Description |
|------------|----------|------------|
| albumID | INT | Unique identifier for each album | 
| albumName | VARCHAR | Name/title of the album | 
| releaseDate | DATE | Date of the album was released | 
| artistID | INT | Foreign key referencing the artist who created the album | 
| unitsSoldID | INT | Foreign key referencing the units sold record associated with the album | 

### Song 
| Column Name | Data Type | Description |
|------------|----------|------------|
| songID | INT | Unique identifier for each song |
| songTitle | VARCHAR | Title of the song | 
| songDuration | VARCHAR | Duration of the song in minutes and seconds | 
| songGenre | VARCHAR | Genre classification of the song | 
| explicit | VARCHAR | Indicates whether the song contains explicit content (Yes/No) |
| trackNumber | INT | Position of the song within the album | 
| albumID | INT | Foreign key referencing the album the song belongs to | 
| streamTotalID | INT | Foreign key referencing the total streaming data for the song | 

### Producer
|Column Name | Data Type | Description |
|------------|----------|------------|
| producerID | INT | Unique identifier for each producer | 
| producerName | VARCHAR | Name of the music producer | 
| producerAge | INT | Age of the producer | 
| locationID | INT | Foreign key referencing where the producer is based in | 

### Song Producer 
|Column Name | Data Type | Description |
|------------|----------|------------|
| songProducerID | INT | Unique identifier for each song-producer relationship |
| producerID | INT | Foreign key referencing the producer associated with the song | 
| songID | INT | Foreign key referencing the song associated with the producer | 

### Sales
|Column Name | Data Type | Description |
|------------|----------|------------|
| salesID | INT | Unique identifier for each sales record | 
| revenueAmount | DECIMAL | Total revenue generated from sales | 

### Unit Total 
|Column Name | Data Type | Description |
|------------|----------|------------|
| totalUnitsID | INT | Unique identifier for each total units record | 
| totalUnitsQty | INT | Total number of units sold for a given record | 
| salesID | INT | Foreign key referencing the associated sales record |

### Stream Total 
|Column Name | Data Type | Description |
|------------|----------|------------|
| streamID | INT | Unique identifier for each streaming record | 
| streamQty | INT | Total numnber of streams for a given record | 
| salesID | INT | Foreign referencing the associated sales record | 

## SQL Queries 
1. Show all of the albums for a specific artist.
Query 1 retrieves album names and release dates for a specific artist by filtering the Album table using the artist’s ID. It provides a simple view of the artist’s discography. 
<img width="494" height="422" alt="image" src="https://github.com/user-attachments/assets/8f59d9cd-2b94-4c30-bbd1-831f760cf593" />

This query gives management quick access to an artist’s portfolio of work and track their release history. Understanding an artist’s output is important for planning future releases and activities. It also provides an idea of an artist’s content production and an overview of their career progression. 

2. Which songs are the most popular based on streaming?
Query 2  retrieves song titles and their total stream counts by joining the Song and Stream Total tables. It ranks songs in descending order and returns the top 10 most-streamed tracks.
<img width="637" height="455" alt="image" src="https://github.com/user-attachments/assets/f89a0daa-434a-4387-8344-65d8a4014b0b" />

This query allows management to have a better understanding of which songs are currently the most popular among listeners. High streaming numbers indicate strong audience engagement and can guide the company’s promotion decisions. The results can also be utilized to maximize revenues from streaming platforms. 

3. Which albums have sold above 9,000,000 albums?
Query 3 retrieves album names and total units sold by joining Album and Unit Total tables. It filters for albums exceeding 9,000,000 units and orders them from highest to lowest sales. 
<img width="572" height="527" alt="image" src="https://github.com/user-attachments/assets/f8765f24-3ad1-40be-bd7c-f54947fb62e5" />

This query helps management identify which albums are performing well in terms of sales volume. By focusing on high-selling albums, the label can prioritize its resources for the successful projects. This insight can guide future investment strategies and production decisions. 

4. Which hip hop feature has the most streams?
<img width="582" height="540" alt="image" src="https://github.com/user-attachments/assets/b897fd12-9e13-4e4e-af9b-d84d73dbb40e" />


5. Where should we look for new talent? (Which location generates the most revenue)
<img width="682" height="424" alt="image" src="https://github.com/user-attachments/assets/e5f3c581-04b3-4061-ac98-74e800fb7bb4" />



6. Do pre or post 2000s albums generate the most sales?
<img width="590" height="426" alt="image" src="https://github.com/user-attachments/assets/b2cfa90b-3ec2-4d70-83a5-595eef353904" />



7. Which record label has released the most albums? 
<img width="403" height="391" alt="image" src="https://github.com/user-attachments/assets/c3c59e79-c2bb-4955-bd2d-c5b3674fcaae" />

This query calculates the total number of albums released by each record label by joining the Album, Artist, and Record Label tables. It organizes the data by record label and counts the number of albums linked to each label, and then it arranges the results in descending order. This query assists management in determining which record labels are generating the most albums. Being able to identify which label is effectively, provides insight into overall label performance and market presence. This data can help make decisions about investments, resource distribution, and collaborations with successful labels.  

8. Which artists have more total album sales than the average total sales of all artists 
<img width="719" height="327" alt="image" src="https://github.com/user-attachments/assets/291eb264-03b5-4dc7-a3da-190ef2f03c75" />

This query calculates the total album sales for each artist by joining the Artist, Album, and Unit total tables. By comparing, each artist’s total sales to the average total sales across all artists using a subquery, it returns only those artists whose sales are higher than the average. This query assists management in determining artists who are exceeding average sales performance. These insights can help make decisions regarding marketing spending, resource distribution, contract extensions, and focusing on top-performing artists within the company.  

9. Which locations have a city name that ends with “ville” (REGEX)
<img width="499" height="336" alt="image" src="https://github.com/user-attachments/assets/72f5115c-6b84-4d35-9db0-2c73ce667f44" />

Query 9 was created to pull a list of all cities in the Location table that ends with the letters "ville". To make the list clean and easy to read, I used a Regular Expression to find the pattern and grouped the results by city. This query helps filter through the location data more effectively. Instead of scrolling through rows of data, this helps identify specific areas based on their name.

10. Display producers who have never worked on a song in the Hip Hop genre (NOT EXISTS) 
<img width="469" height="298" alt="image" src="https://github.com/user-attachments/assets/76b68c18-c9e1-40e5-8afe-d8c20e1f83dd" />

Query 10 is designed to find the names of producers in the Producer table who have never been associated with a "Hip Hop" song. To do this, I used a NOT EXISTS subquery to filter anyone linked to that specific genre. For every producer, the subquery checks the Song Producer table to see if they are linked to any song labeled 'Hip Hop'. If the subquery finds any match, NOT EXISTS becomes false, and that producer is excluded. This logic can be used to isolate producers who work exclusively in other genres like Country or Pop. It’s a great way to find a music producer whose specialty does not fall in Hip Hop. 


| Feature                   | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 | 
|---------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Multiple Table Join       |         |    X    |    X    |    X    |    X    |    X    |    X    |    X    |         |    X     |
| Subquery                  |         |         |         |    X    |         |         |         |    X    |         |          |
| GROUP BY                  |         |         |         |         |         |         |    X    |    X    |         |          |
| GROUP BY with HAVING      |         |         |         |    X    |         |         |         |         |         |          |
| Multi-condition WHERE     |         |         |    X    |         |         |         |         |         |         |          |
| Built - in Functions      |         |    X    |    X    |    X    |    X    |    X    |    X    |    X    |         |          |
| REGEXP                    |         |         |         |         |         |    X    |         |         |    X    |          | 
| NOT EXISTS                |         |         |         |         |         |         |         |         |         |     X    |
| WHERE Clause              |    X    |         |         |         |         |         |         |         |         |          |
| Basic SELECT              |    X    |         |         |         |         |         |         |         |         |          |

## Database Information
Name of the database: al_Group_21482_G5 








