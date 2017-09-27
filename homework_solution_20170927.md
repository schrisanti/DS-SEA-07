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

  **NOTE 2**: Per our conversation I tried to sum the [quantity] column to determine popularity by volume. I could not get it to work. I know there's $ awk '{sum+=$2} END {print sum}' chipotle.tsv to sum the [quantity] column (answer = 4972, which is the SumOfQuantity). But I can't figure out how to layer on the SQL equivalent of a GROUP BY clause (which would sum by $3 or the [item_name], or what I think is the right path, the SQL equivalent of a WHERE clause to limit to either "Steak Burrito" or "Chicken Burrito". Based on my searhces it doesn't seem like you should mix $ grep and $ awk.... but logically the two would make sense (grep to limit to lines with the [item_name] I want, and awk to sum the [quantity] column). I did try to $ grep -i "steak burrito" chipotle.tsv |  awk '{sum+=$2} END {print sum}' chipotle.tsv but it still comes back with 4972. I could potentially "hack" a solution with $ grep -i "steak burrito" chipotle.tsv > chipotle2.tsv then $ awk '{sum+=$2} END {print sum}' chipotle2.tsv but that seems expensive. That all being said, using other tools I figured out that Chicken Burritos are more popular,  where Chicken Burrito = 591 and Steak Burrito = 386.
  
4. *Do chicken burritos more often have black beans or pinto beans?*  
    Using the following commands:  
    A. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "black beans" | wc -l (answer: 282)
    B. $ grep -i -E "chicken burrito" chipotle.tsv | grep -i -E "pinto beans" | wc -l (answer: 105)
    I found that Chicken Burrito orders are more often made with black beans.  
    **NOTE**: Same as above, I did not take [quantity] column into consideration. So I verifed based on orders, not items ordered.
    [Link to original solution resource](http://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/)  
    ** NOTE 2** Same as my Note 2 above, I couldn't layer in the WHERE clause to the summed quantity but the same concept would be involved. And again, using other tools I found that 'Chicken Burrito' + 'pinto beans' = 108, and 'Chicken Burrito' + 'pinto beans' = 307, so black beans are still ordered more often.

5. *Make a list of all of the CSV or TSV files in the [our class repo] (https://github.com/ga-students/DS-SEA-07). repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.*  
    Using this command:



6. *Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files of [our class repo] (https://github.com/ga-students/DS-SEA-7).*

**Optional**: *Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!*
