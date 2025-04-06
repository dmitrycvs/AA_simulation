# Optimized Strategy for Iterated Prisoner's Dilemma

This repository contains an optimized strategy for the Iterated Prisoner's Dilemma tournament, designed to maximize points by strategically exploiting opponent behaviors while maintaining tactical cooperation when advantageous.

## Strategy Overview

Based on analysis of previous test results, this updated strategy adopts a more aggressive approach to ensure victory. It is designed to exploit predictable opponent behaviors and punish defections while maintaining a calculated level of cooperation to avoid mutual defection spirals.

### Part 1: Core Strategy (`strategy` function)

The strategy works by balancing aggression and cooperation, focusing on exploiting opponent patterns and responding to defections. The algorithm follows these core principles:

1. **Dominance Establishment**: Starts with defection if no prior history exists, asserting control over the game.
2. **Pattern Recognition**: Identifies predictable opponent behavior and exploits it for future moves.
3. **Tactical Cooperation**: Cooperates only when it maximizes long-term advantage or counters a specific pattern.
4. **Punishment Mechanism**: Defects harshly in response to opponent defections, especially after a series of defections.
5. **End-game Exploitation**: Defects in the final rounds to maximize individual payoff, when the end of the game is known.

Key Features:
- Defaults to cooperation unless there’s evidence that defection is beneficial.
- Implements pattern recognition to predict and exploit opponent moves.
- Detects opponent’s tendency to defect (if over 20% of their moves are defections) and responds accordingly.
- Establishes dominance through initial defections, maintaining an aggressive stance throughout the match.

### Part 2: Opponent Behavior Exploitation

The strategy includes methods for assessing and exploiting opponents in the following ways:

1. **Pattern Recognition**: Identifies recurring sequences in the opponent’s history and predicts their next move.
2. **Defection Rate Calculation**: Calculates the rate of defections in the opponent's history to determine the likelihood of further defections.
3. **End-Game Strategy**: Adjusts behavior for the final rounds to maximize defection when beneficial.
4. **Punishment for Repeated Defections**: Increases the likelihood of defection if the opponent defects multiple times in succession.

### Performance Analysis

The previous strategy was too passive, often cooperating too early and forgiving opponent defections. The revised strategy incorporates the following improvements:

- **First-move defection** to assert dominance, rather than cooperating immediately.
- **Default defection bias** (around 60-70%) to discourage opponents from exploiting cooperation.
- **Punishment of defection** after a series of defections, with harsher responses if an opponent consistently defects.
- **Pattern recognition** to create beneficial cycles with tit-for-tat or alternating strategies.
- **Strategic exploitation** of cooperative players, while minimizing interaction with uncooperative ones.

This updated strategy ensures a balance between short-term exploitation and long-term strategic cooperation, crucial for a successful tournament outcome.

## Implementation Notes

This strategy is robust against various opponent types:
- **Naive cooperators**: Exploited with a consistent defection rate.
- **Tit-for-tat players**: Engaged in cooperative cycles to maximize mutual benefit.
- **Random players**: Defected against consistently to avoid giving them points.
- **Other adaptive strategies**: The strategy adapts by recognizing and exploiting predictable behavior patterns.

### Code Explanation

The core of the strategy is in the `strategy` function, which takes the following parameters:
- `my_history`: A list of the player's previous moves.
- `opponent_history`: A list of the opponent’s previous moves.
- `rounds`: The total number of rounds remaining in the game.

#### Key Components of the `strategy` Function:
1. **First Move Defection**: If there is no previous history, the strategy defects on the first round.
2. **Pattern Recognition**: Looks for repeating patterns in the opponent’s history and predicts their next move.
3. **Punishment Mechanism**: Defects if the opponent has defected multiple times, especially in the last few rounds.
4. **Defection Rate Calculation**: If the opponent has defected more than 20% of the time, the strategy defaults to defection to minimize risk.
5. **Endgame Strategy**: Defects in the final rounds to maximize points.

## Conclusion

This optimized strategy is designed to exploit predictable behaviors, punish defections, and maintain a calculated level of cooperation when beneficial. It provides a robust solution to the Iterated Prisoner's Dilemma, ensuring a competitive edge in the tournament.