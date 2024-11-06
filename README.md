java c
Assignment 2 - Wacky Wonderland

It's the early 2000s and the internet is transforming rapidly with companies racing to develop new and groundbreaking technologies. After your fantastic job automating tasks at Wacky's Restaurant, she now has the time and resources to explore new ventures. Inspired by the internet boom, Wacky has decided to create a platform. where users can enjoy her games. Your task is to build a basic user authentication system for her service as well as design one of her games — Numbers Search!
Get the starter code here: a2.zip (https://q.utoronto.ca/courses/362212/files/33843607?wrap=1)
(https://q.utoronto.ca/courses/362212/files/33843607/download?download_frd=1)
Goals:
Use the function design recipe to plan, implement, and test your functions.
Write function bodies using lists and loops, including nested lists and nested loops. You can do this whole assignment with the concepts taught from Weeks 1 to 6.
Understand how to create, navigate, and mutate lists and nested lists of numerical values.
A pinned thread on Piazza will be available for any corrections or clarifications. Be sure to check it regularly for updates.
Your Tasks:
For this assignment, you will be required to complete the functions inside wonderland.py using the Function Design Recipe that you have been learning in class. Below, we have provided a detailed summary for key functions along with their intended usage. It will be your responsibility to paraphrase these descriptions in order to write appropriate docstring descriptions.
0. Preventing Mutation through Copying Values
During this assignment, you may run into a situation where you need to duplicate an array or matrix without affecting the original.>>> a = [1, 2, 3]
>>> b = a
>>> b[2] = 0
>>> print(a)
[1, 2, 0]
In the example above, notice how modifying also modifies ? This is because is a reference to the values of . We can prevent this by declaring as an independent copy of . This way, modifications to will not affect .
>>> a = [1, 2, 3]
>>> b = deepcopy(a)
>>> b[2] = 0
>>> print(a)
[1, 2, 3]
>>> print(b)
[1, 2, 0]
Why is this useful? Suppose Wacky gives you an important list of numbers to perform. some action on (eg. find the median of the list). But to find the median - you would need a sorted list. You don't want to sort Wacky's list (that list is important to her)! The alternative is to copy all her numbers to your own list, and perform. actions on that instead.
Note: You are not required to use deepcopy on your assignment. If you decide to create your own copy (eg. create a new array and append values), feel free to remove the import at the top of the file.
1. Validating Account Numbers is_valid_account(num_array: list[int]) -> bool
Wacky wants to ensure that only paying customers have access to her platform. To achieve this, she provides each customer with a unique list of numbers, which they use to verify their identity. The verification process relies on Wacky's Algorithm, a customized version of Luhn's Algorithm. The specific details of the algorithm are described below.
Given a list of non-negative numbers with a minimum size of 3, divide the list into three parts: payload, multiplier, and modulo. The last two elements in the list will always represent the multiplier and the modulo, respectively. All remaining elements before them will make up the payload.

1. Starting from the rightmost digit of the payload and moving left, multiply every second digit by the multiplier.
2. Afterwards, split all numbers into their individual digits and take the sum.
3. Finally, add all the sums together to get a final total sum.
4. The account number is valid if and only if the resulting sum modulo 10 is equal to the modulo variable.

2. Memory Trail
Wacky is introducing a game called Memory Trail. In this game, players are shown a list of numbers and later quizzed about it. Your task is to develop efficient code that will help answer these questions.
A. What's the median? memory_median(num_array: list[int]) -> float
Wacky presents players with a possibly unordered list of numbers and asks them to determine the median. The median is the middle value in a sorted list. If the list has an even number of elements (meaning there will be two middle numbers), the median is calculated as the average of the two middle numbers.

B. What's that sequence? memory_sequence(num_array: list[int]) -> list[int]
Wacky challenges players to recall a list of numbers in the correct sequence. To make it more interesting, she includes repeating numbers. Players must repeat the numbers in the order of their first appearance, ignoring any duplicates.

C. How many times did it happen? memory_count(num_array: list[int], recall_array: list[int]) -> list[int]
Wacky provides players with a list of numbers and challenges them to count how many times specific numbers appear. To raise the difficulty, Wacky asks about multiple numbers at once, including ones that never appeared in the list at all, and players must respond with all the counts in a single answer.

Explanation: 1 occurs 2 times. 5 occurs 1 times. 7 occurs 0 times. 2 occurs 3 times.
3. Numbers Search
Numbers Search is a game that is a variation o代 写Assignment 2 - Wacky WonderlandPython
代做程序编程语言f word search — however you are searching for series of numbers instead of letters! In this section, you'll use loops and lists to develop algorithms that search for specific numbers within a grid. Your task is to write efficient code to help find the hidden numbers in the grid.
Note: All matrices must be in row-major format, including matrices those from function returns.
Note: You may assume all matrices provided as an argument have at least one element.

A. Swap Around swap_around(matrix: list[list[int]]) -> list[list[int]]
Given an integer matrix of size , return a new integer matrix of size that swaps the rows and columns of the original (also known as transpose). The original matrix must remain unmodified. The resulting matrix must appear in the exact order as shown below.

B. Searching in a List search_list(num_list: list[int], series: list[int]) -> int
Given a list of integers, search for and return the index of the first occurrence of a specified series of numbers. The numbers must match in the exact order provided but can also be matched in reverse order. If no matches are found, return .

C. Searching in a Matrix's rows search_rows(matrix: list[list[int]], series: list[int]) -> bool
Given a matrix of size , return True if and only if a specified series of numbers can be found in the rows of the matrix. The numbers must match in the exact order provided but can also be matched in reverse order. If no matches are found, return False .

D. Searching in a Matrix's Columns search_columns(matrix: list[list[int]], series: list[int]) -> bool
Given a matrix of size , return True if and only if a specified series of numbers can be found in the columns of the matrix. The numbers must match in the exact order provided but can also be matched in reverse order. If no matches are found, return False .

E. Searching in a Matrix's Diagonals search_diagonals(matrix: list[list[int]], series: list[int]) -> bool
Given a matrix of size , return True if and only if a specified series of numbers can be found in the diagonals of the matrix. The numbers must match in the exact order provided but can also be matched in reverse order. If no matches are found, return False .
Hint: This will be a relative large function. You may find it incredibly helpful to plan this function out in advance.
This end goal isn't much different than searching in columns or rows - we're still searching for a list, as we've already done above.
Can we reduce the matrix into a bunch of lists, then just search that instead? Wouldn't it be much easier to search the series in [3], [8, 4], [1, 8, 5] ...

F. Validating Coordinates in a Matrix validate_coordinates(matrix: list[list[int]], row_idx: int, col_idx: int, series: list[int]) -> bool
Given a matrix of size , a series of numbers, and the indices represent a row and column inside the matrix, return True if and only if the specified series of numbers can be found at and overlap the given indices inside the matrix either via row, column, or diagonal. The numbers must match in the exact order provided but can also be matched in reverse order. If no matches are found, return False .
Hint: You may find it incredibly helpful to plan this function out in advance. Similar to , the end goal here is still the same — we want to search for a list in a group of lists.
The number of lists in this question is constant (one for each direction). How many lists do you always have to build?
What are the constraints of the list? How far away do we really have to search from a coordinate?
It may be helpful to think of the question in terms of a single dimension first. What if the question was rephrased to being given a List L , Index I , and Series S ?

Marking:
These are the aspects of your work that may be marked for A2:
Coding style. (20%):
Make sure that you follow Python style. guidelines that we have introduced and the Python coding conventions that we have been using throughout the semester. Although we don't provide an exhaustive list of style. rules, the checker tests for style. are complete, so if your code passes the checker, then it will earn full marks for coding style. with one exception: docstrings will be evaluated separately.
For each occurrence of a PyTA
(https://www.cs.toronto.edu/~david/pyta/checkers/index.html#style-errors) error, a one mark deduction will be applied. For example, if a C0301 line-too-long error occurs 3 times, then 3 marks will be deducted.
PyTA style. checks are done entirely by using a2_checker.py . You must successfully run this program to determine any styling issues.
All functions, including helper functions, should have complete docstrings including preconditions when you think they are necessary and at least two valid examples.
Correctness (80%):
Your functions should perform. as specified. Correctness, as measured by our tests, will count for the largest single portion of your marks.
Once your assignment is submitted, we will run additional tests not provided in the checker. Passing the checker does not mean that your code will earn full marks for correctness.
It is highly recommended that students write their own tests, on top of the ones already given.



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
