---
layout: post
title: Python sort lists based on the values in another list
---


## <span style="color:Orange; ">Python: zip and itemgetter</span>

### Create some lists to loop through


    algorithm_codes = ["SVM", "DT", "RF", "LR"]
    algorithms = ["SVM", "Decision Trees", "Random Forests", "Linear Regression"]
    accuracy = [0.8, 0.9, 0.79, 0.95]

###Step One: Zip everything into a single list


    combined_data = zip(algorithm_codes, algorithms, accuracy)

###Step Two: Sort 


    ###Sort based on the third column i.e., index 2 in python
    from operator import itemgetter
    combined_sorted = sorted(combined_data, key=itemgetter(2), reverse= True) ##Descending order

###Look at the result


    for i in combined_sorted:
        print i 

    ('LR', 'Linear Regression', 0.95)
    ('DT', 'Decision Trees', 0.9)
    ('SVM', 'SVM', 0.8)
    ('RF', 'Random Forests', 0.79)

