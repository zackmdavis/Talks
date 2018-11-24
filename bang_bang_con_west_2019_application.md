> Talk Title \*

Minimax Search and the Structure of Cognition!

> Abstract for your talk \*

We discuss an algorithm for playing chess—or Reversi, or Tic-Tac-Toe, or indeed, any two-player, zero-sum, perfect information game—and its surprising philosophical implications for cognitive science, free will, and ourselves.

> Timeline for your talk \*

Origin story (1 minute): it all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team but I didn't want to invest the effort 

The minimax algorithm (4 minutes): For a two-player board game like chess (or Reversi, or ...), if we know how to evaluate how "good" a position is for a player (and, by zero-sumness, how bad it is for the other player), and we know how to compute the set of legal next moves given a position, then we can recursively search the "game tree" to a given depth, working out "my best move, _given_ her best reply, _given_ my best counterreply, _given_ her best counter-counterreply ..." The game tree grows exponentially, but there's a trick to speed it up called alpha-beta pruning, in which we keep track of the best guaranteed score for each player and eliminate branches of the game tree that are "too good to be true," that require a player to act against her own interest.

Surprising philosophical implications thereof (5 minutes): instrumental goals that aren't part of the algorithm, counterfactuals 

> Intended audience \* What kind of background knowledge will your audience need to be able to get something out of your talk?

familiarity with recursion

> Your name \*

Zack M. Davis

> Your email address \*

—

> Short bio \*

Zack M. Davis is a programmer and epistemology enthusiast residing in Berkeley, CA.

> If you consider yourself to be part of any groups that are underrepresented in tech, please share that here (if you feel comfortable)

somewhat gender-dysphoric (but not currently transitioning)
