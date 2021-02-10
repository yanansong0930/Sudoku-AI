# Sudoku-AI
Design different algorithms to implement a Sudoku AI

1. MRV
The main idea of MRV is to find the variable with the fewest possible values. Thus, I try to find the unassigned variable with the fewest number of domains and return it. I iterate through all variables in the network, looking for unassigned variable and compare the size of its domain, which is the number of possible values. Finally return the variable that has the minimum size of domain in the end.
2.  LCV
LCV asks us to choose the least constraining value for a given variable. I create a map with all possible values of the variable as keys. Then I count how many times that each possible value appears as possible values of the variable’s neighbor and store it in the map. A list of those
possible values are returned in as a list with ascending order in constrained neighbors.
3.  FC
Our FC algorithm is straightforward. I iterate through all the variables in the network. When finding an assigned variable, I’ll check its neighbors. If any neighbor’s domain still contains the value which the variable is assigned to, I’ll push the neighbor in the trail in convenience of getting back and remove the value from its domain. If there is no possible value for the neighbor, I’ll directly return False and stop the iteration, since the current assignment is inconsistent.
4.  NOR
In this part, I follow Norvig’s basic Sudoku strategies. The first strategy is similar to what I did in the FC function. For the second strategy, I create a counter map for each
constraint with all the possible values (which is N) as keys. Then I iterate through all the variables in the constraint and their possible values. For each possible value, I add one to the corresponding value in the counter. At last I check the counter map. If there’s any value that only counted once, I find the variable that contains this value in the domain and assign it with the value. I check the consistency of the whole game board at the end.
5. MAD
First, I define a helper function similar to MRV function which returns a list of variables with the same smallest domain. The idea of tie breaker is that the variable affecting the most unassigned neighbors has the priority to be assigned. Thus, I iterate through all variables returned from the helper function, check their neighbors and record the number of unassigned ones. I find the variable with most unassigned neighbors, put them in the list and return them.
