---
layout: post
title: Pandas-applymap
---


## <span style="color:Orange; ">Using Pandas applymap()</span>

### Create an example dataframe


    import pandas as pd
    df = pd.DataFrame({"Reviews":["Is this a movie?","An excellent film","Terrible!!!!!"]})
    print df

                 Reviews
    0   Is this a movie?
    1  An excellent film
    2      Terrible!!!!!


### We would like to apply the function clean_data on every movie review, this kind of analysis is mostly done in Sentiment Analysis


    ###Define a function to clean the data
    def clean_data(review):
        import re
        alpha_review = re.sub("[^a-zA-Z]"," ", review)
        lower_split = alpha_review.lower().split()
        cleaned_data = " ".join(lower_split)
        return cleaned_data

Pandas applymap() does this for you in one line, similar to R


    df["Clean Reviews"] = df.applymap(clean_data)
    print df

                 Reviews      Clean Reviews
    0   Is this a movie?    is this a movie
    1  An excellent film  an excellent film
    2      Terrible!!!!!           terrible

