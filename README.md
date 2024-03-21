# Movie-Studio-Blueprint
![Microsoft Visual Studio Blueprint](https://github.com/Misfit911/Microsoft-Movie-Studio-Blueprint/assets/127237815/66300c64-853c-44ea-bb7b-5735ce301b0d)
## Overview
***
This project leverages data from [Box Office Mojo](https://www.boxofficemojo.com), [IMDb](https://www.imdb.com/), [The Numbers](https://www.the-numbers.com/), [TheMovieDB](https://www.themoviedb.org/) and [Rotten Tomatoes](https://www.rottentomatoes.com/) to define Microsoft's New Movie Studio Strategy. 
It sees all the big companies creating original video content and they want to get into the lucrative business prospects. 
Microsoft decided to create a new movie studio based on scientific facts through data analysis.
Here are the insights following the **exploratory data analysis** conducted:
- The movie genres **Action, Adventure & Drama** are the most popular.
- The safest budget range is ***$170,001,400$ - $255,001,400$***,  with the highest profitability index of *96.96%*.
- Summer months ***(June, July, and August)*** show strong performance in terms of both average worldwide gross and
average rating.

An overview of research recommendations include:
- **Focus on Popular Genres**: Allocate resources to produce movies in genres that are currently performing well based on box office gross and audience ratings. This can increase the likelihood of commercial success and positive audience reception.
- **Optimize Release Timing**: Use the insights from seasonal trends to strategically plan movie releases.
- **Collaborate with Industry Experts**: Engage with industry experts and professionals to complement data-driven insights with creative expertise and market knowledge, ensuring a well-rounded approach to movie production. 
***
## Business Problem
***
Microsoft wants a piece of the cake in the movie industry, however, it is limited in the domain knowledge. The research was done based on the following research questions:
1. Which are the **top performing movie genres**?
1. What are the **preferences** of the **target audience**?
1. How to **break market barriers**?

The following are the **data questions** answered in this analysis:

**1. What types of films are currently performing best at the box office (based on box office gross)?**
- What are the characteristics of top-performing movies based on box office gross?
- Which movies have been the most successful financially?

**2. Which movie genres have been the most popular and successful over time?**
- What are the trends in genre preferences?
- What are the preferences of the target audience based on user ratings and reviews? 
- What type of content resonates well with the audience?

**3. How does the movie budget impact box office revenue, and can smaller budget films be profitable?**
- How does the movie budget affect box office revenue? 
- Can smaller budget films be profitable, and is there an optimal budget range?

**4. Are there seasonal trends in movie performance, and when is the best time to release a movie?**
- Are there seasonal patterns in movie performance? 
- When is the best time to release a movie for maximum revenue?
***
## Data Understanding
***
The research retrieves information from Box Office Mojo, The Numbers and IMDb databases.

**Data Description**:
The data used for this project comes from multiple movie-related datasets from the following sources:

1. **IMDb (Internet Movie Database)**:
    - **IMDb Basics**:
       - Dataset: imdb.title.basics
       - Description: Contains basic movie information like **movie_id, primary_title, original_title, start_year,
         runtime_minutes, genres**
       - Relationship to Data Analysis Questions: Provides information on movie genres and basic movie details required for genre analysis.

    - **IMDb Ratings**:
       - Dataset: imdb.title.ratings
       - Description: Contains **'movie_id', 'averagerating', 'numvotes'**
       - Relationship to Data Analysis Questions: Allows us to explore audience preferences based on user ratings and reviews.

2. **Box Office Mojo**:
   - Dataset: bom.movie_gross
   - Description: Contains box office gross information for movies. \
   i.e **'title', 'studio', 'domestic_gross', 'foreign_gross', 'year'**
   - Relationship to Data Analysis Questions: Essential for analyzing box office success and financial performance of movies.

3. **The Numbers**:
   - Dataset: tn.movie_budgets
   - Description: Contains movie financials, like **'id', 'release_date', 'movie', 'production_budget', 'domestic_gross',
     'worldwide_gross'**
   - Relationship to Data Analysis Questions: Enables us to analyze the impact of movie budgets on box office revenue.

  Key Variables:
> performance, rating, genre, budget, revenue

Other particulars involved include:
> movie title, box office gross, user rating, release date

**Properties of Variables of interest**:
- **Movie Name**: Categorical variable which is a textual label or name of the movie. 
- **Genre**: Categorical variable representing the type or category of the movie (e.g., Action, Drama, Comedy).
- **Budget**: Continuous variable representing the production cost or budget of the movie.
- **Worldwide Gross**: Continuous variable representing the total revenue generated by the movie at the box office.
- **User Rating**: Continuous variable representing the average ratings or scores given by users for the movie.
- **Release Date**: Temporal variable indicating the date when the movie was released in theaters.

**Target Variable**:
The target variable for this project is the **"worldwide gross"** of movies. Box office gross represents the total revenue generated by the movie in theaters and serves as an indicator of movie financial success.

These variables will be used to answer the data questions and derive actionable insights to guide Microsoft's new movie studio in making informed decisions for successful movie production. The analysis will focus on understanding the relationships between these variables and their impact on movie success and profitability.
## Data Preparation
***

The following describes the conventional data cleaning process to remove inconsistencies and operate on standardized data:


1. **Data Loading**:
- Load the required datasets, including `bom_movie_gross`, `imdb`, `rt_movie_info`, `rt_reviews`, `tmdb_movies` and `tn_movie_budgets` into the analysis environment.

2. **Data Cleaning**:
- Handle Missing Values: Identify and handle missing values appropriately for each dataset. Depending on the extent of missingness, we may choose to impute missing values, drop rows, or drop entire variables if they are not crucial for the analysis.
- Drop Irrelevant Variables: Remove irrelevant or redundant variables that do not contribute to the analysis questions or recommendations.
- Merge Data: Combine relevant datasets based on common keys (e.g., movie titles) to create a comprehensive dataset that includes essential movie information.

3. **Handling Outliers**:

- Analyze and Address Outliers: Identify outliers in numeric variables like budget and box office gross. Outliers may affect our analysis, and we need to decide whether to remove or transform them based on their impact on the results.
- Consider Genre Outliers: In genre analysis, we may encounter less common or niche genres. We must decide whether to group them into broader genres or retain them as unique categories based on their significance.
4. **Feature Engineering**:

- Calculate `Profit`: Create a new variable to calculate the profit for each movie by subtracting the budget from the box office gross. This will help us understand the financial performance of each movie.
- Calculate `foreign_gross`: from the difference between worldwide gross and domestic gross.
***
## 1. Data Loading
***
Import the necessary modules and packages:
