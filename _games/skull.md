---
layout: default
title: Skull
resource: true
categories: [games]
aim: Winner is the first to 2 points or the last left in the game after all others
  are eliminated.
deal: 1 Spade and 3 Hearts to each player
players: 3 - 8
rank: Spades are Skulls, Hearts are Roses
category: Uncategorised
actions:
- text: 'Random dealer: 3 Hearts and 1 Spade to each player.'
  type: deal
  title: Deal
- text: ''
  type: play
  title: Start Round
  actions:
  - text: ''
    type: play2
    title: Each Player
    actions:
    - text: From hand of cards select either Spade (Skull) or Heart (Rose) Face down.
      type: play3
      title: Play
- text: Starting with Lead Player (determined by previous round)
  type: bidding
  title: Placement Phase
  actions:
  - text: ''
    type: bidding2
    title: Each Player
    actions:
    - text: Lay another card down.
      type: bidding3
      title: Play
      prefix: Do
    - text: Start Challenge Phase (no further cards can be played).
      type: bidding3
      title: Make Bid
      prefix: Else
- text: 'Bid: say how many Hearts (Roses) you can turn over.'
  type: bidding
  title: Challenge Phase
  actions:
  - text: Clockwise from initial bidder
    type: bidding2
    title: Each Player
    actions:
    - text: Player may Raise Bid.
      type: bidding3
      title: Raise Bid
      prefix: Do
    - text: Player is out of this Hand.
      type: bidding3
      title: Pass
      prefix: Else
    subtitle: Until all players have passed
  - text: When all players have passed, Start Revelation Phase (no more bids can be
      made).
    type: bidding2
    title: Until
- text: Highest bidder attempts to make Bid by revealing cards.
  type: play
  title: Revelation Phase
  actions:
  - text: Player must always turn over own cards first.
    type: play2
    title: Reveal Own Cards
    actions:
    - text: Player has Lost Hand.
      type: play2
      title: Skull
      prefix: If
    - text: One at a time reveal the top cards of other players.
      type: play2
      title: Reveal Other Cards
      prefix: Else
      actions:
      - text: Stop if you reveal a Skull.
        type: play3
        title: Skull
        prefix: If
      - text: Continue if you reveal a Rose
        type: play3
        title: Rose
        prefix: Else
      subtitle: Until bid is made.
  - text: Player Scores 1 Point.
    type: play2
    title: Bid Success
    prefix: If
    subtitle: No Skulls
  - text: Lose 1 Card. Player of revealed Skull picks from shuffled set face down.
      If Player revealed own Skull, they may select a card. Discarded cards go in
      front of player and remain hidden.
    type: play2
    title: Bid Failure
    prefix: Else
    subtitle: Skull Revealed
- text: Highest bidder leads next hand whether they won or lost.
  type: flow
  title: Player In
  prefix: If
  subtitle: Has cards remaining
- text: Bid Winner is out of the game, the Player of the revealed Skull leads.
  type: flow
  title: Player Out
  prefix: Else
  subtitle: No cards left
- text: Furst player to score 2 points or the last remaining player is the winner.
  type: end
  title: Game End

---

{%- include rules.html -%}
