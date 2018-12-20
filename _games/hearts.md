---
layout: default
title: Hearts
resource: true
categories: [games]
aim: LOWEST score wins when a player reaches 100pts
deal: 17 (3) , 13 (4) or 10 (5 [2♦] & [2♣] removed)
players: 3 - 5
rank: '2, A, K, Q, J, 10…3; Suits: ♠ ♥ ♣ ♦'
category: Trick Taking Game
actions:
- text: ''
  type: root
  title: Hand
  actions:
  - text: Random dealer. 17 (<strong>3</strong><i class='fas fa-user'></i>) , 13 (<strong>4</strong><i
      class='fas fa-user'></i>) or  10 (<strong>5</strong><i class='fas fa-user'></i>
      [2♦] & [2♣] removed) cards each.
    type: deal
    title: Deal
    actions:
    - text: All players choose 3 cards to pass face down.
      type: deal2
      title: Pass Cards
      actions:
      - text: 'On 1st hand: pass to left, 2nd hand: pass to right, 3rd hand: pass
          opposite, 4th hand: no passing.'
        type: deal3
        title: Pass Rotation
  - text: Player with 2♣ leads by playing it (or 3♣ if no 2♣).
    type: play
    title: Play
    actions:
    - text: Lead any suit but not Hearts ♥ until a Heart has been played ('broken').
      type: play2
      title: Trick
      actions:
      - text: ''
        type: play3
        title: Each Player
        actions:
        - text: Play card following suit if possible.
          type: play4
          title: Try to follow suit
          prefix: ''
        - text: Including Heart ♥ and Black Maria Q♠.
          type: play4
          title: Otherwise play any other suit
          prefix: ''
        subtitle: Until all players have played
      - text: Winner of Trick is highest rank of lead suit. Winner leads next trick
          until no more cards.
        type: play2
        title: Next Trick
      subtitle: Repeat until all cards have been played
  - text: Each Heart won is 1pt. Black Maria Q♠ is 13pts.
    type: score
    title: Score
    actions:
    - text: If player wins ALL Hearts & Q♠ remove 26pts from their score or add 26pts
        to all others (player choice).
      type: score
      title: Shooting The Moon
    reference:
      items:
      - key: Each Heart
        value: 1pt
      - key: Black Maria Q♠
        value: 13pts
      - key: Shooting the moon
        value: "-26pts"
      title: Scoring Reference
  - text: When all cards played.
    type: root
    title: Next Hand
  subtitle: Repeat until a player reaches target score
- text: A player reaches 100pts (or any value agreed). The player with the lowest
    score wins.
  type: end
  title: Game End

---

**title**

{%- include rules.html -%}

## History

Hearts card game has origins from 18 century game Reversis. It has evolved until the commonly known variant presented here. Microsoft shipped it with Windows in the 1990's and reached a whole new audience.

## Play

- Shooting the moon is a risky strategy which only really works if no-one suspects you are attempting it.
- Temporary loose alliances between players is one of the most interesting aspects of this game.

## Strategy Tips

- Gang up on the player with the lowest score.
- Whilst trying to shed the queen of spades at the earliest opportunity seems like an obvious good move, it can be useful to hang on to it to force it upon the leading player.
- The cards passed to you probably provide some clues about what tactics they are going to be using that hand.
- If they pass low hearts, they may be trying to shoot the moon, in which case you may need to play a self sacrificing game to stop them (temporary alliances form a key part of this card game!)
- If you get a bunch of the same suit, the player may be trying to build a void of that suit. Be careful not to play a high card of that suit!
- Building a void in a suit gives an opportunity to discard any card when that suit is led - this is really useful - especially if you have the Queen of Spades.
- Sometimes it can be useful to help the losing player to stop them hitting 100 if you are not the current leader, as that signals the end of the game.
- Taking the first trick with hearts stops anyone but you shooting the moon.
- Taking a few hearts is nothing compared with taking the queen of spades so stay focussed on avoiding taking her!