# Homework Assignment Due 9/27/2017

#### Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo. Think for a minute about how the data is structured. What do you think each column means? What do you think each row means? Tell me! (If you're unsure, look at more of the file contents.)  

> The Order ID represents the entire order, the item_name is the item as it appears on the menu, and the choice_description details the (free) ingredients added to the burrito/bowl. Each line represents a specific combination of burrito/bowl + additional ingredients being ordered, and the quantity represents the number of items of a specific combination. So if you had three lines with the same Order ID, two lines had a Quantity of 1 and the third line had a Quantity of 2, then the order had a total of 4 items with three different combinations. The item_price represents the cost of the line item; if the Quantity = 2 then the item_price represents the cost of two items.  


1. *How many orders do there appear to be?*  
    Using $ tail chipotle.tsv command, the last order id appears to be 1834.  
    **Note**: using this command assumes the IDs are in order. If they were not in order, I found this code for an answer:  
    $ sort -nrk1,1 chipotle.tsv | head -1 (answer: 1834    1       Chicken Salad Bowl      [Fresh Tomato Salsa, [Fajita Vegetables, Pinto Beans, Lettuce]] $8.75)
     [Link to resource](https://unix.stackexchange.com/questions/170204/find-the-max-value-of-column-1-and-print-respective-record-from-column-2-from-fi)
    
2. *How many lines are in this file?*  
    Using the $ wc -l chipotle.tsv command, there are a total of 4623 lines in this file.

3. *Which burrito is more popular, steak or chicken?*  
    Using the following commands:  
    A. $ grep -i "steak burrito" chipotle.tsv | wc -l   (answer: 368)  
    B. $ grep -i "chicken burrito" chipotle.tsv | wc -l (answer: 553)  
    I found that there are more orders for Chicken Burritos.   
    **NOTE**: I did not take into account order [quantity] column, so the total number of chicken burritos ordered may be fewer than total steak burritos ordered.
  [Link to original solution resource](https://unix.stackexchange.com/questions/291225/count-the-number-of-lines-found-by-grep)
    **NOTE 2**: Per our conversation I tried to sum the [quantity] column to determine popularity by volume. 
    A. $ grep -i "Steak Burrito" chipotle.tsv | awk '{sum+=$2} END {print sum}' (answer = 386)
    B. $ grep -i "Chicken Burrito" chipotle.tsv | awk '{sum+=$2} END {print sum}' (answer = 591)
    I figured out that Chicken Burritos are more popular, where Chicken Burrito = 591 and Steak Burrito = 386.
  
4. *Do chicken burritos more often have black beans or pinto beans?*  
    Using the following commands:  
    A. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "black beans" | wc -l (answer: 282)
    B. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "pinto beans" | wc -l (answer: 105)
    I found that Chicken Burrito orders are more often made with black beans.  
    **NOTE**: Same as above, I did not take [quantity] column into consideration. So I verifed based on orders, not items ordered.
    [Link to original solution resource](http://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/)  
    **NOTE 2**: 
    A. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "black beans" | awk '{sum+=$2} END {print sum}' (answer = 307)
    B. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "pinto beans" | awk '{sum+=$2} END {print sum}' (answer = 108)
    I found that 'Chicken Burrito' + 'pinto beans' = 108, and 'Chicken Burrito' + 'pinto beans' = 307, so black beans are still ordered     more often.

5. *Make a list of all of the CSV or TSV files in the [our class repo] (https://github.com/ga-students/DS-SEA-07). repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.*  
    Using this command: $ find /c/Users/schri/Desktop/DS-SEA-07-master -name <asterisk>.?sv
    (Answer: 
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/airlines.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/Airline_on_time_west_coast.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/bank-additional.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/bikeshare.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/chipotle.tsv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/citibike_feb2014.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/drinks.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/drones.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/hitters.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/icecream.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/imdb_1000.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/mtcars.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/NBA_players_2015.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/ozone.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/pronto_cycle_share/2015_station_data.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/pronto_cycle_share/2015_trip_data.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/pronto_cycle_share/2015_weather_data.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/rossmann.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/rt_critics.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/sms.tsv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/stores.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/syria.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/time_series_train.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/titanic.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/ufo.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/vehicles_test.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/vehicles_train.csv
    + /c/Users/schri/Desktop/DS-SEA-07-master/data/yelp.csv
     )

6. *Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of [our class repo] (https://github.com/ga-students/DS-SEA-7).*  
       I used this command $ find . -iname <asterisk>dictionary<asterisk> but it came back with zero results. I also used the command $ grep -r "directory" . | wc -w (answer: 951)


**Optional**: *Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!*

I used the command $ tail -n+2 chipotle.tsv | cut -f3,3 | sort | uniq -c to get a list of unique item names and the count of orders:
    (answers:
        1 Carnitas Salad
        6 Carnitas Salad Bowl
       40 Carnitas Soft Tacos
      726 Chicken Bowl
      553 Chicken Burrito
       47 Chicken Crispy Tacos
        9 Chicken Salad
      110 Chicken Salad Bowl
      115 Chicken Soft Tacos
      211 Chips
      110 Chips and Fresh Tomato Salsa
      479 Chips and Guacamole
        1 Chips and Mild Fresh Tomato Salsa
       22 Chips and Roasted Chili Corn Salsa
       18 Chips and Roasted Chili-Corn Salsa
       43 Chips and Tomatillo Green Chili Salsa
       48 Chips and Tomatillo Red Chili Salsa
       31 Chips and Tomatillo-Green Chili Salsa
       20 Chips and Tomatillo-Red Chili Salsa
        2 Crispy Tacos
       20 Izze
       27 Nantucket Nectar
        2 Salad
      101 Side of Chips
      211 Steak Bowl
      368 Steak Burrito
       35 Steak Crispy Tacos
        4 Steak Salad
       29 Steak Salad Bowl
       55 Steak Soft Tacos
       85 Veggie Bowl
       95 Veggie Burrito
        1 Veggie Crispy Tacos
        6 Veggie Salad
       18 Veggie Salad Bowl
        7 Veggie Soft Tacos
    )

