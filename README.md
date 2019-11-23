A demonstration of the thesis stated in [this post](https://word.site/2019/11/12/dynamic-pow/):

```
Proof-of-work consensus works without a target inter-block time, difficulty, or even a timestamp.

This is called ‘continuous’ or ‘dynamic’ POW.

The key security property remains the same: Barring a 51% attack, the probability that a transaction which has been confirmed gets un-confirmed (or reorganized) drops exponentially with time.

A regular (light) client still works the same way. It chooses the chain with the most cumulative work.

Miners play a betting game with their hash power remniscient of CASPER proof-of-stake.

A timestamp is only necessary when there is a fee subsidy, which should be a function of time, not block height.
```
