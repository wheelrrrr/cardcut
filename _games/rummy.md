---
layout: default
title: Rummy
resource: true
categories: [games]
aim: Target score reached. Typically 500. Score points by 'going out'.
deal: 10 (2x), 7 (3-4) or 6 (5-6)
players: 2 - 6
rank: High ( K, Q, J ... 3, 2, A ) Low
category: Uncategorised
actions:
- type: root
  title: Hand
  actions:
  - text: Random dealer. 10 (<strong>2x</strong><i class='fas fa-user'></i>), 7 (<strong>3-4</strong><i
      class='fas fa-user'></i>) or 6 (<strong>5-6</strong><i class='fas fa-user'></i>)
      cards each.
    type: deal
    title: Deal
    actions:
    - text: 1 card face up as discard pile.
      type: deal2
      title: Discard Pile
    - text: Remaining cards form face down as stock.
      type: deal2
      title: Stock Pile
  - text: ''
    type: play2
    title: Each Player
    actions:
    - text: 1 from Stock <em>OR</em> Discard. If the stock runs out, shuffle and reuse.
      type: play3
      title: Draw
    - text: A single group of 3+ cards (Meld) face-up in front of player.
      type: play3
      title: Play
      prefix: Opt.
      reference:
        items:
        - Sequence = e.g. [♣5-♣6-♣7]
        - Set = e.g. [♦7-♣7-♠7]
        title: Meld Reference
    - text: Lay Off any cards to any existing melds on table.
      type: play3
      title: Play
      prefix: Opt.
    - text: 1 card from hand face-up on Discard.
      type: play3
      title: Discard
    subtitle: Until first player to empty hand
  - text: A player has won by playing all cards. Declare 'Rummy!'
    type: flow
    title: End of Hand
  - text: Round winner scores total from remaining players cards.
    type: score
    title: Score
    reference:
      items:
      - Face (K, Q, J) = 10pts each
      - Ace = 1pt
      - Number card = that amount
      - e.g. 3 = 3pt
      - e.g. 7 = 7pt
      title: Scoring Reference
  - text: Clockwise.
    type: flow
    title: Next Hand
  - text: When a player reaches target score.
    type: end
    title: Game End
  subtitle: Repeat until a player reaches target score.

---

{%- include rules.html -%}
