---
layout: default
title: Shithead
resource: true
categories: [games]
aim: Avoid being the last player left at the end.
deal: 
players: 
rank: 
category: Uncategorised
actions:
- title: Dealing
  actions:
  - text: 'Random dealer: Row of 3 Face down cards to each player.'
    type: start
    title: Deal
  - text: Row of 3 Face up cards to each player (on top of face down cards).
    type: start
    title: Deal
  - text: Hand of 3 cards face down to each player.
    type: start
    title: Deal
  - text: Remaining cards form face down Draw pile.
    type: start
    title: Draw Pile
  - text: Players can swap any cards in hand for face up cards.
    type: start
    title: Swap
- text: First player with face up 3, or 3 in hand, or 4 etc.
  type: start
  title: Start Hand
  actions:
  - text: ''
    type: start
    title: Each Player
    actions:
    - text: Must always equal or beat value of previous card on Discard.
      type: turn
      title: Play
    - text: Play 1x card face up on Discard. Or 2 or more of same value [♣7-♠7].
      type: turn
      title: If cards in hand
    - text: Play face up card.
      type: turn
      title: If empty hand
    - text: Turn face-down card and play blind.
      type: turn
      title: If empty hand and no face-up cards
    - text: Pick up Discard pile
      type: turn
      title: Otherwise, Pass
    - text: Replenish hand from Draw. Should have minimum of 3 cards.
      type: turn
      title: Replenish
    - text: Clockwise.
      type: flow
      title: Next Player
  - text: 2 = Can play on any card. Any card can be played on top of it.<br/>10
      = Play on any card, clear and shuffle Discard and same player plays again.<br/>Completing
      any Set of 4x e.g. [♥7-♦7-♣7-♠7] = Clear and shuffle Discard and same player
      plays again.
    type: condition
    title: Special Cards
  - text: When a player empties hand and table cards, they drop out.
    type: condition
    title: Drop Out
- text: Last player left is the Shithead.
  type: end
  title: End of Game
---

{%- include rules.html -%}
