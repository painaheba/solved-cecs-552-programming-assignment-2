Download Link: https://assignmentchef.com/product/solved-cecs-552-programming-assignment-2
<br>
<h1>Monte Carlo Simulation for Playing Blackjack</h1>

A simple version of the (two-player) game of Blackjack is described as follows. For this version we use four special decks of cards in which each deck, in addition to its usual cards, has an additional four cards, each with a numerical value equal to 1. The four decks of cards are randomly shuffled together to make a <strong>dealing deck </strong>of 56 × 4 = 224 cards total. The value of a number card equals the card number, the value of a face card equals 10, while the value of an ace equals 11 (aces no longer can equal 1, since we’ve added the 1 cards). In what follows we let random variable <em>X </em>represent the result of drawing a card at random from the (entire) dealing deck. For example, <em>P</em>(<em>X </em>= <em>i</em>) = 16<em>/</em>224 = 1<em>/</em>14, for all <em>i </em>= 1<em>,…,</em>9<em>,</em>11}, while <em>P</em>(<em>X </em>= 10) = 64<em>/</em>224 = 2<em>/</em>7.

Each player is first dealt a card facing downward that is hidden from her opponent. Players are then alternately dealt cards facing upward that are visible to the opponent. Before a card is dealt to a player, she has the option of <strong>holding</strong>, meaning that she is not dealt any further cards. If she does not hold, then she <strong>hits</strong>, meaning that she is dealt an additional card. Play ends when one of the following has occurred:

<ol>

 <li>a player hits, and the card dealt to her results in a sum (of the values of all her cards) equal to 21, in which case she immediately wins the game;</li>

 <li>a player hits, and the card dealt to her results in a sum that exceeds 21, in which case she immediately loses the game; or</li>

 <li>both players have decided to hold, in which case the winner is the player whose card values have the highest sum (a tie occurs if the sums are equal).</li>

</ol>

When a game ends, all dealt cards are revealed to both players, and the cards are placed in the <strong>used pile</strong>, and are never dealt again during the <strong>match</strong>, which is a sequence of games that ends once the

1

dealing deck is exhausted (if this happens during a game, then the game ends in a tie). Note that, during a match, the players take turns at being dealt the first card.

Now consider the following strategy that can be used by a player in order to decide on whether to hit or hold on a given turn. In this strategy, player <em>P </em>hits provided one of the following is true. Let <em>S </em>denote the sum of <em>P</em>’s cards.

<ol>

 <li><em>P</em>’s opponent has not yet decided to hold, and <em>P</em>(<em>X </em>+ <em>S </em>≤ 21) <em>&gt; p</em><sub>1</sub>, where <em>p</em><sub>1 </sub>≥ 0<em>.</em>5 is some threshold value that is provided as input by the user. Here <em>X </em>represents the value of the next card that will be dealt if <em>P </em>decides to hit. The reasoning is that <em>P </em>hits provided there is sufficient probability that the next card dealt will not bring her sum over 21.</li>

 <li><em>P</em>’s opponent has already decided to hold, and <em>E</em>[<em>X</em>|<em>X </em>+<em>S<sub>v </sub>&lt; </em>21]+<em>S<sub>v </sub>&gt; S</em>. Here, <em>X </em>represents the opponent’s hidden card. In words, <em>P </em>calculates the expected value of the hidden card, on condition that, when adding it to the visitble sum, it must give a value that is less than 21. Then, if this expected value is added to the visible sum, and it exceeds <em>S</em>, then <em>P </em>hits because she believes that her opponent has held with a better hand.</li>

 <li><em>P</em>’s opponent has already decided to hold, and <em>P</em>(<em>X </em>+ <em>S </em>≤ 21) ≥ <em>p</em><sub>2</sub>, where <em>p</em><sub>2 </sub>≥ 0<em>.</em>5 is a threshold value provided as input by the user. In this case, <em>P </em>hits because she has a good chance of not going over 21. Of course, how “good” depends on the value of <em>p</em><sub>2</sub>.</li>

</ol>

<h1>Program Options</h1>

<ol>

 <li>The user inputs a value <em>S</em>, and the program returns <em>P</em>(<em>X </em>+ <em>S </em>≤ 21).</li>

 <li>The user inputs a value <em>S<sub>v</sub></em>, and the program returns <em>E</em>[<em>X</em>|<em>X </em>+ <em>S<sub>v </sub>&lt; </em>21].</li>

 <li>The user inputs a value <em>M</em>, that represents the number of matches to be played between two players. Then the user inputs a (<em>p</em><sub>1</sub><em>,p</em><sub>2</sub>) pair for each of the players. The program simulate <em>M </em>matches between these two players and reports on the followng: i) the number of games won by each player over all the matches, and ii) a 90% confidence intervals for each player that captures her probability of winning against her opponent.</li>

 <li>Repeat the previous option, but now, for each player, indicate if the player is either assuming <em>X </em>is sampled over the original deck, or if <em>X </em>is being sampled over the <em>remaining </em> In other words, in addition to <em>p</em><sub>1 </sub>and <em>p</em><sub>2 </sub>indicate whether or not the player is “card counting”, meaning she is memorizing the cards that have already been played.</li>

</ol>

2