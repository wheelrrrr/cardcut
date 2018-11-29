---
layout: default
title: Cribbage
resource: true
categories: [games]
aim: The first to 121 points
deal: 6 (2x), 5 (3-4)
players: 2 - 4
rank: High ( K, Q, J ... 3, 2, A ) Low
category: Adding Game
actions:
- text: ''
  type: root
  title: Hand
  actions:
  - text: Cut for dealer. Deal 6 (<strong>2x</strong><i class='fas fa-user'></i>)
      or 5 (<strong>3-4</strong><i class='fas fa-user'></i>) cards each.
    type: deal
    title: Deal
    actions:
    - text: All discard 2x cards (<strong>2x</strong><i class='fas fa-user'></i>)
        to form 'crib' face down. Discard 1x card with (<strong>3-4</strong><i class='fas
        fa-user'></i>). All players should now have 4 cards. Crib should contain 4
        cards. Deal extra card to Crib if required.
      type: deal2
      title: Discard
    - text: Right of dealer cuts for Start Card and turns it up.
      type: deal2
      title: Start Card
    - text: If 'Start Card' is a Jack, dealer scores 2 (for his Heals).
      type: deal2
      title: Score
  - text: Start left of dealer
    type: play
    title: Pegging
    actions:
    - text: ''
      type: play2
      title: Round
      actions:
      - text: ''
        type: play3
        title: Each Player
        actions:
        - text: Play 1x card face up in (must play if possible). Say aloud running
            total as you play. Keep played cards in front of each player.
          type: play4
          title: Play
          prefix: Do
        - text: Pass if cannot play to '31' or under. Say 'Go!'.
          type: play4
          title: Pass
          prefix: Else
        - text: Peg anything which scores immediately.
          type: play4
          title: Score
        subtitle: Until no player can play to 31 or under
      - text: Reset running total to zero. Score 1pt for last card played. Turn over
          all played cards. Left of last player leads next.
        type: play3
        title: Next
        subtitle: When no cards can be played
      subtitle: Repeat until all cards played
    reference:
      items:
      - Scoring is pegged immediately.
      - In 4P game players are paired, sit opposite and score together
      - 15 = 2
      - Last card 31 = 2
      - Last card under 31 = 1
      - Pair = 2
      - Set 3x = 6
      - Set 4x = 12
      - Run 3x = 3
      - Run 4x = 4 etc
      - Runs may be out of sequence but still count e.g. [4-6-5]= 3
      - Runs must be uninterupted e.g. [4-9-6-5] = No score
      title: Scoring Reference
  - type: score
    title: Hand Scoring
    actions:
    - text: Left of dealer
      type: score2
      title: Each Player
      actions:
      - text: Reveal hand and score as many combinations as possible (inc. 'Start
          Card').
        type: score3
        title: Score
      subtitle: Until all players have scored (dealer last)
    - text: After Dealer scores own hand, turn over 'Crib' and score combinations
        (inc. 'Start Card').
      type: score2
      title: Score Crib
    reference:
      items:
      - 15 = 2
      - Pair = 2
      - Set 3x [7-7-7] = 6
      - Set 4x [7-7-7-7]= 12
      - Run 3x [5-6-7] = 3
      - Run 4x [5-6-7-8] = 4 etc.
      - Flush 4 = 4
      - Flush 5 = 5 (inc. Starter)
      - Nobs = 1 (Jack of same suit as Starter)
      title: Scoring Reference
  - text: When all cards have been played and scored.
    type: flow
    title: Next Hand
  subtitle: Repeat until player reaches target score
- text: First player reaches 120pts wins (or any value agreed).
  type: end
  title: Game End
---

{%- include rules.html -%}
