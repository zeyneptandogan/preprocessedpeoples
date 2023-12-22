---
layout: page
title: CinemaScope
subtitle: Lens on Gender Bias
cover-img: /assets/img/header.png
thumbnail-img: /assets/img/header.png
share-img: /assets/img/header.png
---
<div style="text-align: justify">
    Movies have long held a mirror to society and offered viewers the opportunity to share different experiences and
    emotions. While giving us a roller-coaster of emotions and a great way to bond and connect with different people and cultures universally, they are presenting a reflection to the modern societies that we are living in which has historically been known as gender biased.
    <br><br>
    Grab your popcorn and join us this time while we embark on a journey to unreveal this gender bias in the film industry which has been so deeply rooted and implicit that most of us have been missing it all along. 
    Get ready to discover how your beloved actors' career paths and collaborations have been influenced by their gender. Action! 🍿🎬
</div>
<div class="img-container">
    <img id="zoom-img" src="{{ 'assets/img/WhatsApp Image 2023-12-22 at 01.14.45.jpeg' | relative_url }}" alt="Popcorn">
</div>
## About the Dataset 
<div style="text-align: justify">
<strong>Main Dataset:</strong>  CMU Movie Summary Corpus, collected by the Machine Learning Department of Carnegie Mellon University includes Movie metadata consisting of release date, runtime, movie language, box office revenue, countries. Character metadata included is consisting of character names, actors, gender and age at the time of the movie release. Additionally, plot summaries and Stanford CoreNLP-processed summaries are also provided by them. 
</div>

<div style="text-align: justify">
    <p><strong>Additional Datasets:</strong> To perform a detailed analysis, we used 5 additional datasets such as follows:</p>
    <span>1) Cast and crew data is collected by us following the steps below:</span><br>
    <ul>
        <li>Dataset creation using Freebase IDs and Wikidata API to extract IMDb IDs.</li>
        <li>Usage of the TMDB API for acquiring gender information of cast and crew members.</li>
        <li>Storage of the results in movie_with_gender_info.csv file, that can be found in the repository.</li>
    </ul>
    <span>2) Oscar Awards Dataset from Kaggle: </span><br>
    <span> The dataset contains a scrape of The Academy Awards Database, recorded of past Academy Award winners and nominees between 1927 and 2023. It is used to reveal gender differences and can be found here <a href="https://www.kaggle.com/datasets/unanimad/the-oscar-award/data?select=the_oscar_award.csv">Oscar Award Dataset</a></span><br><br>
    <span>3) IMDB Rating Dataset:</span><br>
    <span>As a success measure, ratings taken from IMDB Non-commercial datasets are considered. Only the files titled 'title.ratings.tsv.gz' and 'title.basics.tsv.gz' are used for this analysis. The datasets can be found in <a href="https://developer.imdb.com/non-commercial-datasets/">IMDB Ratings Datasets</a></span><br>
    <span>4) Character types descriptions dataset:</span><br>
        <span>Created manually by extracting descriptions from tvtropes.org. </span><br>
</div>

## Research Questions
<div style="text-align: justify">
    In the scope of our analysis, we will try to answer the following research questions:<br>
    <span>1) How does gender impact actors' career opportunities, collaborations and success, particularly in terms of the types of role and reward opportunities offered?</span><br>
    <span>2) Do plot summaries contain any gender stereotypes, and if so, how?</span><br>
    <span>3) Does semantic analysis of character types reveal any distinct differences in the assignment of roles based on gender?</span><br>
    <span>4) Does the gender composition of cast and crew influence the critical success of films, evaluated by IMDb ratings?</span><br>
    <span>5) Are there specific movie genres that demonstrate a minimal or no gender gap in terms of character representation?</span><br>
    
We now have the datasets and our research questions ready to unveil the gender bias.  
So brace yourselves for the analysis🚀
</div>
## Temporal Analysis 🎞️

<h3>How does the number of movies released changes over time?</h3>
{% include interactive_chart.html %}

<div style="text-align: justify"> Before we start, we observed that there are movies between 1900 to 2016 in our dataset. However, between 2010 and 2015 there is less value in contrast to the increasing trend in time. Thus, we decided to use the data which we have found more reliable i.e. from 1900 to 2010.</div>

