---
layout: post
title: On deck combinations and probabilities of drawing cards
subtitle: Or how can I compute the probability of drawing any number of cards from any number of specific sets of cards on the first hand.
cover-img: 
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

$$\text{Probability of an event}=\frac{\text{number of favourable outcomes}}{\text{total number of outcomes}}$$

Now to apply this idea in our case, if we want to compute the probability of drawing the king of hearts we can count the number of successes (number of cards that can make the event happen, in this case only the king of hearts) and the number of possible outcomes (the total number of cards in the deck):

$$\text{Probability of drawing the king of hearts} = \frac{\text{\# of king of hearts}}{\text{total \# of cards}} = \frac{1}{52} = 0.019 = 1.9\%$$

Now we may ask ourselves what is the probability of drawing the king of hearts when drawing a hand of 5 cards?

![King_hearts_in_hand.jpg](https://i.imgur.com/YWK4uiY.jpg)

For each time we draw a card we may expect the same probability of drawing the king of hearts, i.e. 1.9%.

## Hypergeometric probability mass function

$$P() = \frac{\binom{K}{k} \binom{N-K}{s-k}}{\binom{N}{s}}$$
