---
layout: page
title: CinemaScope
subtitle: Lens on Gender Shifts
cover-img: /assets/img/header.png
thumbnail-img: /assets/img/header.png
share-img: /assets/img/header.png
---
<div style="text-align: justify">
    Movies have long held a mirror to society and offered viewers the opportunity to share different experiences and
    emotions. While doing this, movies generally focus on emotions such as sadness and joy and see the reflection of
    society. In this context, it struggles with the problem of gender bias, which is also seen in daily life. So how did
    this effort manifest itself in the process?
    <br><br>
    Let's generally examine the status of gender representation in the movie
    industry from many aspects such as the effect on career trajectories and collaborative opportunities and its impact
    on the results obtained and its change over time.
</div>

## The Dataset
<div style="text-align: justify">
<strong>Main Dataset:</strong>  CMU Movie Summary Corpus which is collected by the Machine Learning Department of Carnegie Mellon University. This data includes Movie metadata consists of release date, runtime, movie language, box office revenue, countries and Character metadata consists of character names, actors, gender, age at the time of movie release. In addition to this, they also provided plot summaries and Stanford CoreNLP-processed summaries which is the version of plot summaries that run through the Stanford CoreNLP pipeline.
</div>

<div style="text-align: justify">
    <p><strong>Additional Datasets:</strong> To perform detailed analysis, we preferred to use datasets that will support our analysis.</p>
    <span>1) Data collection by us:</span><br>
    <span>We collected additional data by following the below steps:</span><br>
    <ul>
        <li>Dataset creation using Freebase IDs and Wikidata API to extract IMDb IDs.</li>
        <li>Utilization of the TMDB API for acquiring gender information of cast and crew members.</li>
        <li>The results are stored in movie_with_gender_info.csv file, that can be found in the repository.</li>
    </ul>
    <span>2) Oscar Awards Dataset from Kaggle: </span><br>
    <span>Analyzing Oscar awards data by gender, focusing on nominee and winner gender proportions, revealing industry gender biases and progress towards equality in film awards. The dataset can be found in <a href="https://www.kaggle.com/datasets/unanimad/the-oscar-award/data?select=the_oscar_award.csv">Oscar Award Dataset</a></span><br><br>
    <span>3) IMDB Rating Dataset:</span><br>
    <span>As a success measure, IMBD ratings are used in the analysis. The data is taken from IMDB Non-commercial datasets. Only the files titled 'title.ratings.tsv.gz' and 'title.basics.tsv.gz' are utilized for this analysis. The datasets can be found in <a href="https://developer.imdb.com/non-commercial-datasets/">IMDB Ratings Datasets</a></span><br>
</div>

## Research Questions
<div style="text-align: justify">
    In the scope of this analysis, we will try to answer the following research questions:<br>
    <span>1) How does gender impact actors' career opportunities, collaborations and success, particularly in terms of the types of role and reward opportunities offered?</span><br>
    <span>2) Do plot summaries contain any gender stereotypes, and if so, in what manner?</span><br>
    <span>3) Does semantic analysis of character types reveal any distinct differences in the assignment of roles based on gender?</span><br>
    <span>4) Does the gender composition of cast and crew influence the critical success of films, evaluated by IMDb ratings?</span><br>
    <span>5) Are there specific movie genres that demonstrate a minimal or no gender gap in terms of character representation?</span><br>
</div>

## General Analysis based on Time

<h3>The Change in the Number of Movies</h3>
{% include interactive_chart.html %}

<div style="text-align: justify"> It is seen that there are movies between 1900 to 2016. However, between 2010 and 2015 it is observed that there is less value in contrast to the increasing trend in time. So, we decided to use the data which we have found more reliable which is 1900 to 2010.</div>

<h3>The Change in the Number of Female vs Male Characters</h3>
<div style="text-align: justify"> We did the same time based analysis based on the gender. The below graph shows the number of female and male characters in the movies for the specific time interval. It is observed that in all times the number of male characters outnumbers the number of female characters. </div>

{% include gender_time.html %}

## Gender Impact on Actors' Career Opportunities, Collaborations and Success

<h3>Analysis for Reward Opportunities based on Gender</h3>

<div style="text-align: justify;">
In this analysis, we utilized the Oscar Rewards dataset along with CMU Movie dataset. 
</div>

| Gender      | Not Nominated | Nominated | Won |
|-------------|---------------|-----------|-----|
| **Females** | 48,374        | 124       | 38  |
| **Males**   | 84,692        | 118       | 33  |