<h3>How does the Number of Female and Male Characters change over time?</h3>
<div style="text-align: justify"> We did the same temporal analysis based on the gender. The below graph shows the number of female and male characters in the movies for specific time intervals. It is observed that for all times the number of male characters are higher then the number of female characters as expected considering the historical male dominancy in the film industry. </div>

{% include gender_time.html %}

## Gender Impact on Actors' Career Opportunities, Collaborations and Success

<h3>Oscar's Magic Touch🏆✨, does it exist equally for all genders?</h3>

<div style="text-align: justify;" >
Did you ever find yourselves watching an Oscar Reward ceremony and wondering how the life of the actors winning the award would change afterwards? Did it ever occured to you that even this effect may differ based on their gender? Surprised? Well, continue reading.. <br>
Apparently, actors don't just strut down the red carpet differently; they actually end up with a different count in their movie appearances afterwards. Let us examine how genders affect these rise up on their movie counts and success.
In this analysis, we used the Oscar Rewards dataset merged with the CMU Movie Corpus dataset. 
</div>

| Gender      | Not Nominated | Nominated | Won |
|-------------|---------------|-----------|-----|
| **Females** | 48,374        | 124       | 38  |
| **Males**   | 84,692        | 118       | 33  |

<div style="text-align: justify; margin-top: 10px;"> Let's dump some facts we found. The number of actors that nominated/won Oscars at least once is 151. There are also actors that have been nominated multiple times cheers to Meryl Streep who got nominated 21 times. After this, we got each actors' first nomination year and calculated the number of movies they appeared before and after their first nomination based on gender to illustrate the effect of Oscar's Magic Touch.</div>
<h4>Average Number of Films Before and After Nomination by Actor Gender</h4>

| Actor Gender | Average Films Before Nomination | Average Films After Nomination |
|--------------|---------------------------------|--------------------------------|
| F            | 9.47                            | 12.96                          |
| M            | 12.38                           | 21.09                          |

<div style="text-align: justify; margin-top: 10px;"> In the first glimspe, it can be seen that male actors have higher average of apperances with 12.38 films whereas the female actors have the apparence in 9.47 film on average before their first Oscar nomination or win. After the award nomination or win, it is observed that the average gap of appearances between actors and actresses has increased, since the male actors significantly increased their average film count to 21.09 films.</div>

<h4>Hypothesis Testing</h4>
<div>Hold on, we have also applied several hypothesis testing for the following cases:
    <ul>
        <li>The effect of receiving Oscar nominee/win on the career paths based on appearances</li>
        <li>Genre Preference</li>
        <li> Age at First Nomination/Win</li>
    </ul>
</div>
<h5>The effect of receiving Oscar nominee/win on the career paths based on appearances</h5>
1\) Before Nomination/Win
<br>
Null Hypothesis (H0): There is no difference in the number of films acted in by male and female actors before receiving an Oscar nomination or win.<br>
Alternative Hypothesis (H1): There is a difference in the number of films acted in by male and female actors before receiving an Oscar nomination or win.

| Statistic       | Value   |
|-----------------|---------|
| T-statistic     | -1.153  |
| P-value         | 0.251   |

<div style="text-align: justify; margin-top: 10px;"> Well, gender bias is not always the case since the p value shows us that there is no statistically significant difference in the number of films acted in by male and female actors before Oscar nomination/win. In other words, we do not have enough evidence to say that the gender has an influence over the career paths on the film appearances before Oscar recognition in the dataset. The negative and low t value shows that male average is higher than female however this difference is not large enough.</div>

2) After Nomination/Win

Null Hypothesis (H0): There is no difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.<br>
Alternative Hypothesis (H1): There is a difference in the number of films acted in by male and female actors after receiving an Oscar nomination or win.

| Statistic   | Value  |
|-------------|--------|
| T-statistic | -2.976 |
| P-value     | 0.00351|

<div style="text-align: justify"> Based on the result, we have a statistical evidence to reject the null hypothesis. As a result, the p value was found to be 0.003, which is less than 0.05, indicating that there is a statistically significant difference in the number of films released by male and female actors. Female actors tend to act in fewer films than male actors after receiving their Oscar nomination/win on average.<br>
In conclusion, Oscar nomination/win can have a significant impact on the career paths of male and female actors. Female actors 👩‍🦰 potentially have fewer film opportunities in contrast to their male counterparts 👨 after the Oscar's Magic Touch.
Apparently this touch is more magical for men 🤴.
</div>

