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

<div style="text-align: justify;" >
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

| Statistic       | Value   |
|-----------------|---------|
| T-statistic     | -1.153  |
| P-value         | 0.251   |

<div style="text-align: justify; margin-top: 10px;"> The p value shows that there is no statistically significant difference in the number of films acted in by male and female actors before Oscar nomination/win. In other words, we do not have enough evidence to say that the gender has an influence over the career paths on the film appearances before Oscar recognition in the dataset. The negative and low t value shows that male average is higher than female and this difference is not large enough.</div>

2) After Nomination/Win

Null Hypothesis (H0): There is no difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.<br>
Alternative Hypothesis (H1): There is a difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.

| Statistic   | Value  |
|-------------|--------|
| T-statistic | -2.976 |
| P-value     | 0.00351|

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

| Statistic       | Value    |
|-----------------|----------|
| Chi-squared     | 161.49   |
| P-value         | 0.0058   |


<div style="text-align: justify"> The larger the Chi-square value, the greater the probability that there really is a significant difference. In this case, it is found as 161.49. The p value is found as 0.0058 which is less than 0.05, which shows that we reject the null hypothesis. It means that there is a statistically significant difference which suggest that the distribution of film genres is not independent from the actors gender.
<br>
Given that the p-value (0.0058) is less than the conventional alpha level of 0.05, we reject the null hypothesis. This means there is statistically significant evidence to suggest that the distribution of film genres is not independent of the actor's gender. So, the fact that male and female actors who receive Oscar nominations tend to star in different genres of films indicates a potential gender-based genre preference or bias.</div>

<h5>Analysis of Top 10 Genres that brings nomination specifically based on genders</h5>
{% include top_genres_by_gender_nomination.html %}

<div style="text-align: justify">Based on top 10 genres that the actors got nomination from, it is seen that there are some overlaps in genre choices between female and male actors, however, there are some specific distinctions like romantic drama for females and war film for males.</div>


<h5> Age at First Nomination/Win</h5>
<div style="text-align: justify">
Null Hypothesis (H0): There is no significant difference in the average age at first nomination/win between male and female actors.
Alternative Hypothesis (H1): There is a significant difference in the average age at first nomination/win between male and female actors.</div>

| Statistic   | Value   |
|-------------|---------|
| T-statistic | 4.902   |
| P-value     | 2.95e-06|

<div style="text-align: justify">The p value less than 0.05 shows that we reject the null hypothesis. The positive t-value shows that male actors tend to be older than female actors at the time of their first Oscar nomination or win.
However, we should know that although the test indicates a significant difference, it does not explain the reasons/ causality behind this difference.
<br>
When we calculated the average age of the nomination for female and male actors, it is observed that while female actors get the nomination approximately at 31, males get the nomination on average approximately at 36. Surprisingly, female actors tend to receive their first Oscar nominations at a younger age than their male counterparts. This finding may reveal potential underlying trends or biases in the industry.
</div>

<h3>Actors and Collaborations Network</h3>
<div style="text-align: justify">In order to come up with insights on the gender difference between the actors collaborations, an analysis based on network properties is conducted through the character metadata. Networks that are created is weighted and undirected where each node is representing actor and each edge showing the cooapearance in the same movies between these actors. Additionally, weights are given according to the number of times actors have collaborated. During the analysis, we delve deep into gender attribute of the nodes and create network by filtering the actors according to their popularity for the sake of better understanding.</div>
{% include gender_distribution_chart.html %}
<div style="text-align: justify">The pie chart above visualizes the gender difference among the top 1000 most popular actors.</div>
{% include top_actors_by_popularity.html %}
<div style="text-align: justify">When we looked at to the top 10 female and male actors in terms of appaerances, there is a high difference between the occurances of top 10 female and male actors where the women is significantly underrepresented.</div>

<h4>Top 100 Actors' Network</h4>
<div class="img-container">
    <img id="zoom-img" src="{{'assets/img/resclaed.png' | relative_url }}" alt="Top 100 actors network">
</div>
<div style="text-align: justify">Here's the extracted Gephi visualization of top 100 actors filtered based on edge weights of 10 for the purpose of clear visualization. Pink nodes represents female actors while the blue ones represent male actors. Pink edges indicate female to female collaboration while blue edges indicate male to male collaborations. Also, nodes with higher degrees are represented bigger than other nodes whereas edges with higher weights are represented with thicker edges.
<br>
To zoom in the details based on gender, lets look at the top 30 edges with the highest weights which means that mostly collaborated ones and see the tendency of collaboration between genders.
</div>
{% include gender_distribution_connections.html %}

<div style="text-align: justify">Looking into the top 30 edges with the highest weights in the network, it is observed that there are no female to female collaborations within while only 5 edges represent male to female connections, the higher portion of these edges represents male to male connections. The pie chart above is also represents the overall distribution of these connections and reveals the underrepresentation of the females within popular actors. The maximum number of connections are found as 96.</div>


<div style="text-align: justify">Assortativity Coefficient for 'gender': 0.008071260038849271 <br>
The positive value of assortativity coefficient shows that the actors are more likely to collaborate on the actors with the same gender. However,we should be careful that the value is very small, meaning that there is no strong preference for same-sex cooperation.
</div>

<div class="img-container">
    <img id="zoom-img" src="{{'assets/img/gephi.jpg' | relative_url }}" alt="Gephi Trial lets goooo changed">
