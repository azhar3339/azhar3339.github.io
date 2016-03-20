---
layout: post
title: Python run a function in parallel with different arguments
---


## <span style="color:Orange; ">Python: Pool from Multiprocess</span>

### Create a slow function which needs to be run in parallel


    import time
    def slow_function(number):
        print "Starting the function with argument:", number
        time.sleep(4) ###Some costly operations
        return number

### Running the slow function sequentially for 4 numbers


    numbers = range(4)
    start = time.time()
    for number in numbers:
        res = slow_function(number)
        print "Output:", res
    end = time.time()
    print "Time taken in seconds:", end - start

    Starting the function with argument: 0
    Output: 0
    Starting the function with argument: 1
    Output: 1
    Starting the function with argument: 2
    Output: 2
    Starting the function with argument: 3
    Output: 3
    Time taken in seconds: 16.017800808


### Now running the four function calls in parallel


    from multiprocessing import Pool
    
    pool = Pool()
    start = time.time()
    results = pool.map(slow_function, numbers)
    end = time.time()
    print "Results from four function calls:", results
    print "New time taken:", end - start


    Results from four function calls: [0, 1, 2, 3]
    New time taken: 4.02795600891
    Starting the function with argument: 2
    Starting the function with argument: 0
    Starting the function with argument: 3
    Starting the function with argument: 1