<h5>Genre Preference</h5>
<div style="text-align: justify">
Now, let's evaluate the existence of a specific genre that specifically provides nominations to men and women when receiving nominations.
<br>
Null Hypothesis (H0): There is no significant difference in the genre preferences of male and female actors in the movies that they obtained nominees/wins.
Alternative Hypothesis (H1): There is a difference in the genre preferences of male and female actors in the movies that they obtained nominees/wins.
</div>

| Statistic       | Value    |
|-----------------|----------|
| Chi-squared     | 161.49   |
| P-value         | 0.0058   |


<div style="text-align: justify"> The larger the Chi-square value, the greater the probability that there really is a significant difference. We have found Chi-square value as 161.49 and p-value as 0.0058 which is less than 0.05, showing that we should reject the null hypothesis. Hence, there is a statistically significant difference highlighting that distribution of film genres is not independent from the actors gender.
<br>
So, the fact that male and female actors who receive Oscar nominations tend to star in different genres of films indicates a potential gender-based movie genre preference or bias.</div>

<h5>Analysis of the Genres: A Breakdown of the Top 10 Film Genres Tailored to Gender-specific Nomination</h5>
{% include top_genres_by_gender_nomination.html %}

<div style="text-align: justify">Based on top 10 genres that the actors got nomination from, it can be seen that there are some overlaps in genre choices between female and male actors. However, there are some specific distinctions like romantic drama 💑 for females and war film 🚁 for males.</div>


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
When we calculated the average age of the nomination for female and male actors, it is observed that while female actors get the nomination approximately at 31, males get the nomination on average approximately at 36. Surprisingly, female actors tend to receive their first Oscar nominations at a younger age than their male counterparts. Our leading ladies snatching those Oscar nominations and winnings, while breaking into the Academy Awards game earlier than the guys! 🎬💃
</div>

<h3>The Ultimate Actors Connection Network 🌟</h3>
<div style="text-align: justify">Lights, camera, collaboration!✨ In order to come up with insights on the gender difference between the actors collaborations on movies, an analysis based on network properties is conducted through the character metadata. Networks that are created is weighted and undirected where each node is representing actor and each edge showing the cooapearance in the same movies. Additionally, weights are given according to the number of times actors have collaborated. Let's shine a spotlight on gender attributes and their popularity. Let's roll!🎥

For a sneak peek into the glamorous popularity-gender landscape, check out the pie chart belove which visualizes the gender difference among the top 1000 most popular actors.</div>
{% include gender_distribution_chart.html %}
<div style="text-align: justify">When we zoom into the top 10 female and male actors below in terms of appaerances, there is a high difference between the occurances of top 10 female and male actors where the women is significantly underrepresented. The gender spotlight reveals a stark contrast between the stars 💫 </div>
{% include top_actors_by_popularity.html %}


<h4>Top 100 Actors' Network</h4>
<div class="img-container">
    <img id="zoom-img" src="{{'assets/img/resclaed.png' | relative_url }}" alt="Top 100 actors network">
</div>
<div style="text-align: justify">Here's the extracted Gephi visualization of top 100 actors filtered based on edge weights of 10 for the purpose of clear visualization. Pink nodes represents female actors while the blue ones represent male actors. Pink edges indicate female to female collaboration while blue edges indicate male to male collaborations. Also, nodes with higher degrees are represented bigger than other nodes whereas edges with higher weights are represented with thicker edges.
<br>
To zoom in the details based on gender, lets look at the top 30 edges with the highest weights 🕵️‍♀️, the crème de la crème of collaborations, and see the tendency of connection between genders.
</div>
{% include gender_distribution_connections.html %}

<div style="text-align: justify">Looking into the top 30 edges with the highest weights in the network💎, it is observed that there are no female to female collaborations while only 5 edges represent male to female connections.  Well, it's a male-to-male extravaganza since the higher portion of these edges represents male to male connections. The pie chart above also represents the overall distribution of these connections and reveals the underrepresentation of the females within popular actors. The maximum number of connections are found as 96. 📊 </div>


