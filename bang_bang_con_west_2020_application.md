> Talk title \*
A Bit of a Question (Literally!); Or, Optimal Hypothesis Generation and the Structure of Cognition!

> Abstract \*

How one programmer's hatred of games drove them to probe the secrets of mind and cognition—to build a machine that can guess what you're thinking! (Live demonstration included.)

> Timeline \*

Origin story and problem statement! (3 minutes): I hate games. I have a few friends who just love niche board games—you know, Hive, Settlers of Catan, what have you. And I can't stand it, because a lot of being good at these games is thinking ahead trying to see which moves are best, and it's just so embarrassing and painful trying to do this with a human brain—that's what we have computers for! I'm always more interested in writing programs to play games for me, rather than playing myself. My friend had a meetup group for playing Zendo, a game where one player, the "master" thinks of a rule that classifies arrangements of plastic pyramids as either matching the rule, or not matching the rule. Other players supply examples that the master classifies, and try to guess the rule. It's really like science itself: you have to think of a hypothesis that matches the data (which plastic-pyramid-arrangements have been said to match or not-match the rule). One day, while rushing to the Zendo meetup, the Code Muse spoke to me in song ("We will classify our gloss'ry of shapes into compliance! / We are magical methodical apes doing triangle science!") and decreed that I had to write a program to solve Zendo as a non-master player: the user should secretly think of a rule, and the program will propose examples and try to guess the rule!

The secret solution! (3 minutes): the program maintains a probability distribution over hypotheses, and generates random examples that are designed to falsify half of its remaining hypotheses. (In the language of information theory, this corresponds to how the answer to a Yes-or-No question is one information-theoretic bit—hence the talk title.) I used Rust, whose type system actually made this pretty awkward to implement compared to dynamic languages, but I needed the speed.

Live demo! (4 minutes): ask audience members to supply a hypothesis, and show how the program generates examples to narrow it down! "Can someone give me a color, chosen from red, green, blue, and yellow?" (Suppose someone says "Yellow.") "And can someone give me a number, 1, 2, or 3?" (Suppose someone says, "Two.") "Okay, our rule is, 'exactly two yellow triangles'." Run the program: it shows ASCII-art triangles of various sizes in the terminal, and I type 'y' when exactly two of them are yellow, and 'n' otherwise. Before too long (if I recall, it tends to take around 10 examples/questions?—compare to the standard party game, "20 Questions"), the program will say, "This program infers that a study has the property if and only if it has two yellow triangles." Amazing!—it read our minds!

> Background knowledge? \*

Passing familiarity with probability and information theory is helpful but not required
