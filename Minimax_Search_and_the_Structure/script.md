## Minimax Search and the Structure of Cognition!

It all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team, but I didn't want to invest the effort in actually learning how to play chess well. So, I did what any programmer would do and wrote a chess engine to do it for me.

(Actually, I felt like writing a chess engine was too much of a cliché, so I decided that _my_ program was an AI for a game that _happens_ to be exactly like chess, except that everything has different names.)

[SLIDE: chess vs. Leafline piece names]

My program wasn't actually terribly good, but I learned a lot about how to think—how the process of making subjectively free-willed decisions can be reduced to an algorithm.

------

Consider a two-player board game like chess—or tic-tac-toe, Reversi, or indeed, _any_ two-player, zero-sum, perfect information game. Suppose we know how to calculate how "good" a particular board position is for a player—in chess, this is traditionally done by assigning a point value to each type of piece and totaling up the point values of remaining pieces for each player.

[SLIDE: chess point values]

Because only one player can win the game, what's good for one player is equally bad for the other: so if we add up all the piece values for one player, and _subtract_ all the piece values for the other, we get a "score" for the board position that the first player is trying to maximize, and the second player is trying to minimize.

[SLIDE: choice pseudocode]

So consider a player pondering her move. For every possible legal move she could make, she knows what the board position will look like after that move, and can calculate the value of that position. So you might think she should choose the move that results in the best value: for example, if she can capture the opponent's queen, that would make the subsequent board position be worth 9 more points.

The problem with that is that it's short-sighted. If capturing the opponent's queen would just result in the opponent capturing the first player's queen back, then what looked like a 9 point gain after one turn, ends up being a wash after both players have taken their turn.

[SLIDE: game tree]

To take this into account, the first player should consider not just the immediate outcome of her move, but what the other player is likely to do after that. And the way the first player can compute what the second player will do is by asking, well, what would _I_ do if I were in that position, except trying to minimize the score rather than maximizing it?

[SLIDE: negamax pseudocode]

... and so on recursively. So instead of just choosing the move with the best _immediate_ consequences, we want to look at the entire "game tree" of "my best move, _given_ her best move, _given_ my best move, _given_ her best move"—down to some given depth at which we give up and just take the point count at face value.

------

So, that's how you play chess. I want to tell you about two surprising philosophical implications I learned from this endeavor.

-----