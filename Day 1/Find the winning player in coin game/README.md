## Problem

You are given two positive integers `x` and `y`, denoting the number of coins with values `75` and `10` respectively. Alice and Bob are playing a game where each player must pick coins totaling `115` on their turn. The game starts with Alice. If a player is unable to make the required total, they lose the game. Determine the name of the player who will win if both players play optimally.

For more details on similar problems, you might explore the [LeetCode Problem Link](https://leetcode.com/problems/find-the-winning-player-in-coin-game/description/?envType=problem-list-v2&envId=game-theory).

## Explanation

The game involves both players trying to optimally pick coins to form a total of `115`. The strategy revolves around checking if it’s possible to continue picking coins with the available amounts. The code provided attempts to simulate this process to determine the winner.

### Approach

1. **Initialization:**
   - Begin with `n` initialized to `0` to keep track of the number of successful turns where a total of `115` was picked.

2. **Game Simulation:**
   - While there are coins available (`x > 0`) and enough coins of value `10` to make up `115` (`y > 3`):
     - A successful turn is executed by decrementing `x` by `1` and `y` by `4` (since the turn involves picking coins totaling `115`, and the optimal combination uses `1` coin of `75` and `4` coins of `10`).
     - Increment the turn counter `n`.

3. **Determine the Winner:**
   - If the total number of successful turns (`n`) is even, Alice will lose, and Bob will win (since Alice makes the first move).
   - If `n` is odd, Alice will win.

### Code

```cpp
        while (x > 0 && y > 3) {
            n++;
            x = x - 1;
            y = y - 4;
        }
        if (n % 2 == 0) {
            return "Bob";
        }
        return "Alice";
```

- **Time Complexity:** O(min(x, y))
- **Space Complexity:** O(1)
