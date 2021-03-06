---
layout: default
title: Big 2
resource: true
categories: [games]
aim: Game ends when a player reaches an agreed points total or time.
deal: '13'
players: '4'
rank: '2, A, K, Q, J, 10…3; Suits: ♠ ♥ ♣ ♦'
category: Climbing Game
actions:
- type: root
  title: Hand
  actions:
  - text: Random dealer. 13 cards each.
    type: deal
    title: Deal
    actions:
    - text: Player with 3♦ leads by playing it in any legal cominbation.
      type: deal2
      title: Starting Player
  - text: Lead with any legal cominbation.
    type: play
    title: Round
    actions:
    - text: Clockwise
      type: play2
      title: Each Player
      actions:
      - text: Must play same number of cards as last played. Must be higher value.
        type: play3
        title: Follow
        prefix: Do
      - text: Cannot play. May opt out by choice.
        type: play3
        title: Or pass
        prefix: Else
      subtitle: Until 3 consecutive passes.
    - text: After 3 consequetive passes, highest played is winner of round and leads
        next round.
      type: play2
      title: Next Round
    reference:
      items:
      - Single
      - Pair
      - Triplet
      - ''
      - 5 Card Group (descending order of value)
      - ''
      - key: 1. Straight-flush
        value: five consecutive cards of the same suit
      - key: 2. Four-of-a-kind (+1)
        value: four cards of one rank, plus any fifth card
      - key: 3. Full-house
        value: three cards of one rank and two of another rank
      - key: 4. Flush
        value: any five cards of the same suit
      - key: 5. Straight
        value: five cards of consecutive rank with mixed suits
      title: Legal Combinations
  - text: Hand won by 1st to shed all cards.
    type: score
    title: Scoring
    reference:
      items:
      - Penalty points for remaining cards
      - "-1 point for each card if less than 10"
      - "-2 per card when 10 / 11 / 12 cards"
      - "-3 per card when 13 (i.e. -39)"
      - Winner scores +1 point for each penalty point
      title: Scoring Reference
  - text: When scoring completed.
    type: root2
    title: Next Hand
- text: When a player reaches target score.
  type: end
  title: Game End
---

{%- include rules.html -%}
