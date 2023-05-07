# Overview
This repository includes my individual portfolio of project: Sentiment Analysis of Twitter Engagement (Group Social Media1). The project was built upon Data Science of Smart Environment course hold by Wageningen UR. In this portfolio, I will mainly reflect on the work I have done to accomplish my personal learning goals.
## I. Personal Learning Goals
As a future urban designer or environmental issue consultor, I expect myself to know how to appropriately interrupt and interact with the environment in the big data era instead of being blind about the reality per se. Thus, I identified 3 learning goals in the course to approach to my expectation: 
* **Data acquisition and wrangling**: my original learning goal used to be data acquiring solely, which was to learn the complete process of retrieving data from Twitter API, as well as its functionality and limitations. For example, how many tweets are we able to get, in what time-period; are we able to filter the tweets by certain topic or location; Is that possible to identify different category to an interactive communication? However, the task seems to be not so challenging. Questions were naturally answered when me and Sam worked together to successfully get Twitter data. Moreover, to achieve my learning goal of data analyzing, it is necessary to know how the data was preprocessed or to implement some new wrangling methods.
* **Data visualization and analysis**: I cut goals of applying natural language processing and making story map for our project for this part, because these tasks did not require any cooperation. So, people who was more experienced in our group could already handle the tasks efficiently. However, I still want to learn story map making and applying ChatGPT API for NLP after the course. By working on the project, I would like to get familiar with programming in Python (utilize tutorials), coworking in Jupyter notebook or Google Colab (not feasible since Colab cannot work in a normal way when multiple people open the same document), data analyzing in Pandas and data visualization by matplotlib. Afterwards, a clear image of the whole workflow should be formed in my head. 
* **Quality, social and privacy**: reflective thinking of our results is very important, which may come out that source datasets are skewed, ethical issues, and the underlying causes of our results. Especially, I want to learn more about ethical issues on data utilization. I knew the privacy crisis of Facebook and the discussion about cookies of website. But the logic behind it is not so clear for me. When will data processing have social impacts, and what is the legal boundaries of it? My understanding of these questions could be included in our ethical document. Moreover, feedbacks from the teacher suggested me to also reflect on my own actions and activities both within and outside of the project.
## II. Sentiment Analysis of Twitter Engagement
1. **Background**

    Polarization has been a growing topic in the last few years. Social media is a platform for discussion but seen as a driver for polarization. People on social media could often engage in lengthy debate with strongly opposed opinions. Besides being a driver for debate, social media also functions to connect people. A deeper understanding about interaction between people on the social media can be insightful for mitigating polarization. To narrow down, this project will focus on spatial sentiment analysis and answer the following questions:

- Is there a difference in the reaction patterns of users who are geographically close compared to those who are far away from the tweeter?

- Is there a tendency towards positive or negative conversations depending on the closeness of people?

