## Team Members
1. Catherine Lusick
2. Emmy Nguyen (https://github.com/emmyn1)
3. Diyaa Patel
4. Caleb Rivers 

## Problem Description

## Data Model
<img width="1192" height="806" alt="DataModelProj1" src="https://github.com/user-attachments/assets/fa321764-ce20-42be-b435-b8e67da91c53" />

### Explanation of Data Model

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
| Feature                   | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 | 
|---------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Multiple Table Join       |         |         |         |         |         |         |         |         |         |          |
| Subquery                  |         |         |         |         |         |         |         |         |         |          |
| GROUP BY                  |         |         |         |         |         |         |         |         |         |          |
| GROUP BY with HAVING      |         |         |         |         |         |         |         |         |         |          |
| Multi-condition WHERE     |         |         |         |         |         |         |         |         |         |          |
| Built - in Functions      |         |         |         |         |         |         |         |         |         |          |
| REGEXP                    |         |         |         |         |         |         |         |         |         |          | 
| NOT EXISTS                |         |         |         |         |         |         |         |         |         |          | 

## Database Information









