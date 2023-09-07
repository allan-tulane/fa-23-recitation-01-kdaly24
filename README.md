[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11681173&assignment_repo_type=AssignmentRepo)
# CMPS 2200  Recitation 01

**Name (Team Member 1):**____Killian Daly________  
**Name (Team Member 2):**_________________________

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

The worst case input value for key would be a value which does not exist in the list. In this way, the linear search and binary search would both check every item in their list before realizing it does not contain the key and returning -1. 

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

The best case input value for linear_search key is the value at list item 0. For binary search, it would be key is == testvar, or the middle item in the list. In the searches, these respective answers are the first checked value in the search and thus the best case.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.016 |    0.033 |
|      100.000 |    0.018 |    0.010 |
|     1000.000 |    0.176 |    0.014 |
|    10000.000 |    1.758 |    0.021 |
|   100000.000 |   19.513 |    0.041 |
|  1000000.000 |  170.490 |    0.040 |
| 10000000.000 | 1396.413 |    0.041 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

Yes, my results match the theoretical running times of the two searches. As we can see from my above graph, the linear search time complexity scales linearly alongside the number of items needing to be searched, whereas binary search sees a modest, if not negligble, increase as number of items increases. This is due to the binary search methodology effectively shortening the number of items that must be checked against the key.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search?
   
   I would imagine that it takes $O(kn)$ time to search a list of $n$ elements $k$ times, as you would not need to sort a list if you are progressing every element and checking it against the key. The search would iterate $k$ times through the worst case time complexity of linear search, $O(n)$. This should return a worst case time complexity of $O(kn)$.

  + For binary search? 

  For binary search, it should be $\Theta(n^2)$ + $O((log_2(n)) * k)$. We account for the time complexity to sort ($\Theta(n^2)$), and then the searches, which would utilize the worst case time complexity of binary search $O(log_2(n))$ multiplied by $k$ iterations.

  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? 

  As $k$ represents the number of times a list is searched, the binary search with sort will be superior for every $k$ value over 1. If the list is searched just one time, then the time it takes to sort $\Theta(n^2)$ + the search time for binary may exceed the time of a single linear search. However, the worst run time complexity for binary search is $O((log_2(n)) * k)$, which is more efficient than the runtime $O(kn)$, especially as k increases from 1 to higher constants and impacts $O(kn)$ and Linear efficiency more than binary.


  

