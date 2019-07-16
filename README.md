# Image Classsification Based on Image Attributes - Analyticscosm
 This competition will require you to collect data from social media and classify images as shareable and non-shareable. Each image comes with a lot of inherent attributes like the color, content, subject, context, message etc. These are subjective qualities and you need to assign meaning to these attributes through your model.  There are plenty of variables you can derive based on above. Your task will be to develop an algorithm that can classify images into shareable and non-shareable based on above tasks. Keep in mind- whether an image is shareable is completely a subjective decision and your model can only be correct, say 90% of the time.
Step by Step Process.....
1. First we started collecting data.
2. We started our search for potential users and we found around 71 users. ``` users.txt```
3. After that, we used the instagram scraper tool to download the json file of the selected users You can find the list of user's json files 
```#username_csv```

```bash
Link of the github for scrapper tool https://github.com/rarcega/instagram-scraper
```
4. 
5. After we have find it hard on what basis we our gonna decide that image is shareable or not, we have thought of on the basis of religious sentiments(like indian flag on slippers make indians crazy,or like someone hurts sentiments of other religion), marketing, product advertisement  
5.After that we started our search for the hashtags which are banned or which can make the image non-shareable on instagram. you can find that in the ``` stopwords.txt ```
6. On the basis of that we have matched the hashtags in the user's post to our stopwords if anything matched then that post becomes non-shareable.
``` bash
Next Part ```
