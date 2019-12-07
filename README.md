A demonstration of the thesis stated in [this post](https://word.site/2019/11/12/dynamic-pow/):

```
Proof-of-work consensus works without a target inter-block time, difficulty, or even a timestamp.

This is called ‘continuous’ or ‘dynamic’ POW.

The key security property remains the same: Barring a 51% attack, the probability that a transaction which has been confirmed gets un-confirmed (or reorganized) drops exponentially with time.

A regular (light) client still works the same way. It chooses the chain with the most cumulative work.

Miners play a betting game with their hash power remniscient of CASPER proof-of-stake.

A timestamp is only necessary when there is a fee subsidy, which should be a function of time, not block height.
```

Concretely:

* Nodes reject blocks whose work is not at least 2/3rd as difficult as prior block
* * (The numeric value of the proof-of-work data must be less than or equal to 3/2 times previous POW)
* If there is a block subsidy, it is a function of time and timestamp is needed in header
* * If timestamps are needed, nodes reject blocks that are in the future

That's it. There is no need for a target inter-block time, target difficulty, or difficulty adjustment period. There is no need to track block height either.

Indexing by block height is using the wrong mental model for nodes/miners trying to create blocks, and makes it difficult to handle high frequency reorgs at the head of the chain.

Instead use an immutable data structure to track header -> state (including cumulative work), and apply changes to the header with the most work. There is no concept of "most recent" or "highest" block.

Ethereum uses a purely functional data structure for most state which makes maintaining consensus simple, but it is primarily designed for proving app logic state "in-chain", not a structure optimized for quickly processing many candidate branches near the head.
