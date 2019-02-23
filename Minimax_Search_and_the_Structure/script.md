## Minimax Search and the Structure of Cognition!

[TITLE SLIDE: name, talk title, blog/social links]

It all started at my old dayjob, where some of my coworkers had an office chess game going. I wanted to participate and be part of the team, but I didn't want to invest the effort in actually learning how to play chess well. So, I did what any programmer would do and wrote a chess engine to do it for me.

[SLIDE: Leafline screenshots and repo]

(Actually, I felt like writing a chess engine was too much of a cliché, so I decided that _my_ program was an AI for a game that _happens_ to be exactly like chess, except that everything has different names.)

[SLIDE: chess vs. Leafline piece names]

My program wasn't actually terribly good, but I learned a lot about _how to think_, for the same reason that building a submarine in your garage in a great way to learn how to swim.

------

Consider a two-player board game like chess—or tic-tac-toe, Reversi, or indeed, _any_ two-player, zero-sum, perfect information game. Suppose we know how to calculate how "good" a particular board position is for a player—in chess, this is traditionally done by assigning a point value to each type of piece and totaling up the point values of remaining pieces for each player.

[SLIDE: chess_piece_relative_value.png]

Because only one player can win the game, what's good for one player is equally bad for the other: so if we add up all the piece values for one player, and _subtract_ all the piece values for the other, we get a "score" for the board position that the first player is trying to maximize, and the second player is trying to minimize.

[SLIDE: choice_pseudocode.png]

So consider a player pondering her move. For every possible legal move she could make, she knows what the board position will look like after that move, and can calculate the value of that position. So you might think she should choose the move that results in the best value: for example, if she can capture the opponent's queen, that would make the subsequent board position be worth 9 more points.

[SLIDE: game tree]

The problem with that is that it's short-sighted. If capturing the opponent's queen would just result in the opponent capturing the first player's queen back, then what looked like a 9 point gain after one turn, ends up being a wash after both players have taken their turn.

To take this into account, the first player should consider not just the immediate outcome of her move, but what the other player is likely to do after that. And the way the first player can compute what she predicts the second player will do is by asking, well, what would _I_ do if I were in that position, except trying to minimize the score rather than maximizing it?

[SLIDE: negamax_pseudocode.png]

... and so on recursively. So instead of just choosing the move with the best _immediate_ consequences, we want to look at the entire "game tree" of "my best move, _given_ her best move, _given_ my best move, _given_ her best move"—down to some given depth at which we give up, take the point count at face value, and propogate that information back up the call stack.

------

So, that's how you play chess. I want to tell you about two more philosophical insights I learned from this endeavor.

First, on the emergence of intstrumental goals. Some decision theorists like to distinguish between "terminal" goals and "instrumental" goals. Terminal goals are things that you want to achieve for their own sake—for example, love, or happiness, or winning a chess game. Whereas instrumental goals are things that you want to achieve _because_ they lead to terminal goals: for example, washing your hair, or getting enough sleep, or capturing one of your opponent's pawns.

Chess enthusiasts have names for special board situations that are advantageous for a player.

[SLIDE: fork.png]

For example, when a piece is in a position to attack two others, that's called a "fork"

[SLIDE: discovered_attack.png]

Or when one piece moves out of the way to "reveal" an attack by another, that's called a "discovered attack"

When observing a chess engine's behavior, it's very tempting to intepret it in such "psychological" terms, as: "Oh, it's 'trying' to set up a fork; it 'wants' to set up a discovered attack".

[SLIDE: again, negamax_pseudocode.png]

But it _can't_ be—_literally_ can't be—because those _concepts_ aren't _represented_ anywhere in the algorithm! The code is just brute-forcing the game tree to find sequences of moves that result in capturing material. Humans don't have the raw computational power to do this efficiently, so we tend to notice features of board situations that lead to capturing matrial and give them special names, and treat them as instrumental goals to be sought out—as, indeed, our piece-counting score in our chess engine is actually just an instrumental goal that happens to typically be useful towards the terminal goal of check mate.

Similarly, if you could do a God's-eye-view brute-force search for the optimal paths through a human life, _many_ such paths would, as a statistical regularity, happen to involve getting enough sleep—and if you have limited computational power, you might just want to treat that as an instrumental, tactical goal to reason about directly.

-----

Second insight! On counterfactual reasoning. The adversarial, recursive nature of this "my best move _given_ her best move _given_ my best move" _&c._ reasoning leads to some behavior that looks _very_ strange compared to how you would reason about optimizing an environment that _isn't_ intelligently opposing your goals. If you're not facing an intelligent opponent, you should just make plans to directly accomplish your goals: and in particular, you wouldn't bother trying things that you can _predict_ won't happen: you wouldn't bother packing your suitcase if you didn't intend to go anywhere.

On the other hand, maybe you _would_ bother loading a gun even if you didn't intend to fire it. When facing an intelligent opponent, you need to take into account how your choices affect your opponent's choices. This leads our algorithm to set up attacks that it _predicts_ won't be realized, because the credible _threat_ constrains the opposing player's choices: 

This position came up in a game with my coworkers as part of the engine's planning after moving the Black bishop to b5.

[SLIDE: scenario, pt. 1]

Here, the engine's predicted move for Black is knight to g3. At a first glance, this looked crazy to me: why would you move the knight to be diagonally in front of those pawns that could capture it?

[SLIDE: scenario, pt 2: moved knight, arrows illustrating threatening pawns]

And of course, what's actually happening is that moving the knight reveals a discovered attack of the black bishop on f5 against the white queen on c2.

[SLIDE: scenario, pt. 3: illustrate discovered attack]

Saving the queen is more important to White than capturing the black knight, allowing Black to use _her_ next turn to capture the white rook on h1.

[SLIDE: scenario, pt. 4: captured "rook"/cop]

But this is pretty weird, right? The algorithm has gone to all this trouble to set up a discovered attack on the white queen—in order to capture the white rook, not the queen!

This kind of behavior has analogues in real life whenever you have situations where different agents, different systems, have conflicting goals and can respond to each other's behavior. If people can _predict_ that _if_ they were to commit crimes, then they would be punished—that incentivizes them to obey the law in the first place: the _threat_ of punishment is shaping the population's behavior even if no one is going to be actually punished for that very reason.

There's an [old joke](https://www.nytimes.com/1988/01/02/opinion/elephant-repellent.html) about a UC Santa Cruz student sprinkling powder outside her dorm, who, when questioned, responds, "Oh, this? It's elephant repellant!"

The questioner replies, "But there aren't any elephants in Santa Cruz!"

The student counterreplies, "Well, that's how you know it's working!"

But you see, sometimes, that actually is the explanation. Thank you.
