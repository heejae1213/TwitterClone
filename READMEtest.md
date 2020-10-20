# Neeva SWE Coding Project: Text Editor - General/Infrastructure

Improving current text editor with a focus on performance.

## High-level Approach

In a nutshell, I've approached this problem in two steps. 

First off, I've analyzed performance of functionalities of the program with regard to time.

There are four functionalities in this program - **Cut & Paste**, **Copy & Paste**, **Text Retrieval**, and **Finding Misspellings** - and below is my analysis regarding the four functionalities.

* **Cut & Paste**: Basic list slicing.
* **Copy & Paste**: Basic list slicing.
* **Text Retrieval**: Just returning the argument. Not much operation here.
* **Misspellings**: Since the function looks up on a **Set** to find out if the word is in the Set or not, the time complexity of the function is **O(1*n)**, where n is the number of words queried at a time.
Though I think current choice of data structure is optimal in terms of time consumed for operations, I wanted to add more structure to it.
So I've implemented a **Dictionary** which has (key: first character of the word (ex. 'A', 'B', ...), value: set of the words that start with certain alphabet) as its elements.

After analyzing existing functions and modifying a bit, I decided to add an additional functionality to ***misspellings()*** to manage misspellings in a more sophisticated way.

I decided to implement a function that returns a list of words that could have been the actual intent of the user for misspellings.

For example, if the user types in "hel", the program will return a list of words that start with "hel", such as ["helbeh", "helcoid", ..., "helvite"].

It could be used towards autocomplete or misspelling correction feature of the text editor.

## How to run this program
Run ``` python editor.py ```

## Design decisions or tradeoffs I've made

* Modified current data structure by implementing a **Dictionary** that carries (key: first character of the word (ex. 'A', 'B', ...), value: set of the words that start with certain alphabet) as its elements.

➡️ Comparing the time consumed for ***misspellings()*** with Set and Dictionary, there was not much difference between them.
So, I've decided to add more structure to the data structure.

* Implemented **Trie** to support misspellings corrections or autocomplete feature.

➡️ Assumed that I have enough space to have both Dictionary and Trie.

## Extensions I would like to add if I had more time

In the problem statement, it's stated that this text editor is for better development workflow.
That being stated, I think there is not much variation in vocabs that are used in Software Development.
There should be a list of vocabs that are used frequently.
Therefore, I think having a cache for those frequently used vocabs could improve the program efficiency. From my quick thought, I think keeping MostRecentlyUsed cache might improve the program efficiency.
