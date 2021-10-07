---
layout: post
title: "Frightcrawler"
image: images/frightcrawler.gif
categories:
  - hardware
tags:
  - crystal
  - mtg
---
# MtG deck legality checker

{% raw %}<img src="/images/frightcrawler.png" alt="Frightcrawler">{% endraw %}

[Frightcrawler](https://github.com/charlesrocket/frightcrawler) is a small tool I wrote to prepare for [MtG](https://magic.wizards.com/) tournaments. It fully supports [Helvault](https://apps.apple.com/us/app/helvault-mtg-card-scanner/id1466963201) and [AetherHub](https://aetherhub.com) (just in case) files. To validate your deck - scan the cards with `Helvault` and load CSV file into `Frightcrawler`:

```
Usage: frightcrawler -g modern -f PATH/TO/FILE
    -g GAME_FORMAT                   Set game format
    -f CSV_FILE                      Path to CSV file
    -i SCRYFALL_ID                   Get card info
    -h, --help                       Print documentation
    -v, --version                    Version
Supported CSV layouts: Helvault, Helvault Pro, AetherHub.
Supported formats: brawl, commander, duel, future, gladiator, historic, legacy,
modern, oldschool, pauper, penny, pioneer, premodern, standard, vintage.
```

```
frightcrawler -g commander -f /Users/chuck/Documents/git/helvault/oct5-b-mono.csv
```

[![asciicast](https://asciinema.org/a/438787.svg)](https://asciinema.org/a/438787)
