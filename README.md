# runoff
a program that runs a runoff election

Specification
Complete the implementation of runoff.c in such a way that it simulates a runoff election. You should complete the implementations of the vote, tabulate, print_winner, find_min, is_tie, and eliminate functions, and you should not modify anything else in runoff.c (and the inclusion of additional header files, if you’d like).

vote
Complete the vote function.
	 The function takes arguments voter, rank, and name. If name is a match for the name of a valid candidate, then you should update the global preferences array to indicate that the voter voter has that candidate as their rank preference (where 0 is the first preference, 1 is the second preference, etc.).
	 If the preference is successfully recorded, the function should return true; the function should return false otherwise (if, for instance, name is not the name of one of the candidates).
	 You may assume that no two candidates will have the same name.
Hints
	 Recall that candidate_count stores the number of candidates in the election.
	 Recall that you can use strcmp to compare two strings.
	 Recall that preferences[i][j] stores the index of the candidate who is the jth ranked preference for the ith voter.

tabulate
Complete the tabulate function.
	 The function should update the number of votes each candidate has at this stage in the runoff.
	 Recall that at each stage in the runoff, every voter effectively votes for their top-preferred candidate who has not already been eliminated.
Hints
	 Recall that voter_count stores the number of voters in the election.
	 Recall that for a voter i, their top choice candidate is represented by preferences[i][0], their second choice candidate by preferences[i][1], etc.
	 Recall that the candidate struct has a field called eliminated, which will be true if the candidate has been eliminated from the election.
	 Recall that the candidate struct has a field called votes, which you’ll likely want to update for each voter’s preferred candidate.

print_winner
Complete the print_winner function.
	 If any candidate has more than half of the vote, their name should be printed to stdout and the function should return true.
	 If nobody has won the election yet, the function should return false.
Hints
	 Recall that voter_count stores the number of voters in the election. Given that, how would you express the number of votes needed to win the election?

find_min
Complete the find_min function.
 The function should return the minimum vote total for any candidate who is still in the election.
Hints
	 You’ll likely want to loop through the candidates to find the one who is both still in the election and has the fewest number of votes. What information should you keep track of as you loop through the candidates?

is_tie
Complete the is_tie function.
	 The function takes an argument min, which will be the minimum number of votes that anyone in the election currently has.
	 The function should return true if every candidate remaining in the election has the same number of votes, and should return false otherwise.
Hints
	 Recall that a tie happens if every candidate still in the election has the same number of votes. Note, too, that the is_tie function takes an argument min, which is the smallest number of votes any candidate currently has. How might you use that information to determine if the election is a tie (or, conversely, not a tie)?

eliminate
Complete the eliminate function.
	 The function takes an argument min, which will be the minimum number of votes that anyone in the election currently has.
	 The function should eliminate the candidate (or candidates) who have min number of votes.
