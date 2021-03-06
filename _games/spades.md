---
layout: default
title: Spades
resource: true
categories: [games]
aim: First partnership to 500 points
deal: '13'
players: '4'
rank: High ( A, K, Q ... 4, 3, 2 ) Low
category: Trick Taking Game
actions:
- type: root
  title: Hand
  actions:
  - text: Random dealer. 13 cards each.
    type: deal
    title: Deal
  - type: bidding
    title: Bidding
    actions:
    - text: Left of dealer.
      type: bidding2
      title: Each Player
      actions:
      - text: Look at cards, bid number of tricks to win.
        type: bidding3
        title: Bid
      - text: 'Player may bid Nil to win no tricks. Success: win 100pts. Failure:
          lose 100pts.'
        type: bidding3
        title: Nil
    - text: Record combined bids for each partnership.
      type: bidding2
      title: End of Bidding
  - text: Left of dealer leads. Lead any suit but not spades until a spade has been
      played (broken).
    type: play
    title: Play
    actions:
    - text: ''
      type: play2
      title: Trick
      actions:
      - text: ''
        type: play3
        title: Each Player
        actions:
        - text: Play card following suit if possible.
          type: play4
          title: Follow Suit
          prefix: Do
        - text: Including Spades ♠.
          type: play4
          title: Play any suit
          prefix: Else
        subtitle: Until all players have played
      - text: Trick won by (a) highest Spade. Otherwise (b) highest rank of lead suit.
        type: play3
        title: Winner
      - text: Winner leads next trick.
        type: play3
        title: Next
      subtitle: Repeat until all cards have been played
  - text: Each Partnership
    type: score
    title: Score
    actions:
    - text: If partnership Bid success, each trick 10pts.
      type: score2
      title: Bid Success
    - text: Each trick over Bid 1pt and added to Sandbags tally.
      type: score2
      title: Overbids
    - text: If partnership Bid failure, each trick negative 10pts.
      type: score2
      title: Bid Failure
    - text: If partnership Sandbags tally reaches 10, lose 100pts. Multiple Sandbags
        penalties may be scored.
      type: score2
      title: Sandbag Penalty
    reference:
      items:
      - Each Trick (success) = 10pts
      - Each Trick (fail) = -10pts
      - Each Overbid trick = 1pt
      - Sandbag penalty = -100pts per 10 bags
      title: Scoring Reference
  - text: When all cards played.
    type: flow
    title: End of Hand
  subtitle: Repeat until a partnership reaches 500pts
- text: When partnership reaches 500.
  type: end
  title: Game End

---

{%- include rules.html -%}
