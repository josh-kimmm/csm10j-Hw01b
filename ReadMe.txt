Josh Kim
CSM10J
10-6-2015

Create 5 different vectors to store name of stock, stock min price, stock max price, stockprice total, and # of stocks
in the file

Run a loop to read from file "stocks.txt" b/c it is default file, close input file once done reading.

Compare name of stock that computer already knows to new input. If there is no record of that stock name add an element
to each vector. Each element of the vector stands for a different stock name.

If there is same name of stock then compare that stock price to the current max and min stock price. If the current stock
price is greater than the max stock price for that stock name, set max stock price to current stock price being read.

Once you insert new stock price to the specified index you must remove the contents of the following element. The
following element contained contents of the old element that you replaced.

Do the same thing for min, total, and avg

Display options, if option '1' was chosen use total stock price and # of stocks to calculate the average of whatever
file the user decides to input(case insensitive).

If a new file was chosen to be read from, option 'c', make new vectors with same name to replace old vectors to store
new data from new file and repeat steps.

