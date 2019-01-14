## Minimax Search and the Structure of Cognition!

It all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team, but I didn't want to invest the effort in actually learning how to play chess well. So, I did what any programmer would do and wrote a chess engine to do it for me.

(Actually, I felt like writing a chess engine was too much of a cliché, so I decided that _my_ program was an AI for a game that _happens_ to be exactly like chess, except that everything has different names.)

[SLIDE: chess vs. Leafline piece names]

My program wasn't actually terribly good, but I learned a lot about how to think—how the process of making subjectively free-willed decisions can be reduced to an algorithm.

------

Consider a two-player board game like chess—or tic-tac-toe, Reversi, or indeed, _any_ two-player, zero-sum, perfect information game. Suppose we know how to calculate how "good" a particular board position is for a player—in chess, this is traditionally done by assigning a point value to each type of piece and totaling up the point values of remaining pieces for each player.

[SLIDE: chess point values]

Because only one player can win the game, what's good for one player is equally bad for the other.

if we know how to evaluate how "good" a position is for a player (and therefore, by zero-sumness, how bad it is for the other player), and we know how to compute the set of legal next moves given a position, then we can recursively search the "game tree" to a given depth, working out "my best move, GIVEN her best reply, GIVEN my best counterreply, GIVEN her best counter-counterreply ..." The game tree grows exponentially, but there's a trick to speed it up called alpha-beta pruning, in which we keep track of the best guaranteed score for each player and eliminate branches of the game tree that are "too good to be true," which would require a player to act against her own interest.
