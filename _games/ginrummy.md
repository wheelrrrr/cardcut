---
layout: default
title: Gin Rummy
resource: true
categories: [games]
aim: Target score reached. Typically 100
deal: '10'
players: '2'
rank: High ( K, Q, J ... 3, 2, A ) Low
category: Draw and Discard Game
actions:
- text: After deal non-dealer can take from Discard. Refusal means dealer can take
    the card and begin. If neither take it, non-dealer begins as normal.
  type: root
  title: Hand
  actions:
  - text: Random dealer. 10 cards each.
    type: deal
    title: Deal
    actions:
    - text: 1 card face up as discard pile.
      type: deal2
      title: Discard
    - text: Remaining cards form face down as stock.
      type: deal2
      title: Stock
  - text: ''
    type: play
    title: Each Player
    actions:
    - text: 1 from Stock <em>OR</em> Discard. If the stock runs out, shuffle and reuse.
      type: play2
      title: Draw
    - text: 1 card from hand face-up on Discard.
      type: play2
      title: Discard
    - text: If player doesn't Knock, play continues.
      type: play2
      title: End of turn
    subtitle: Until a player knocks
  - text: Player may Knock to end round if conditions are met. Player lays all cards
      face up.
    type: flow
    title: End of Hand
    actions:
    - text: All cards in hand are in either a Set or Run ('Melds'). Declare 'Gin'.
      type: flow
      title: Gin
      prefix: If
    - text: Cards in hand are in Melds and surplus cards ('Deadwood') not in any meld
        add up to 10 points or less
      type: flow
      title: Deadwood
      prefix: Else
  - text: Defending player lays out Melds. Defender can Lay-off any cards to the Melds
      of the Knocker.
    type: flow
    title: No Gin
    prefix: If
  - text: ''
    type: score
    title: Score
    actions:
    - text: Knocker gets 25 points plus Deadwood score from Defender.
      type: score2
      title: Gin
      prefix: If
    - text: Knocker subtracts Deadwood points from the Defender Deadwood points. Results
        is score for Knocker. If it is less than 0, points go to Defender plus 25
        points Undercut bonus.
      type: score2
      title: No Gin
      prefix: Else
    reference:
      items:
      - key: Face (K, Q, J) =
        value: "= 10pts each"
      - key: Ace
        value: "= 1pt"
      - key: Number card
        value: "= that amount"
      - e.g. 3 = 3pt, 7 = 7pt etc.
      title: Scoring Reference
  - text: When all scoring completed.
    type: flow
    title: Next Hand
- text: When a player reaches target score.
  type: end
  title: Game End

---

{%- include rules.html -%}
