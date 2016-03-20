---
layout: post
title: Python Dictionaries
---


## <span style="color:Orange; ">Creating a dictionary in Python</span>


    antonym = {} ##Empty Dictionary
    print "Empty Dictionary:",antonym
    antonym["bravery"] = "cowardice" ##Adding elements to a dictionary
    antonym["voluntary"] = "compulsory"
    print "After adding an elements:",antonym

    Empty Dictionary: {}
    After adding an elements: {'voluntary': 'compulsory', 'bravery': 'cowardice'}



## <span style="color:Orange; ">2. Accessing elements in a Dictionary</span>



    print "antonym of bravery:",antonym["bravery"] ##By key
    print "antonym of voluntary:",antonym["voluntary"] ##

    antonym of bravery: cowardice
    antonym of voluntary: compulsory


## <span style="color:Orange; ">3.Checking if an element is present in a dictionary</span>


    key = "bravery"
    if key in antonym:
        print "Antonym of ",key,":",antonym[key]

     Antonym of  bravery : cowardice


## <span style="color:Orange; ">4.Looping through elements in the dictionary</span>

### Using keys


    for key in antonym:
        print key, antonym[key]

    voluntary compulsory
    bravery cowardice


### Using iteritems


    for key, value in antonym.iteritems():
        print key, value
        

    voluntary compulsory
    bravery cowardice