<div style="text-align: justify">Assortativity Coefficient for 'gender': -0.019<br>
"No gender cliques, please!" 🚫👬👭 Negative assortivity coefficient here indicates a disassortative mixing, suggesting  that nodes with different attributes ( male and female actors) are more prone to be connected. Thus there are no gender homophily (i. e. the tendency for actors of the same gender to form social connections or relationships more frequently than would be expected by chance), but rather male and female connections are more likely to occur just as expected and higlights collaboration across gender boundaries.
</div>

<div class="img-container">
    <img id="zoom-img" src="{{ 'assets/img/malenet.png' | relative_url }}" alt="Male Net">
</div>

<div style="text-align: justify">Here's the extracted Gephi visualization of top 100 male actors filtered based on edge weights of 10 for the purpose of clear visualization where nodes with higher degrees are represented bigger than other nodes whereas edges with higher weights are represented with thicker edges. Before getting lost in the dazzling details, don't forget to click on the network image for zooming in.🔍 Happy exploring!</div>

<div class="img-container">
    <img id="zoom-img" src="{{ 'assets/img/femalenet.png' | relative_url }}" alt="Female Net">
</div>
<div style="text-align: justify">Here's the extracted Gephi visualization of top 100 female actors with unfiltered edge weights where nodes with higher degrees are represented bigger than other nodes whereas edges with higher weights are represented with thicker edges.<br> The difference in the average degrees in these two subgraphs representing male and female actors indicates that that male actors tend to engage in more collaborations within the film and television industry since males have a higher average degree. One explanation can be that male actors are involved in a greater number of partnerships and projects, reflecting a more extensive network of collaborations. <br>
Transitivity measures the likelihood that if actors A and B collaborate with actor C, then actors A and B might also collaborate directly. A higher transitivity would indicate a more interconnected and cooperative network.
Hence, the difference in this measure with respect to genders indicate a stability in male actors' collaborations compared to female actors' collaborations, highlighting the fact that male actors network is more interconnected with more frequent collaborations between each other. One interpretation may be that fewer female actors are available in the movie industry, hence there would be a limited pool of potential female candidates for collaboration and rather they are being connected to male actors.<br>
In a nutshell, a higher transitivity in the male actors' network can indicate that there exist more opportunities for collaborative work and stronger professional bonds for males, whereas there are fewer collaboration opportunities and a less interconnected professional community for their female colleagues. Wow, it really is a man's network right?
</div>

## The Impact of Gender Composition in Cast and Crew on IMDb Ratings
<div style="text-align: justify"> Is there a secret formula to higher IMDb ratings? Does the gender makeup of the cast and crew play a role in the audience's verdict? Does a perfect blend of male and female talents guarantee a banger movie and a stellar IMDb score?👥 Before diving into the details of this analysis, let's take a glance at the data landscape.🌐 <br>
First, we'll look at the average cast and crew gender distributions. It should be noted that there is non-binary gender in the dataset for the cases we dont know the gender or it is not wanted to be expressed. As it can be seen from the chart, male dominance shows itself once again in both crew and cast distributions. 
</div>
{% include average_gender_distribution_cast_crew.html %}

<div style="text-align: justify"> Then, Let's examine the number of movies for each dominant gender from our main character dataset. While a very small portion contains more female characters or an equal number of females and males, it has been observed that the number of males is higher in a very large portion of films .
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
However, there is no strong correlation between the cast-crew gender distributions over the imdb ratings. Let's look further!
</div>
<h4>Group Comparisons</h4>
<div style="text-align: justify">To get more interpretable insights based on gender representation, we will analyze the groups as male-dominated, female-dominated, balanced movies and compare their average ratings.<br>
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

<div style="text-align: justify">When we performed the same analysis for crew gender distribution along with the imdb ratings, however, the unequal distribution of genders was also the case in here likewise cast gender distribuitons. The p value is found as 2.903e-48, although the result of p value shows that there is a significant difference, it might be the result of this unequalness.</div>

<h4>Changes in time based on cast and crew distributions</h4>

{% include temporal_trends_female_representation.html %}
{% include temporal_trends_male_representation.html %}

