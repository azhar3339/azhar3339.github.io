
---
layout: post
title: Looping through multiple lists
---


## <span style="color:Orange; ">Python itertools</span>

### Create some lists to loop through


    algorithms = ["SVM", "Decision Trees", "Random Forests", "Linear Regression"]
    accuracy = [87.8, 80, 90, 83]
    true_pos = [20,15,21,16]
    true_neg = [30,20,34,24]

###Naive way to loop through all the lists in one go


    for i in range(len(algorithms)):
        print algorithms[i], accuracy[i], true_pos[i], true_neg[i]

    SVM 87.8 20 30
    Decision Trees 80 15 20
    Random Forests 90 21 34
    Linear Regression 83 16 24


###Nicer way


    import itertools
    for alg,acc,pos,neg in itertools.izip(algorithms, accuracy, true_pos, true_neg):
        print alg, acc, pos, neg

    SVM 87.8 20 30
    Decision Trees 80 15 20
    Random Forests 90 21 34
    Linear Regression 83 16 24