2. **Methodology and Data Source**

    The first workflow below was made by Tom for the whole project. It includes data acquisition and preprocessing, as well as sentiment and spatial analysis. Visit our [story map](https://storymaps.arcgis.com/stories/ffc11d7f630d4eed801a5e8b12742766) to see more operational details. 
    
    <img width="643" alt="method" src="https://user-images.githubusercontent.com/131768624/236615604-ff423380-2375-4b3b-b09c-c8bdfdeeacce.png" align="center" >

    To gain the data from Twitter, we used Twitter API and Twarc2. Twitter’s API is mostly an open API, which means everybody could access to that once users has successfully applied for developer accounts by declaring the purpose of the account. But in this February, Twitter announced that it would no longer provide free access, instead user needs to pay 100$ per month for basic access level. Though the policy was then rolled back to remain free access option, the offer was limited from 2 million to 1.5 thousand for only certain users. Consequently, our applications for developer accounts were all turned down. Fortunately, we still have one account that I had applied last September with 2-million tweet available for retrieving. To pull out tweets, twarc2 was used. Figure below (made by Sam) shows how to make commands to call the harvesting functions.
   
    <img width="643" alt="image" align="center" src="https://user-images.githubusercontent.com/131768624/236615337-a6bae067-e0c5-4d77-8164-b73c36e6a5f5.png">
 
    Since twar2 was not configured to filter tweets by location, the choice was made to search tweets in Dutch language. Dutch word ‘ik’ (I) was used as the keyword for searching to maximize the number of tweets. In addition, this word could also give tweets from users that were expressing their sentiments. This process was repeated three times, all roughly a week apart from each other to avoid harvesting duplicate tweets. In total, we harvested around 1.8 million tweets, among which over 10 thousand were geotagged. Meanwhile, some concerns and drawbacks were also raised by the method:
- **privacy**: geo information and personal information of users like name, gender and age are also collected. To deidentify the datasets is necessary for minimizing potential infringement on privacy, thus we decided to remove any personally identifiable data and utilize bounding box to generalize the exact location.
- **consent**: despite having agreed to the terms & conditions of Twitter, users might be not aware of the range of information that can be extracted from their tweets. In addition, they might not know what other people can do with these tweets and are thus unlikely to have explicitly agreed upon providing their data to researchers like us. 
- **bias**: such method has neglected internationals speaking other languages, which is a large group of people living in the country. On the other hand it also filtered out most of the tourists that were not included in our research. The use of keyword "ik" can lead to a bias towards more or less negativity because some really negative thing happened in the Netherlands in a certain region, or the weather was really bad somewhere, or people tend to be more positive/negative when talking about themselves using the Dutch word ‘ik’. To partly address the issue, we suggest to use more keywords and another data harvesting tool that selects tweets on the basis of geographic location. By these two approaches different strategies could be compared and reliability of results and conclusions could be increased. 

3. **Implementation**

    Apart from the workflow in the previous part, a separated workflow was made to represent my learning process. And details of implementation are included in the Jupter notebook (Data visualiztion.ipynb) which could be found in the repository. 

    ![workflow](https://user-images.githubusercontent.com/131768624/236652700-88efa59c-9bdb-41dc-8f3a-d2dbce7dc672.png)

    Before I start working on my learning goal of data visualization, case study was implemented. Two cases from the US were studied, one was about [spatial analysis of geottaged tweets in the US](https://scholarship.claremont.edu/cgi/viewcontent.cgi?article=3352&context=cmc_theses), another one was more focused on the [operational aspect of visualizing flight routes in the US by python](https://tuangauss.github.io/projects/networkx_basemap/networkx_basemap.html). The Jupyter notebook file contains all the programming work to carry out data preparation and then visualization. Packages like pandas, networkx, matplotlib and baseamap were imported as tools. 

4. **Results**

    Three network maps representing positive, neutral and negative sentiment of interactions were made as outcome of visulization. 

    ![map__po](https://user-images.githubusercontent.com/131768624/236626685-cf69ebd9-e697-47fb-8ffd-217fdf122e02.png)

    ![map__neu](https://user-images.githubusercontent.com/131768624/236626678-e53b0487-57b4-4a8c-8c22-95db1582d297.png)

    ![map__neg](https://user-images.githubusercontent.com/131768624/236626667-3c18ae64-f5e4-4fac-92d1-e22947b96a09.png)
    
    Red points represent users' locations. With lines between the points, users engaged in the same conversations are connected. Green lines means positive interactions, yellow is the color of neutral, and red ones are negative. Thickness of lines represents the communicating frequecy or times of responding between two locations. In general, density of lines in the maps is in the order of neutral, positive and negative. But in general, thicker lines occurs more in positive map and negative map than the neutral one, though there is a communication between the Netherlands and Belgium seems to be very intense. Thick lines of negative interaction are more likely to cross the country in a vertical direction from north to south while positive ones' are relatively gentle. Lastly, lines in three maps all have the patterns to intersect more in the middle of the country. 

6. **Conclusions**

    There is no clear relationship of sentiments of interactions with distance between people. But we could see there were less interactions between people in the northern provinces. Instead, people geotagged in the north tend to reply to tweets from the central part of the Netherlands, or the Randstad area. There could be various reasons for this observation. For example, it could be the population difference. There might be less users in the North as there live less people in that area and probably more users in the Randstad area because there live more people in this region. However, this conclusion could also be false as user interactions that take place within the same bounding box are not visualised.
    
    Also, social media is often believed to be mostly negative (Whatman, 2022), our collected tweets tend to be more positive than negative as the distribution of the tweets is more skewed towards positive than negative sentiment. And we can also conclude that tweets or conversations with sentiment (either positive or negative) have more chance to arose a highly interactive communication.

    From our data analysis done by Tom, it can also be derived that people are more likely to interact with people closer by. This is probably because people mostly interact with people they follow. People tend to follow people they know in real life, and they probably follow people who are in close proximity to them as they have some connection in real life. But the correlation coefficient of 0.01 indicates that sentiment of interaction is not affected by distance at all.
    
    ![image](https://user-images.githubusercontent.com/131768624/236629855-803654e3-b28c-4a55-be5b-a0abdc5f8672.png)

## III. Reflection 
1. **Ethics**

    The main pitfalls of our project were identified in the data collection and sentiment analysis process. The problems and ethical concerns of data retrieving are related to the privacy issue, the amount of data, bounding box and the use of keyword "ik". For the sentiment analysis, it is abuot the 29% inaccuracy of model (Inconclusive evidence) and the black box of machine learning algorithms (Inscrutable evidence). Also, the analysis may not exactly match the definition of polarization for every conversation, which should be how people’s opinions are engaged in strong disagreement with each other. But it may show that people are more likely to discuss positive topics, or behave happier in some places than others.

    We suppose our research outcomes would help governments to get insights about people’s interactive behaviours on social media and policy on potential segregation.  Here are some guidelines are needed to be taken into account when considering to utilize our research outcomes. First of all, it is important to recognize pitfalls associated with the project. Here are a few examples:

- **Bias in the data**: Because Twitter users may not accurately reflect the overall population, it is possible that the data we use to assess social interactions and sentiments in a city as a whole is biassed. Additionally, because some users could be more likely to tweet about particular subjects or in particular ways, Twitter statistics may be biassed due to selection.
- **Privacy issues**: The usage of Twitter data presents serious privacy issues, especially if the data is connected to particular people or places. There may be worries about the data's use for monitoring or the possibility that it will be used to target particular people or groups.
- **Ethical issues**: Utilizing Twitter data for governmental objectives may raise ethical issues. Examples include whether the use of this data is in accordance with fairness and justice principles or whether it justifies current inequities in the city.

    To avoid pitfalls above, it's crucial to create governance frameworks for the usage of sentiment analysis and take accountability, transparency, and fairness into account. Furthermore, the governemnt would get a more holistic view about how interactions on the social media geographically looks like:

- **Understand how social media may lead to segregation**: By analyzing the sentiment of tweets and responses, a local governance may be able to identify patterns of segregation in different areas of the city. The information from our research could be used to inform policy decisions, aimed at promoting greater social cohesion and reducing segregation. This can be done in two main ways: firstly, by identifying areas of the city where social-media interaction is low, and secondly, by identifying areas of the city with high levels of positive or negative social-media interaction.

- **Identify areas of the city where social-media interaction is low**: Our project may be able to identify areas of the city where social-media interaction is low, based on the frequency, tone of tweets and responses. This information could be used to target policies aimed at improving social interaction in these regions. 

- **Identify areas of the city with high levels of positive or negative social-media interaction**: Conversely, the project may be able to identify areas of the city with high levels of positive social-media interaction. This information could be used to identify the factors that contribute to social cohesion and community building. 

    As for further steps to utilize the information, we would encourage policymakers to see the outcome of our research while contemplating the causes of phenomena to better facilitate citizens engaging in positive interactions instead of setting up interceptions on negative conversations. Moreover, the government could choose to implement [regional integration](https://www.worldbank.org/en/topic/regional-integration/overview) or push the collaboration between different regions to enhance their interrelationship. Looking into the potential cause of negative reponse, which might represent the overall mindset or unsatisfaction of one area, would also help to troubleshooting and solve societal problems in advance. The use of big data in the governing process is an [evidence-based approach for policy-making](https://www.mdpi.com/2504-2289/6/4/160), only by following the guidelines can this approach be valid.

2. **Boundary crossing competence (BCC)** 

    From four aspects that I will reflect on my BCC:
    
- **Identification**:Originally we had two topics in mind and our group was evenly divided between them. I was in the Climate perception group, which was finally defeated. But choosing our final topic did not demotivate the supporters of the other topic. This process actually promoted us to really understand both ideas, think about the highlights of one case and drawbacks of the other to convince the group. In the end, I got to realize that the climate change perception topic could be too hard to implement in a short period of time. And societal polarization analysis could be used as the basic of establishment. The research questions are also easier to be intuitively answered by visualization.

- **Coordination**:In the beginning, the roles were a bit unclear and everybody was still a bit hesitant about what to do. This was also due to the problems with the Twitter API and it took quite some time before the data was actually harvested. When the first data was harvested, we had something to work with and quite a natural process of task division emerged. Though we all were aware of each other's learning goals and assigned tasks or formed sub-groups depending on them, some overlap in learning goals was present. In combination with a large difference in scripting skills, some overlapped work is not all used in our final group deliverables but was relevant to our individual learning goals.

- **Reflection**:As the data science group work was like a flow, the task is always based on the previous outcomes. So, I basically could do nothing for the project before the data was preprocessed and did not actively engaged in the communications but focused on the lectures and practice. Later I started to understand how important it is to know what and how did everyone do their jobs. I felt confused at a result sometimes. Sam found my anomaly and kindly asked whether I need help, then it turns out his help of data wrangling had saved me from stucking before I really begin to visualization.

- **Transformation**:Here I could not come up with any personal behaviour change connected to our project. But a evidence-based approach for policy-making may be part of the transformation. 
