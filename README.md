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

    The first workflow below was made by Tom for the whole project. It includes data acquisition and preprocessing, as well as sentiment and spatial analysis. Visit our [story map](https://storymaps.arcgis.com/stories/ffc11d7f630d4eed801a5e8b12742766) to see more operational details. Apart from it, a separated workflow was made to represent my learning process. 
    
    <img width="643" alt="method" src="https://user-images.githubusercontent.com/131768624/236615604-ff423380-2375-4b3b-b09c-c8bdfdeeacce.png">
    
    ![workflow](https://user-images.githubusercontent.com/131768624/236615518-6f129872-a1f4-4a3f-bcab-4450e2541825.png)


    To gain the data from Twitter, we used Twitter API and Twarc2. Twitter’s API is mostly an open API, which means everybody could access to that once users has successfully applied for developer accounts by declaring the purpose of the account. But in this February, Twitter announced that it would no longer provide free access, instead user needs to pay 100$ per month for basic access level. Though the policy was then rolled back to remain free access option, the offer was limited from 2 million to 1.5 thousand for only certain users. Consequently, our applications for developer accounts were all turned down. Fortunately, we still have one account that I had applied last September with 2-million tweet available for retrieving. To pull out tweets, twarc2 was used. Figure below (made by Sam) shows how to make commands to call the harvesting functions.
    
    ![image](https://user-images.githubusercontent.com/131768624/236615337-a6bae067-e0c5-4d77-8164-b73c36e6a5f5.png)
 
    Since twar2 was not configured to filter tweets by location, the choice was made to search tweets in Dutch language. Dutch word ‘ik’ (I) was used as the keyword for searching to maximize the number of tweets. In addition, this word could also give tweets from users that were expressing their sentiments. This process was repeated three times, all roughly a week apart from each other to avoid harvesting duplicate tweets. In total, we harvested around 1.8 million tweets, among which over 10 thousand were geotagged. Meanwhile, some concerns and drawbacks were also raised by the method:
- **privacy**: geo information and personal information of users like name, gender and age are also collected. To deidentify the datasets is necessary for minimizing potential infringement on privacy, thus we decided to remove any personally identifiable data and utilize bounding box to generalize the exact location.
- **consent**: despite having agreed to the terms & conditions of Twitter, users might be not aware of the range of information that can be extracted from their tweets. In addition, they might not know what other people can do with these tweets and are thus unlikely to have explicitly agreed upon providing their data to researchers like us. 
- **bias**: such method has neglected internationals speaking other languages, which is a large group of people living in the country. But it also filtered out most of the tourists that were not included in our research. 
    
3. **Implementation**

    The details of implementation are included in the Jupter notebook which could be found in the repository.

4. **Results**
5. **Conclusions**
## III. Reflection 
1. **Ethics**
2. **Boundary crossing competence** 
