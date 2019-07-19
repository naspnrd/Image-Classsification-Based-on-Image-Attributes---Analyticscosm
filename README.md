# Image Classsification Based on Image Attributes - Analyticscosm
 This competition will require you to collect data from social media and classify images as shareable and non-shareable. Each image comes with a lot of inherent attributes like the color, content, subject, context, message etc. These are subjective qualities and you need to assign meaning to these attributes through your model.  There are plenty of variables you can derive based on above. Your task will be to develop an algorithm that can classify images into shareable and non-shareable based on above tasks. Keep in mind- whether an image is shareable is completely a subjective decision and your model can only be correct, say 90% of the time.
 
 https://naspnrd.github.io/Image-Classsification-Based-on-Image-Attributes---Analyticscosm/
 
```bash
Step by Step Process.....
```
```bash
part one - Shareable or Non-Shareable.. 
```
1. First, challenge was what to collect and how, so to begin with we tried to manually scrape instagram using web scrapping for a single user, for all the posts and their metadata, after failing to collect via web scrapping we looked out for new ways.
2. We came across this tool https://github.com/rarcega/instagram-scraper, and we collected names of instagram users from all fields to make a balanced dataset.
3. Instagram-scrapper, gives almost all the meta-data associated with the media files and using scrapper we collected the data of all instagram users choosen in above step.
4. Scrapper gave information of all the media and meta-data in a single json file per user. 
```#username_csv```

```bash
Link of the github for scrapper tool https://github.com/rarcega/instagram-scraper
```
5. Since scrapper returned individual json files, we converted each json to Comma Separated Values(CSV) by extracting information using json loader, removed unnecessary values that were irrelevant to this context, and saved it into a CSV file.
6. Using a python script(code present in repository) concatenated all the CSV files of individual users to get a single CSV file to work upon.
7. We decide a few a parameters that would have made an image shareable, i.e. if comments were disabled that most probably the image was related to some controversial and second was to use some stop words, we have decided to not share those images that had the any one of the stop words in its hashtags list,be it related marketing, product advertisement, or some previous hashtags that in previous years led to a shadow/permanent ban from instagram.
8. All the images that either had comments disabled or had any tags which was also in stopwords list were not shareable and hence removed, and proceeded with the rest of images.
9.To get list of stopwords we looked and searched for the hashtags which are banned or which can make the image non-shareable on instagram. you can find that in the ``` stopwords.txt ```
10. So far having filtered the original data-set we can now move to second part of the project which was to make predictor for the number of likes.

P.S.: the data collection was not "just these 10 lines" but required an enormous amount of effors, time, patience and persistence. 😊😊 
``` bash
Next Part ie mean no of likes predictor
```
1. Next inline was to collect a list of popular hashtags online to decide a popularity factor associated with the tags of each post, look, search and finally filtered a few popular hashtags online on instagram.
2. Since instagram-scrapper doesn't return number of followers, following or posts, so that had to be manually collected for each of the users online on instagram itself, saved the information to a new CSV file and later on joined the two files for an augmented dataset, and following that we also added values of average number of likes and average number of comments per user in the same CSV file using join operation.  After that we find popular hashtags on the instagram.
``` Popular hashtags.txt  ```
3. We actually tried to do something like that if users put popular tags below the post then it is more likely to be get more likes then not puttting popular tags so we decided to give some extra likes.
4. So we make an attribute in the dataset regarding the counts of the popular hashtags and later use it. ``` dataset.csv ```
5. Now coming to model making we started off by exploring dataset and the features that did not seem to be relevant were removed from dataframe, all this was done after exploring sns heatmaps and scatter plots.
6. Now since dataset was precleaned by us, we went ahead to choose a regression model(since we were predicting number of likes), and choose Logistic Regression model. Predictions from Logistic Regression model were compared to actual number of likes of images using 2 Scikit's model quality evaluation metrics(See code to check the 2 metrics), the results were not as expected. (P.S. : Of all the regressors that we tried RandomForest gave best results in all default parameters regressors and hence we proceeded to tune it.)
7. Moved to Random Forest Regressor, and even the default regressor had outperformed the Logistic Regressor (as quality metrics showed), a change of 2 parameters only increased metric evaluations of random forest.
8. Moved ahead to further hypertuning parameters of our regressor in step 7, used Cross Validation to search over a grid of parameters to select the best parameters for our regressor, and predictions on this fine-tuned regressor gave high ever quality metric so far.
9. The predictions were combined with dafault metadata of the images for future refernce.
10. For media submission metadata along with media can be now easily extracted for further completion of project and only these media files had to uploaded.
```bash
Future Approach
```
```bash
1. Use of Google Vision Api to use extract data from the text images and predict the positive and negativeness of the text and also on the comments of the post
but the api is paid so we can't able to do it i.e sentiment analysis.
If you guys have access to the Google Vision Api then you can also do the sentient analysis of the comments and retrieve text image and to further predictions
That's it from our side..
```
