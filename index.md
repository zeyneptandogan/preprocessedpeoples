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
    <p>1) Data collection by us:</p>
    <p>We collected additional data by following the below steps:</p>
    <ul>
        <li>Dataset creation using Freebase IDs and Wikidata API to extract IMDb IDs.</li>
        <li>Utilization of the TMDB API for acquiring gender information of cast and crew members.</li>
    </ul>
    <p>The results are stored in movie_with_gender_info.csv file, that can be found in the repository.</p>
    <p>2) Oscar Awards Dataset from Kaggle: </p>
    <p>Analyzing Oscar awards data by gender, focusing on nominee and winner gender proportions, revealing industry gender biases and progress towards equality in film awards. The dataset can be found in <a href="https://www.kaggle.com/datasets/unanimad/the-oscar-award/data?select=the_oscar_award.csv">Oscar Award Dataset</a></p>
    <p>3) IMDB Rating Dataset:</p>
    <p>As a success measure, IMBD ratings are used in the analysis. The data is taken from IMDB Non-commercial datasets. Only the files titled 'title.ratings.tsv.gz' and 'title.basics.tsv.gz' are utilized for this analysis. The datasets can be found in <a href="https://developer.imdb.com/non-commercial-datasets/">IMDB Ratings Datasets</a></p>
</div>

## Research Questions
<div style="text-align: justify">
    In the scope of this analysis, we will try to answer the following research questions:
    1) How does gender impact actors' career opportunities, collaborations and success, particularly in terms of the types of role and reward opportunities offered? 
    2) Do plot summaries contain any gender stereotypes, and if so, in what manner? 
    3) Does semantic analysis of character types reveal any distinct differences in the assignment of roles based on gender? 
    4) Does the gender composition of cast and crew influence the critical success of films, evaluated by IMDb ratings?
    5) Are there specific movie genres that demonstrate a minimal or no gender gap in terms of character representation?
</div>