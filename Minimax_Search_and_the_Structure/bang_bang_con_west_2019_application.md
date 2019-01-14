> Talk Title \*

Minimax Search and the Structure of Cognition!

> Abstract for your talk \*

We discuss an algorithm for playing chess—or Reversi, or Tic-Tac-Toe, or indeed, any two-player, zero-sum, perfect information game—and its surprising philosophical implications for cognitive science, free will, and ourselves.

> Timeline for your talk \*

Origin story (1 minute): it all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team but I didn't want to invest the effort in actually learning how to play chess well. So, I did what any programmer would do and wrote a chess engine to do it for me. My program wasn't actually terribly good (compared to my coworkers or other hobby chess engine projects on GitHub), but I learned a lot about how to think—how the process of making subjectively free-willed decisions can be reduced to an algorithm.

The minimax algorithm (4 minutes): For a two-player board game like chess (or Reversi, or ...), if we know how to evaluate how "good" a position is for a player (and therefore, by zero-sumness, how bad it is for the other player), and we know how to compute the set of legal next moves given a position, then we can recursively search the "game tree" to a given depth, working out "my best move, GIVEN her best reply, GIVEN my best counterreply, GIVEN her best counter-counterreply ..." The game tree grows exponentially, but there's a trick to speed it up called alpha-beta pruning, in which we keep track of the best guaranteed score for each player and eliminate branches of the game tree that are "too good to be true," which would require a player to act against her own interest.

Two surprising philosophical implications thereof—

Emergence of instrumental goals (2.5 minutes): when observing the program's behavior, it's tempting to interpret it in "psychological" terms: "Oh, it's trying to set up a 'fork' (where one piece is in a position to attack two others) or a 'discovered attack' (where moving one piece 'reveals' an attack by a rook, bishop, or queen behind it)". But the concept of "trying to set up a fork" isn't represented anywhere in the program! Rather, it just so happens that the "brute force" minimax search frequently turns up move sequences that happen to contain clever tactics that humans have given names to—specifically because they happen to turn up in move sequences that lead to the capture of material (itself an instrumental goal towards the ultimate goal of checkmate). This has analogues in human life insofar as good habits and best practices (e.g., get enough sleep, refactor your code to be reusable) can be viewed either as goals in themselves, or instrumental stepping-stones that emerge on the way to actual goals.

Counterfactual reasoning (2.5 minutes): the adversarial, recursive nature of "my best move GIVEN her best move GIVEN ..." reasoning leads the algorithm to "set up attacks" (in the emergent sense just described) that it predicts won't be realized, because of how they affect the opponent's behavior. (I'll describe a specific example with the aid of a slide showing the board position.) This also has real-world analogues (e.g., people obeying the law they're aware of the possibility of being punished, even though they won't in fact be punished for that very reason).

> Intended audience \* What kind of background knowledge will your audience need to be able to get something out of your talk?

familiarity with recursion, familiarity with how chess pieces move is optional but helpful

> Your name \*

Zack M. Davis

> Your email address \*

—

> Short bio \*

Zack M. Davis (GitHub: zackmdavis / Twitter: @zackmdavis) is a programmer and epistemology enthusiast residing in Berkeley, CA.

> If you consider yourself to be part of any groups that are underrepresented in tech, please share that here (if you feel comfortable)

somewhat gender-dysphoric (but not currently transitioning)
