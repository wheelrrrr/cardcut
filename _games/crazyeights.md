---
layout: default
title: Crazy Eights
resource: true
categories: [games]
aim: 'First to score: 2 = 100, 3 = 150, 4 = 200, 5 = 250, 6 = 300, 7 = 350'
deal: 7 (2x) or 5 (3+)
players: 2 - 7
rank: High ( 8, A, K, Q ... 4, 3, 2 ) Low
category: Matching Game
actions:
- type: root
  title: Hand
  actions:
  - text: Random dealer. 7 (<strong>2x</strong><i class='fas fa-user'></i>) or 5 (<strong>3+</strong><i
      class='fas fa-user'></i>) cards each.
    type: deal
    title: Deal
    actions:
    - text: Remaining cards form face down Stock pile.
      type: deal2
      title: Stock Pile
    - text: Top card from Stock to start Discard
      type: deal2
      title: Discard Pile
  - text: Any card matching Rank or Suit of card on Discard.
    type: play
    title: Each Player
    actions:
    - text: Play any card matching Rank or Suit of card on Discard.
      type: play2
      title: Follow Rank or Suit
      prefix: Do
      subtitle: Or play special card.
      reference:
        items:
        - 8 = Play on any card. Nominate new suit.
        - 2 = Next player draw two cards or play a two (effect is cumulative i.e.
          next player draw 4)
        - 4 = Reverse direction
        - J = Skip next player
        title: Special Cards
    - text: Draw from Stock.
      type: play2
      title: Pass
      prefix: Else
    subtitle: Until first player to empty hand
  - text: Player empties hand to win.
    type: play
    title: Winner
  - text: Winner scores from cards left in other player's hands.
    type: score
    title: Score
    reference:
      items:
      - 8 = 50pts
      - Face (K, Q, J) = 10pts each
      - Ace = 1pt
      - Number card = that amount
      - e.g. 3 = 3pt, 7 = 7pt etc.
      title: Scoring Reference
  - text: When all scoring completed.
    type: flow
    title: Next Hand
  subtitle: Repeat until first player to reach target
- text: When player hits required score.
  type: end
  title: Game End
scoring:
- 8 = 50pts
- Face (K, Q, J) = 10pts each
- Ace = 1pt
- Number card = that amount
- e.g. 3 = 3pt
- e.g. 7 = 7pt
---

{%- include rules.html -%}
