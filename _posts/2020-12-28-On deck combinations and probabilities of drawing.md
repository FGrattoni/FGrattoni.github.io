---
layout: post
title: On deck combinations and probabilities of drawing cards
subtitle: Or how can I compute the probability of drawing any number of cards from any number of specific sets of cards on the first hand.
cover-img: https://i.imgur.com/MOkExEX.png
thumbnail-img:
share-img: 
tags: [probability]
---

Table top games are a wonderland of maths and probability, much more than one may be willing to think about when trying to seek pleasure, maybe even disconnect the mind with a simple game. Card games, in this, are no exception.

It's practical use, its easy application in everyday life and its approachable and familiar theme made card games one of the most used examples appearing in any probability book.

> What is the probability of drawing the king of hearts from a fairly shuffled deck of 52 cards?

> What is the probability to draw any figure but the spades ones, from a fairly shuffled deck?

These kind of [problems](https://www.math-only-math.com/playing-cards-probability.html) build on a single assumption that is needed to solve them: the deck is well shuffled, meaning that any card has the exact same probability of being drawn than any other card left in the deck. There is no previous order imposed on the cards.

## Number of different combination of decks

This is all the information we need to compute how many different, well shuffled, deck combination may exist. In fact, for any deck, the first card can be any of the 52 existing cards. Then the second card of the deck can be any of the remaining 51 cards. The third any of the remaining 50, and so on, up until the last card, which remains the unique card left. This leaves us with this formula to compute the number of different deck combinations:

$$\begin{aligned} 
\text{\# of deck combinations} &= 52 \cdot 51 \cdot 50 \cdot \dots \cdot 1 \\ &= 52! \\ &= 8,07 \cdot 10^{67} 
\end{aligned}$$

This is a number extremely large. One almost impossible to conceive for us. To give an idea of the scale of this number we can take inspiration from a number that has seen many [attempts of estimation](https://skeptics.stackexchange.com/questions/9059/more-stars-than-grains-of-sand): the number of grains of sand present on earth. The most conservative number that has been estimated is $10^{24}$ grains of sand that are present of earth. You may find yourself in struggle when trying to visualize how many these are. It may even be difficult to visualize the number of grains of sand on a single beach, let alone the entire earth. But this number is incredibly far from the number of different deck combinations. Now, try to imagine for a moment that any single grain of sand is an entire world, identical to the Earth, with the exact same number of beaches, deserts and, ultimately, grains of sand. This would surely grant us a number of grains of sand that exceeds the number of combinations of single deck, composed by just 52 cards, right? Wrong, because even  if it may be difficult to imagine, this scenario would give use a number that is not even close to the different combinations, namely: $(10^{24})^2 = 10^{48}$ grains of sand. Not even close. In fact, the number of different combination of shuffled decks is so large that if you shuffle a normal deck of cards properly, now, you most likely are going to see in front of your eyes a combination of cards that no eye has ever seen before or will ever do.. Pretty incredible, right? Or is it? Not really, since this is something that would happen to anyone trying. It just sounds cool, a nice little fun fact. 

However, this was just a little, fun, digression from what the goal of the article is.

## Investigating probabilities of drawing cards

If we want to compute the probability of drawing cards it will be useful to introduce a simple trick to compute probability, which comes from one of the existing definitions of probability. It builds upon the idea that we can compute the probability of an event by simply count the different outcomes that we define as successful, and compare it to the number of all possible outcomes: 

$$\text{Probability of an event}= \frac{\text{\# favourable outcomes}}{\text{\# total outcomes}}$$

Now to apply this idea in our case, if we want to compute the probability of drawing the king of hearts we can count the number of successes (number of cards that can make the event happen, in this case only the king of hearts) and the number of possible outcomes (the total number of cards in the deck):

$$
\begin{aligned}
  P(\text{King of hearts}) & = \frac{\text{\# of king of hearts}}{\text{total \# of cards}} \\ & = \frac{1}{52} = 0.019 = 1.9\%
\end{aligned}
$$

Now we may ask ourselves what is the probability of drawing the king of hearts when drawing a hand of 5 cards?

![King_hearts_in_hand.jpg](https://i.imgur.com/ENBgXxW.jpg)

For each time we draw a card we may expect the same probability of drawing the king of hearts, i.e. 1.9%.


## The binomial function
Now, to move on with the article, a very useful function needs to be introduced: the **binomial function**.

$$ \binom{a}{b} = \frac{a!}{(a-b)!\ b!} $$

Apart from the formula, what matters even more is the intuition behind the number that this formula will help us calculate. Perhaps, the other way in which we can read this formula, can help us introduce its interpretation. We can read the binomial coefficient as _a chooses b_. In other words, this coefficient computes the **number of ways we can pick** _b_ **cards** (without considering their order) **out of** _a_ **total cards**.

We can make a numerical example to show how this works. Let's say we want to compute the number of different ways we can pick 2 cards out of 3 total cards. We want to compute _3 chooses 2_:

$$ \binom{3}{2} = \frac{3!}{(3-2)!\ 2!} = \frac{3\cdot2\cdot1}{1\cdot2\cdot1} = 3$$

Graphically:

![Graphical rapresentation of Binomial Coefficient](https://i.imgur.com/CB2Bi5T.jpeg)

This can help us determine how many possible different hands of cards we can be dealt. This will be useful because will represent the denominator of our formula when computing the probability of succesful hands. It represents the total amount of possible outcomes as used in the previous formula. It will also be a key component when calculating the number of success cases. The next section will make use of this formula, making the next steps towards answering our question. 

## Hypergeometric distribution

We now have all the tools we needed to compute and understanf the probability of drawing a specific number of cards from a set of cards. 

We make use of the **Hypergeometric Distribution** to compute the probability of the event X, i.e. drawing exactly $k$ cards out of $K$ possible, from adeck composed of $N$ cards, when drawing a total of $s$ cards. Such probability is computed as follows:

$$P(X_k) = \frac{\binom{K}{k} \binom{N-K}{s-k}}{\binom{N}{s}}$$

Let us consider an example. We want to consider the probability of drawing exactly two aces when drawing 5 cards from a standard, well-shuffled, 52 cards deck. In this specific example we are computing the probability of drawing $k=2$ aces from a total of $K=4$ that are present in the deck. We will draw $s=5$ cards from a deck composed by $N=52$ cards. 

$$
    P(X_2) =
    \frac{\binom{4}{2} \binom{52-4}{5-2}}{\binom{52}{5}}
   = 0.04 
   = 4\%
$$

Now we have a formula and a way to answer many possible questions. However, let's develop a more intuitive understanding of the formula.

The above formula should remind you of the method to compute probability showcased earlier:

$$ P(\text{event}) = \frac{\text{\# favourable outcomes}}{\text{\# total outcomes}}$$

Starting the analysis from the denominator, which is much simpler, it determines how many different combinations, of a hand of 5 out of 52 cards, are possible.

The numerator, on the other hand, computes the number of favourable outcomes. The number of different possible combination, provided that two aces are drawn. 

Graphically: 

![Hypergeometric formula visualized](https://i.imgur.com/Ev3XzPu.png)
As seen in the figure, we first "reserve" two spots, out of the total 5, for the aces. And to do so we compute the nuber of combinations in which this could happen. Then we compute the number of ways in which we can pick the remaining 3 cards. We multiply the two numbers and then we divide it by the total number of combinations possible. This will give us the probability of the event actually happening as a result. 

## Moving our analysis to more than one set of interest
Now the question becomes, what if we want to compute the probability of drawing cards, similarly to the one in the previous section, but with a small difference. The cards we want draw belong to different set of cards. Let's say we want to compute the probability of drawing two aces (as before), but they need to be of different colors. We may transform the question to being: 

> What is the probability that, when drawing 5 cards from a standard, well-shuffled, deck of 52 cards, we are drawing both one red and one black ace?

And now we can clearly see how two different sets of _cards of interest_ are formed. We can modify our model to accomodate this change. $N$ will remain the total number of cards in the deck and $s$ the total number of cards drawn. But now we need to differentiate te cards of interest: $K_1$ will be the number of cards that represent a success from the first set, and $k_1$ the number of cards drawn from that set. Now we will have a second set, composed by $K_2$ cards from which we will draw $k_2$ cards. 

The way we will compute the number of favorable combination (in the nominator of the probability formula) will be changed, taking into account the new requirements: 

$$ 
P(X_{(k_1,k_2)}) = \frac
{\binom{K_1}{k_1} \binom{K_2}{k_2} \binom{N-K_1-K_2}{s-k_1-k_2}}
{\binom{N}{s}}
$$ 

As you can see we add a new component to the numerator to accomodate to the different set of combination that this new restriction sets. From the example discussed at the beginning of the section:

$$
P(X_{(k_1=1, k_2=1)}) = 
\frac
{\binom{2}{1} \binom{2}{1} \binom{52-2-2}{5-1-1}}
{\binom{52}{5}}
= 0.027 = 2.7\%
$$

As you can see the probability of the event happening is lower than the one without the restriction, hence I have been calling it a **restriction**.


## The general case
By induction we can derive the general formula:

$$
\begin{aligned}
P(X_{k_1,\dots, k_t}) & = 
\frac{\binom{K_1}{k_1} \dots \binom{K_i}{k_t} \binom{N-K_1-\ldots-K_t}{s-k_1-\ldots-k_t}}
{\binom{N}{s}}\\
 & = \frac{
        \prod_{i=1}^{t} \binom{K_i}{k_i} \cdot
        \binom{N - \sum_{i=1}^{t}(K_i)} {s - \sum_{i=1}^{t}(k_i)} }
 {\binom{N}{s}}
\end{aligned}
$$

where $ K_1, \dots, K_t $ are the different _sets of interest_, $k_1, \dots, k_t$ are the number of cards that we have to draw from the deck, $N$ and $s$ are, as usual, the number of cards in the deck and the number of cards drawn.

The two formulas are just two ways, using a different notation, to write exactly the same thing.

