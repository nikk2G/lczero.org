---
title: "Jumping on the NNUE bandwagon"
# slug: "blog-post-title"
published: 2021-04-01
#draft: true
author: "borg"
# image: "name"
# cover: "cover.png" # Default
---

Unless you were living under a rock during the last year, you have probably heard of the revolution that has been happening in computer chess. That is assuming you are interested in computer chess, but if you are not then why are you reading this? We are talking about Efficiently Updatable Neural Networks (referred to as NNUE, giving new meaning to backronyms) allegedly discovered by Japanese monks on sacred FORTRAN punched cards. The introduction of NNUE to the Alpha-Beta search of Stockfish resulted in impressive gains, despite initial bugs and ridicule. Since then the dominoes have been falling one after the other and now almost all the top chess engines have a NNUE implementation. Obviously Lc0 couldn’t be far behind, so we proudly present LcFiSh, the latest incarnation of Lc0 with NNUE technology.

<!--more-->

Of course, no NNUE chess engine can work without a net. Moreover, no serious chess engine can ignore the TCEC rules, as participating in TCEC is all we want anyway. Therefore, the restriction that “All NNUE training data should be generated by the unique engine's own search and/or eval code” is really important, so the capability to generate training data in the standard Lc0 v6 training format, using selfplay mode, is retained. Using such training data, the net is trained in a repetitive process that [generalizes](https://youtu.be/bhtO4DsSazc) the information from the input positions seen, to allow the evaluation of any position. Starting with a few hundred million positions generated from recent T60 series nets, a custom NNUE net was trained specifically for LcFiSh in a completely “zero” (no human chess knowledge involved) way. [Having never trained a NNUE net](https://youtu.be/v9UJXASmh48), this required a bit of trial and error, and is an ongoing process but the initial results are very promising.

The end result is a chess engine with an interesting style of play (no idea really, but this is what every engine author says), based on the [close cooperation](https://youtu.be/34_SfP7ZCXA) of the custom NNUE net and LcFiSh’s search. As the NNUE search is distinct from Lc0’s search and the custom net is trained following the rules (as mentioned above), we understand LcFiSh is eligible for participation in TCEC and we eagerly await our invitation and expect an excellent result.

Windows binaries are provided on the [release page](https://github.com/borg323/lc0/releases/tag/lcfish) for all recent processor architectures, as the NNUE technology greatly benefits from the latest processor features. To build for Linux you follow the normal Lc0 build process, but there is a new option to use to specify the processor architecture, as in the following example:
`CXX=g++-9 CC=gcc-9 ./build.sh -Darch=x86-64-avx512-vnni`

[Have fun!](https://youtu.be/dQw4w9WgXcQ)

