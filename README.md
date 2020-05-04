# GetCoin
---------
What is a Blockchain?
----------------------
Blockchain is just a chain of blocks. 
Where each block in the blockchain will have its own digital fingerprint which is called - 'Hash', 
And also contain the digital fingerprint of the previous block, and have some data in form of anything (Could be transactions, could be strings).
Each block doesn’t just contain the hash of the block previous to it, but its own hash is in part, calculated from the previous hash. 
If the previous block’s data is changed then the previous block’s hash will change (since it is calculated in part, by the data),
In turn affecting all the hashes of the blocks there after. 
Calculating and comparing the hashes allow us to see if a blockchain is invalid or not.

What GetCoin Does and how GetCoin qualifies as a BlockChain?
-------------------------------------------------------------
GetCoin does the same it creates hashes (the digital fingerprints) and some data into it.
It uses uses SHA256 Algorithm to generate fingerprints and is done by importing 'java.security.MessageDigest;'
It takes a string and applies SHA256 algorithm to it, and returns the generated signature as a string.
For more in-dept working of GetCoin check out the README.md and focus on #Project related#.

-----------------------------------------------
#Question & Answers#
-------------------
Q1. What is GetCoin?
--------------------
A personal BlockChain generator created and programmed in JAVA.

Q2. What are the properties of GetCoin?
---------------------------------------
1. It is made up of blocks that store data.
2. Has a digital signature that chains your blocks together.
3. Requires proof of work mining to validate new blocks.
4. Can be check to see if data in it is valid and unchanged.

Q3. Who made GetCoin?
---------------------
https://github.com/sarnav98
------------------------------

#Project related#
-----------------
Block class:
------------
As you can see our basic Block contains a String hash that will hold our digital signature. 
The variable previousHash to hold the previous block’s hash andString data to hold our block data.

StringUtility class:
--------------------
Next we will need a way to generate a digital fingerprint,
there are many cryptographic algorithms you can choose from, however SHA256 fits just fine for this example. We can import java.security.MessageDigest; to get access to the SHA256 algorithm.
We need to use SHA256 later down the line so lets create a handy helper method in a the class.
It takes a string and applies SHA256 algorithm to it, and returns the generated signature as a string.
'applySha256' helper, in a new method in the Block class, to calculate the hash. 
We must calculate the hash from all parts of the block we don’t want to be tampered with. 
So for our block we will include the previousHash, the data and timeStamp.

GetCoin class:
--------------
isChainValid() Boolean method in the GetCoin class, 
that will loop through all blocks in the chain and compare the hashes. 
This method will need to check the hash variable is actually equal to the calculated hash, 
and the previous block’s hash is equal to the previousHash variable.

Any change to the blockchain’s blocks will cause this method to return false.

We will require miners to do proof-of-work by trying different variable values in the block until its hash starts with a certain number of 0’s.
Lets add an 'int' called 'nonce' to be included in our calculateHash() method, and the much needed mineBlock() method.

In reality each miner will start iterating from a random point. 
Some miners may even try random numbers for nonce. 
Also it’s worth noting that at the harder difficulties solutions may require more than integer.
MAX_VALUE, miners can then try changing the timestamp.

The mineBlock() method takes in an int called difficulty, this is the number of 0’s they must solve for. 
Low difficulty like 1 or 2 can be solved nearly instantly on most computers.
I’d suggest something around 4–6 for testing. 
At the time of writing Litecoin’s difficulty is around 442,592.

What is difficulty? -> https://en.bitcoin.it/wiki/Difficulty

*public static int difficulty = 5;* // This keeps the diffuculty=5 for our GetCoin.

The GetCoin class to trigger the mineBlock() method for each new block. 
The isChainValid() Boolean should also check if each block has a solved by mining thehash.

----------------

Requirements ->
-------------
You will need:
Java and JDK installed
Eclipse / IntelliJ ( or another IDE/Text Editor ).

Dependencies -> 
---------------

GSON 2.6.2 - Link -> https://repo1.maven.org/maven2/com/google/code/gson/gson/2.6.2/gson-2.6.2.jar

Why use GSON ->
-------------
This will allow us to turn an object into JSON.
It’s a super useful library that we will also be using further down the line for PEER-TO-PEER stuff.
But you can try any other method.

--------------------------------------------------------------------------------------
Thank you and Keep supporting -> https://github.com/sarnav98
-------------------------------------------------------------
Created by - https://github.com/sarnav98.
-----------------------------------------
