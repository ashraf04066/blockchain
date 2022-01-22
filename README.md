# blockchain

# Instructions to run the code: testing
...............................

Data Organization:
..................
1. A data folder exists in the same directory where Python files are located
2. Put edges2015 folder inside data directory. All input and output files should be under edges2015 folder.
3. For the darknet data, put the unzipped grams folder inside data directory
4. There should be a folder named intermediate_data inside data directory which is initially empty

Running Python Files:
....................
1. At first, run load_network.py file. It should write some file inside intermediate_data directory. Don't delete those files.
2. Secondly, run load_darknet.py file. It should also write some file inside intermediate_data directory. Don't delete those files.
3. At last, run get_features.py file. It will extract necessary features and write to a CSV file named output_features.csv. This csv file will be availabel inside data directory.

Features:
........
1. address_hash: Unique ID of the address
2. price: Bitcoin amount for the address
3. no_neighbor: No of extra output addresses of the transaction where this address is also an output
4. avg_price_neighbors: Average price/bitcoin amount of the neighbors of this address
5. month: month when the transaction of this address happened
6. day: day when the transaction of this address happened
7. is_bad_address: True if this address is a darknet address, False otherwise


Description of Features:
........................
1. address_hash: This feature is not used when train and test a model, as it cannot make any difference between good and bad addresses. 
2. price: If it happens that price ranges are different for bad addresses and good addresses, then price will help the model a lot to classify the bad and good addreses.
3. no_neighbor: Number of other output addresses for a transaction of an address might be helpful in classifying good and bad addresses if number of output address of attacked transactions differ significantly from that of non-attacked transactions.
4. avg_price_neighbors: In case the previous two features are helpful in classifying good and bad addresses, this feature should also be helpful. The intuition is that the average price of an attacked transaction should differ from that of a non-attacked transaction if price of attacked address and neighbors of attacked transaction vary from those of non-attacked addresses and transactions.
5. month and day: If it happens that bad addresses are more frequent for some specific dates compared to some other dates, knowing the transaction dates of each address is supposed to improve the classification accuracy of the model.
6. is_bad_address: This is the label of addresses indicating whether good or bad address.