</div>

## Analysis about the Impact of Gender Composition in Cast and Crew on IMDb Ratings

<div style="text-align: justify">Before diving into the details of this analysis, let's perform an overarching review of the data. <br>
Firstly, lets look at the average cast and crew gender distributions. It should be noted that there is non-binary gender in the dataset, for the cases we dont know the gender or it is not wanted to be expressed. As it can be seen from the chart, male dominance shows itself in both crew and cast distributions. 
</div>
{% include average_gender_distribution_cast_crew.html %}

<div style="text-align: justify">Then, Let's examine the number of movies for each dominant gender from our main character dataset. As it is observed, while a very small portion contains more female characters or an equal number of females and males, it has been observed that the number of males is higher in a very large portion of films .
</div>
{% include films_gender_character_distribution.html %}

<h4>Correlation Analysis based on gender distribution in Cast & Crew and IMDB ratings</h4>
<div style="text-align: justify">Key Findings:
    <ul>
        <li>Male Cast Percentage: 0.001782</li>
        <li>Female Cast Percentage: -0.008818</li>
        <li>Nonbinary Cast Percentage: -0.003767</li>
        <li>Male Crew Percentage: 0.013692</li>
        <li>Female Crew Percentage: 0.028989</li>
        <li>Nonbinary Crew Percentage: -0.020391</li>
    </ul>
So, there is no strong correlation between the cast-crew gender distributions over the imdb ratings.
</div>
<h4>Group Comparisons</h4>
<div style="text-align: justify">To get more interpretable insights based on gender representation, we prefer to analyze the groups as male-dominated, female-dominated, balanced movies and compare their average ratings.<br>
Conducting the ANOVA test:</div>

| Statistic   | Value   |
|-------------|---------|
| T-statistic | 5.913   |
| P-value     | 0.00270 |


<div style="text-align: justify">High F-statistics shows that there is a difference in variances between the groups. When we examined p value in this case, it suggests that the IMDb ratings are significantly different among films based on the cast gender distribution. It can be considered as an indicator that shows the gender composition of the cast might have an influence over the ratings. However, this is most probably due to the unequal distribution of classes in the original dataset that we are using. In order to get more convinced by the result, we will look at the statistics of Male-Dominant and Female-Dominant films.</div>

| Metric                  | Male-Dominant Films           | Female-Dominant Films         |
|-------------------------|-------------------------------|-------------------------------|
| Mean IMDb Rating        | 6.271                         | 6.318                         |
| Standard Deviation      | 1.029                         | 1.142                         |
| Interquartile Range (IQR)| 1.200                         | 1.700                         |
| Minimum IMDb Rating     | 1.3                           | 1.1                           |
| Maximum IMDb Rating     | 10.0                          | 9.6                           |

<div style="text-align: justify">Between the mean IMDB ratings the difference is quite small and both groups have similar standard deviation. However, the interquartile range shows that there is more variability in rating ranges within the category for female dominant films. Altough there is a statistically significant difference, this stats might suggest that there are other factors in the determination of film ratings beside gender distributions. <br> 
Then, After an ANOVA test has found a significant difference, we used Tukey's HSD test to find out which specific groups' means (comparisons between pairs of groups) are different The results:
<ul>
    <li>There is a significant difference between the balanced and female-dominated groups, the female-dominated group has a higher mean in both comparisons.</li>
    <li>There is no significant difference between the balanced and male-dominated groups.</li>
</ul>
</div>

<div style="text-align: justify">When we performed the same analysis for crew gender distribution along with the imdb ratings, however, the unequal distribution of genders was also the case in here likewise cast gender distribuitons. The p value is found as 2.903e-48, although the result of p value shows that there is a significant difference it might be the result of this unequalness.</div>

<h4>Changes in time based on cast and crew distributions</h4>

{% include temporal_trends_female_representation.html %}
{% include temporal_trends_male_representation.html %}

<div style="text-align: justify">Both graphs point to gender inequality in the film industry; It seems that there are more men than women in both the cast and the crew. The data shows that there have been some efforts towards gender balance over time, but there is a notable gap between the representation of men and women.
</div>

## Movie Genre Evaluation based on Genders

<div style="text-align: justify">In this section, we will look at the genders based on genres such as the existence of specific movie genres that demonstrate a minimal or no gender gap in terms of character representation. In this scope, we will firstly look at the top 20 since there are a variety of genres. </div>
{% include top_genre_gender_distribution.html %}
<div style="text-align: justify">It is obvious that for the top 20 genres, the amount of the male characters exceeeds the female characters. But this fact causes us to think whether we really have some genres that the number of females are equal or more than the male characters or not. Let's search for it.</div>
{% include equal_or_more_female_genres.html %}

<div style="text-align: justify">As it can be seen from the plot, there are only 12 films which includes more number of females. When we analyzed the specifc genres,many of these genres—including "feminist film," "gender issues," and "women in prison films"—have topics that are exclusive to women. This pattern points to a concentrated portrayal of female characters in genres that are probably going to examine topics and storylines centered around women. <br>
When we look at the genres that has minimal difference for genders, genres like 'Gender Issues,' 'Point of View Shot,' 'Kitchen Sink Realism,' 'Singing Cowboy,' 'Clay Animation,' 'Tokusatsu,' and 'Animals' show a perfect balance with absolute zero difference in male and female character counts.</div>