<div style="text-align: justify; margin-top: 10px;">The number of actors that nominated/win Oscars at least once are 151. There are also actors that are nominated multiple times, even  one actor is nominated/win at most 11 times in the dataset. After this, we got each actors' first nomination year and calculate the number of movies they appeared before and after their first nomination seperating based on gender.</div>
<h4>Average Number of Films Before and After Nomination by Actor Gender</h4>

| Actor Gender | Average Films Before Nomination | Average Films After Nomination |
|--------------|---------------------------------|--------------------------------|
| F            | 9.47                            | 12.96                          |
| M            | 12.38                           | 21.09                          |


<div style="text-align: justify; margin-top: 10px;">Based on the averages, it is seen that male actors have higher average of apperances with 12.38 films whereas the female actors have the apparence in 9.47 film on average before their first Oscar nomination or win. After the award nomination or win, it is observed that the average gap of appearances between actors and actresses has increased, since the male actors significantly increase their average film count to 21.09 films.</div>

<h4>Hypothesis Testing</h4>
<div>In this part, we have applied several hypothesis testing for the following cases:
    <ul>
        <li>The effect of receiving Oscar nominee/win on the career paths based on appearances</li>
        <li>Genre Preference</li>
        <li> Age at First Nomination/Win</li>
    </ul>
</div>
<h5>The effect of receiving Oscar nominee/win on the career paths based on appearances</h5>
1\) Before Nomination/Win
Null Hypothesis (H0): There is no difference in the number of films acted in by male and female actors before receiving an Oscar nomination or win.<br>
Alternative Hypothesis (H1): There is a difference in the number of films acted in by male and female actors before receiving an Oscar nomination or win.
<div style="text-align: center;">

| Statistic       | Value   |
|-----------------|---------|
| T-statistic     | -1.153  |
| P-value         | 0.251   |
</div>

<div style="text-align: justify; margin-top: 10px;"> The p value shows that there is no statistically significant difference in the number of films acted in by male and female actors before Oscar nomination/win. In other words, we do not have enough evidence to say that the gender has an influence over the career paths on the film appearances before Oscar recognition in the dataset. The negative and low t value shows that male average is higher than female and this difference is not large enough.</div>

2) After Nomination/Win

Null Hypothesis (H0): There is no difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.<br>
Alternative Hypothesis (H1): There is a difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.

<div style="text-align: center;">

| Statistic   | Value  |
|-------------|--------|
| T-statistic | -2.976 |
| P-value     | 0.00351|

</div>


<div style="text-align: justify">Based on the result, we have a statistical evidence to reject the null hypothesis. As a result, the p value was found to be 0.003, which is less than 0.05, which shows that there is a statistically significant difference in the number of films released by male and female actors. Female actors tend to act in fewer films than male actors after receiving their Oscar nomination/win on average. <br>
This conclusion points out that Oscar nomination/win can have a significant impact on the career paths of male and female actors. Female actors potentially have fewer film opportunities following the nomination/win.
</div>

<h5>Genre Preference</h5>
<div style="text-align: justify">
In this section, we will evaluate the existence of a specific genre that specifically provides nominations to men and women when receiving nominations.
<br>
Null Hypothesis (H0): There is no significant difference in the genre preferences of male and female actors in the movies that they obtained nominees/wins.
Alternative Hypothesis (H1): There is a difference in the genre preferences of male and female actors in the movies that they obtained nominees/wins.
</div>

<div style="text-align: center;">

| Statistic       | Value    |
|-----------------|----------|
| Chi-squared     | 161.49   |
| P-value         | 0.0058   |

</div>
<div style="text-align: justify"> The larger the Chi-square value, the greater the probability that there really is a significant difference. In this case, it is found as 161.49. The p value is found as 0.0058 which is less than 0.05, which shows that we reject the null hypothesis. It means that there is a statistically significant difference which suggest that the distribution of film genres is not independent from the actors gender.
<br>
Given that the p-value (0.0058) is less than the conventional alpha level of 0.05, we reject the null hypothesis. This means there is statistically significant evidence to suggest that the distribution of film genres is not independent of the actor's gender. So, the fact that male and female actors who receive Oscar nominations tend to star in different genres of films indicates a potential gender-based genre preference or bias.</div>

Analysis of Top 10 Genres that brings nomination specifically based on genders

<div class="img-container">
    <img id="zoom-img" src="{{'assets/img/gephi.jpg' | relative_url }}" alt="Gephi Trial lets goooo changed">
</div>

