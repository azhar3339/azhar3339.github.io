---
layout: post
title: Some Pandas usecases 
---


## <span style="color:Orange; ">Pandas: Things I googled</span>

### Remove rows with NA


    import pandas as pd
    df = pd.DataFrame({"Reviews":["Is this a movie?","An excellent film","Terrible!!!!!"]})
    print df
    ###Introduce NAs
    df = df.reindex([4,0,1,2,3])
    print "***********After introducing NAs************"
    print df
    ###Remove rows with NA
    df.dropna()

                 Reviews
    0   Is this a movie?
    1  An excellent film
    2      Terrible!!!!!
    ***********After introducing NAs************
                 Reviews
    4                NaN
    0   Is this a movie?
    1  An excellent film
    2      Terrible!!!!!
    3                NaN





<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Reviews</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Is this a movie?</td>
    </tr>
    <tr>
      <th>1</th>
      <td>An excellent film</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Terrible!!!!!</td>
    </tr>
  </tbody>
</table>
</div>



### Access rows in a dataframe by index


    ##df[1] Key error
    df.ix[1]




    Reviews    An excellent film
    Name: 1, dtype: object



### Remove Duplicates


    df = pd.DataFrame({"Numbers":[1,1,2,2,3,3], "Words":["One","One","Two","Two","Three","Three"]})
    print df
    unique_df = df.drop_duplicates(df)
    print "*************************************************"
    print unique_df

       Numbers  Words
    0        1    One
    1        1    One
    2        2    Two
    3        2    Two
    4        3  Three
    5        3  Three
    *************************************************
       Numbers  Words
    0        1    One
    2        2    Two
    4        3  Three


### Remove Duplicates by column


    df = pd.DataFrame({"Numbers":[1,1,2,2,2,3,3],
                       "Words":["One","One","First Two","Second Two","Third Three","Three","Three"]})
    print df
    unique_df = df.drop_duplicates(subset = 'Numbers', take_last = True)
    print "*************************************************"
    print unique_df
    unique_df = df.drop_duplicates(subset = 'Numbers', take_last = False)
    print "*************************************************"
    print unique_df

       Numbers        Words
    0        1          One
    1        1          One
    2        2    First Two
    3        2   Second Two
    4        2  Third Three
    5        3        Three
    6        3        Three
    *************************************************
       Numbers        Words
    1        1          One
    4        2  Third Three
    6        3        Three
    *************************************************
       Numbers      Words
    0        1        One
    2        2  First Two
    5        3      Three


### Resetting Index


    ### unique_df.ix[1] Will throw a key error as this index was removed see above
    ###Resetting index This will add another column index
    df = unique_df.reset_index()
    print df
    ###Drop that column
    df = unique_df.reset_index(drop=True)
    print df

       index  Numbers      Words
    0      0        1        One
    1      2        2  First Two
    2      5        3      Three
       Numbers      Words
    0        1        One
    1        2  First Two
    2        3      Three


### Subsetting Dataframe based on column values


    df = pd.DataFrame({"Country":["India","Pakistan","France","Italy","Kenya"],
                       "Capital":["Delhi","Islamabad","Paris","Rome","Nairobi"],
                       "Continent": ["Asia","Asia","Europe","Europe","Africa"]})
    print df
    ###Extract the details for continent of Asia
    df_asia = df[df["Continent"] == "Asia"]
    print "*************************************************"
    print df_asia
    ###Asia and Africa
    df_asia_africa = df[df["Continent"].isin(["Asia","Africa"])]
    print "*************************************************"
    print df_asia_africa

         Capital Continent   Country
    0      Delhi      Asia     India
    1  Islamabad      Asia  Pakistan
    2      Paris    Europe    France
    3       Rome    Europe     Italy
    4    Nairobi    Africa     Kenya
    *************************************************
         Capital Continent   Country
    0      Delhi      Asia     India
    1  Islamabad      Asia  Pakistan
    *************************************************
         Capital Continent   Country
    0      Delhi      Asia     India
    1  Islamabad      Asia  Pakistan
    4    Nairobi    Africa     Kenya


### Replacing Values in a dataframe
Let us say we want to replace the continents by some numeric codes.   


Asia =1, Africa = 2, Europe = 3


    df["Continent"] = df["Continent"].replace("Asia", 1)
    df["Continent"] = df["Continent"].replace("Africa", 2)
    df["Continent"] = df["Continent"].replace("Europe", 3)
    print df

         Capital  Continent   Country
    0      Delhi          1     India
    1  Islamabad          1  Pakistan
    2      Paris          3    France
    3       Rome          3     Italy
    4    Nairobi          2     Kenya


### Writing a list of lists to a csv file


    def write_to_csv(list_of_lists,column_names):
        df = pd.DataFrame(list_of_lists, columns=column_names)
        df.to_csv("Filename.csv", index=False)

### Combine data from files in a directory


    def read_data(path_to_dir):
    
        file_names = os.listdir(path_to_dir)
        for i in range(len(file_names)):
            ###First file create dataframe
            if i == 0:
                df = pd.read_csv(path_to_dir + '/' +file_names[i])
                df = df[['Comment','tags']]
            else:
            ###subsequent files, append to dataframe
                df1 = pd.read_csv(path_to_dir + '/' +file_names[i])
                df1 = df1[['Comment','tags']]
                df = df.append(df1, ignore_index=True)
    
        return df
