## Minimax Search and the Structure of Cognition!

[TITLE SLIDE: name, talk title, blog/social links]

It all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team, but I didn't want to invest the effort in actually learning how to play chess well. So, I did what any programmer would do and wrote a chess engine to do it for me.

[SLIDE: Leafline screenshots and repo]

(Actually, I felt like writing a chess engine was too much of a cliché, so I decided that _my_ program was an AI for a game that _happens_ to be exactly like chess, except that everything has different names.)

[SLIDE: TODO chess vs. Leafline piece names]

My program wasn't actually terribly good, but I learned a lot about how to think—how the process of making subjectively free-willed decisions can be reduced to an algorithm.

------

Consider a two-player board game like chess—or tic-tac-toe, Reversi, or indeed, _any_ two-player, zero-sum, perfect information game. Suppose we know how to calculate how "good" a particular board position is for a player—in chess, this is traditionally done by assigning a point value to each type of piece and totaling up the point values of remaining pieces for each player.

[SLIDE: chess_piece_relative_value.png]

Because only one player can win the game, what's good for one player is equally bad for the other: so if we add up all the piece values for one player, and _subtract_ all the piece values for the other, we get a "score" for the board position that the first player is trying to maximize, and the second player is trying to minimize.

[SLIDE: choice_pseudocode.png]

So consider a player pondering her move. For every possible legal move she could make, she knows what the board position will look like after that move, and can calculate the value of that position. So you might think she should choose the move that results in the best value: for example, if she can capture the opponent's queen, that would make the subsequent board position be worth 9 more points.

The problem with that is that it's short-sighted. If capturing the opponent's queen would just result in the opponent capturing the first player's queen back, then what looked like a 9 point gain after one turn, ends up being a wash after both players have taken their turn.

[SLIDE: TODO game tree]

To take this into account, the first player should consider not just the immediate outcome of her move, but what the other player is likely to do after that. And the way the first player can compute what she predicts the second player will do is by asking, well, what would _I_ do if I were in that position, except trying to minimize the score rather than maximizing it?

[SLIDE: negamax_pseudocode.png]

... and so on recursively. So instead of just choosing the move with the best _immediate_ consequences, we want to look at the entire "game tree" of "my best move, _given_ her best move, _given_ my best move, _given_ her best move"—down to some given depth at which we give up, take the point count at face value, and propogate that information back up the call stack.

------

So, that's how you play chess. I want to tell you about two surprising philosophical implications I learned from this endeavor.

First, on the emergence of intstrumental goals. Some decision theorists like to distinguish between "terminal" goals and "instrumental" goals. Terminal goals are things that you want to achieve for their own sake—for example, love, or happiness, or winning a chess game, or godlike understanding of the true structure of the world beneath the world. Whereas instrumental goals are things that you want to achieve _because_ they lead to terminal goals: for example, washing your hair, or getting enough sleep, or capturing one of your opponent's pawns.

Chess enthusiasts have names for special board situations that are advantageous for a player.

[SLIDE: fork.png]

For example, when a piece is in a position to attack two others, that's called a "fork"

[SLIDE: discovered_attack.png]

Or when one piece moves out of the way to "reveal" an attack by another, that's called a "discovered attack"

When observing a chess engine's behavior, it's very tempting to intepret it in such "psychological" terms, as: "Oh, it's 'trying' to set up a fork; it 'wants' to set up a discovered attack".

[SLIDE: again, negamax_pseudocode.png]

But it _can't_ be, because those _concepts_ aren't _represented_ anywhere in the algorithm! The code is just brute-forcing the game tree to find sequences of moves that result in capturing material. Humans don't have the raw computational power to do this efficiently, so we tend to _notice_