<div style="text-align: justify">Both graphs point to gender inequality in the film industry; It seems that there are more men than women in both the cast and the crew. The data shows that there have been some efforts towards gender balance over time, but there is still a notable gap between the representation of men and women. Acknowledging the efforts made, the industry has taken steps towards a more balanced portrayal. Still, the long road on ensuring equal representation for all talents in the cinematic world stretches far beyond the horizon. 🌅
</div>

## Movie Genre Evaluation based on Genders

<div style="text-align: justify"> Now, we're putting movie genres under the gender microscope.🧐 We will look at the genders based on genres and try to answer whether there are specific movie genres that demonstrate a minimal or no gender gap in terms of character representation. Any guesses? We actually have but for now, let's keep the genre guessing game alive! In this scope, we will firstly look at the top 20 since there are a variety of genres. </div>
{% include top_genre_gender_distribution.html %}
<div style="text-align: justify">It is obvious that for the top 20 genres, more male characters hogging the spotlight. But, as we know, the best twists come when we least expect them.. Let's keep exploring!</div>
{% include equal_or_more_female_genres.html %}

<div style="text-align: justify">As it can be seen from the plot, there are only 12 films which includes more number of females in the dataset.😯 Unveiling the feminine spotlight, many of these genres—including "feminist film," "gender issues," and "women in prison films"—have topics that are exclusive to women. This pattern points to a concentrated portrayal of female characters in genres that are examining topics and storylines centered around women. <br>
A handful of genres emerge as true champions of gender equality.🏆 'Gender Issues,' 'Point of View Shot,' 'Kitchen Sink Realism,' 'Singing Cowboy,' 'Clay Animation,' 'Tokusatsu,' and 'Animals' show a perfect balance with absolute zero difference in male and female character counts. As we celebrate these genres, it's a recognition of the filmmakers and storytellers who break free from gender stereotypes. 👏 </div>

## Sentiment Analysis of the Character Type Descriptions 

<div style="text-align: justify">In this section, our lens zooms in on the intricate relationship between character types and gender. Which character types are unisex, which are specific to a particular gender, and how they change semantically?</div>

<h4>Character Types Portrayed by Only Women, Only Men and both</h4>

{% include unisex_character_types_gender.html %}

<div style="text-align: justify">According to the plot, the unisex character types (i.e. that are portrayed by both female and male characters) in the CMU dataset are mostly played by male actors with few gender biased streotypical exceptions such as "dumb blonde" and "brainless beauty".<br>
The characters played only by female actors can be seen as types that focus on beauty, appearance and emotional roles, such as 'chantese', 'silly blonde' and 'valley girl' whereas characters played exclusively by male actors include 'tranquil fury', 'playful hacker', and 'byronic hero', clearly leaning towards action-oriented or intellectually complex personalities. Can't a blonde male character be dumb? Well the answer of the directors is apparentlly no. </div>

{% include character_types_gender_distribution.html %}

<h4>Sentiment Analysis over Character Descriptions 🎭 </h4>

<div style="text-align: justify"> Armed with our digital magnifying glass, we performed the sentiment analysis to the character type descriptions by calculating the average polarity and subjectivity of the tokens. There are two points that we looked for: Semantic polarity (Semantic orientation as positive, negative, neutral) and Semantic subjectivity (the degree to which text expresses personal opinions, emotions, or judgments, instead of objective factual information). Overall, the character types are not just ink on a page but rather emotive beings. 🎢🤩 </div>

{% include sentiment_polarity_gender.html %}

<div style="text-align: justify">According to the box plots we can see that median value of sentiment polarity is around the same for both genders. However male characters sentiment polarity distribution shows skewness while female characters polarity is not. Also, characters with more negative sentiment polarity is observed to be more. However, since the wilcoxon test gives the 0.58 p-value, it does not indicate a significance difference we can infer that there are not enough character types to conclude a statistical difference based on gender for sentiment polarity. </div>

{% include sentiment_subjectivity_gender.html %}

<div style="text-align: justify"> These box plots show that sentiment subjectivity for female characters is distributed within a much wider range then males. However, since the wilcoxon test applied below does not indicate a significance difference also for subjectivity we can infer that there are not enough character types to conclude a statistical difference based on gender for sentiment subjectivity as well. We can conclude that a further sentiment analysis can be performed to reveal a possible gender bias based on scripts or plot summaries as well.</div>
