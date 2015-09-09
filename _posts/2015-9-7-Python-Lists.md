---
layout: post
title: Python Lists
---


## <span style="color:Orange; ">1. Creating a list in Python</span>


    a = [] ##Empty list
    print "Empty List:",a
    a.append('first element') ##Adding elements to a list
    print "After adding an element:",a
    a = range(0,10) ##List with numbers ranging from 0 to 9
    print a
    a = range(10) ##Same as above
    print a
    a = range(0,10,2) ##Arguments: Start, Stop, Step
    print a
    a = range(0,10,3) ##Step by 3
    print a

    Empty List: []
    After adding an element: ['first element']
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [0, 2, 4, 6, 8]
    [0, 3, 6, 9]



## <span style="color:Orange; ">2. Accessing elements in a list</span>



    a = range(1,101) ###List of first n natural numbers 
    print "First element:",a[0] ## Indexing starts from 0
    print "First 10 elements:",a[:10]
    print "Elements from 11 to 20:",a[10:20]
    print "Last Element:",a[-1]
    print "Exclude last 10 elemnts:",a[:-10]
    print "10th to 20th elements from the end:",a[-20:-10]


    First element: 1
    First 10 elements: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    Elements from 11 to 20: [11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
    Last Element: 100
    Exclude last 10 elemnts: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90]
    10th to 20th elements from the end: [81, 82, 83, 84, 85, 86, 87, 88, 89, 90]


## <span style="color:Orange; ">3.Something fancy: by my standard and if you are reading this then by your standard as well</span>

### 3.1 USD to INR


    USDs = range(1000,10000,1000)
    print "USD:",USDs
    INRs = [66.84 * usd for usd in USDs]
    print "INR:",INRs

    USD: [1000, 2000, 3000, 4000, 5000, 6000, 7000, 8000, 9000]
    INR: [66840.0, 133680.0, 200520.0, 267360.0, 334200.0, 401040.0, 467880.0, 534720.0, 601560.0]


### 3.2 Countries and Capitals


    ######From list to dictionary
    country_capital= ['India:Delhi','Pakistan:Islamabad']
    capital = [{i.split(":")[0] : i.split(":")[1]} for i in country_capital][0]
    print capital['India']

    Delhi
