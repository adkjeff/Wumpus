# Wumpus
Play the Wumpus game -- avoid pits and the Wumpus and find the gold

Propostional logic (knowledge base, resolution method and queries) are handled via functions from AIMA found in:
https://github.com/aimacode/aima-python/blob/master/logic.py
http://aima.cs.berkeley.edu/python/utils.html

Here is an example of the moves that are made for the following initial board:
(the agent "A" always starts in the lower left corner)

--------------------
     -  -  G  P 
     W  -  P  - 
     -  -  -  - 
     A  -  P  - 
--------------------

Move # 1 -- to (1, 1): Safe
------------------------------------------------------------------------
111  111  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
111  111  111  111     ---  ---  ---  ---      0  0  0  0     W  -  P  - 
000  111  111  111     ---  ---  ---  ---      0  0  0  0     -  -  -  - 
000  000  111  111     ---  ---  ---  ---      1  0  0  0     A  -  P  - 
------------------------------------------------------------------------
Move # 2 -- to (1, 2): safe, detect stench
------------------------------------------------------------------------
111  111  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
010  111  111  111     ---  ---  ---  ---      0  0  0  0     W  -  P  - 
000  010  111  111     -S-  ---  ---  ---      2  0  0  0     A  -  -  - 
000  000  111  111     ---  ---  ---  ---      1  0  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 3 -- to (2, 1): safe, detect breeze
------------------------------------------------------------------------
111  111  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
020  111  111  111     ---  ---  ---  ---      0  0  0  0     W  -  P  - 
000  000  111  111     -S-  ---  ---  ---      2  0  0  0     -  -  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  A  P  - 
------------------------------------------------------------------------
Move # 4 -- to (2, 2): safe
------------------------------------------------------------------------
111  111  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
020  000  111  111     ---  ---  ---  ---      0  0  0  0     W  -  P  - 
000  000  000  111     -S-  ---  ---  ---      2  4  0  0     -  A  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 5 -- to (2, 3): safe, detect breeze & stench
------------------------------------------------------------------------
111  110  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
020  000  110  111     ---  BS-  ---  ---      0  5  0  0     W  A  P  - 
000  000  000  111     -S-  ---  ---  ---      2  4  0  0     -  -  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 6 -- to (3, 2): safe, detect breeze
------------------------------------------------------------------------
111  110  111  111     ---  ---  ---  ---      0  0  0  0     -  -  G  P 
020  000  100  111     ---  BS-  ---  ---      0  5  0  0     W  -  P  - 
000  000  000  100     -S-  ---  B--  ---      2  4  6  0     -  -  A  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 7 -- to (2, 4): risky, detect glitter
------------------------------------------------------------------------
001  000  001  111     ---  --G  ---  ---      0  7  0  0     -  A  G  P 
020  000  200  111     ---  BS-  ---  ---      0  5  0  0     W  -  P  - 
000  000  000  100     -S-  ---  B--  ---      2  4  6  0     -  -  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 8 -- to (1, 4): safe, detect stench
------------------------------------------------------------------------
000  000  002  111     -S-  --G  ---  ---      8  7  0  0     A  -  G  P 
020  000  200  111     ---  BS-  ---  ---      0  5  0  0     W  -  P  - 
000  000  000  100     -S-  ---  B--  ---      2  4  6  0     -  -  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
Move # 9 -- to (3, 4): gold, detect breeze
Game Won!
------------------------------------------------------------------------
000  000  002  111     -S-  --G  B--  ---      8  7  9  0     -  -  A  P 
020  000  200  111     ---  BS-  ---  ---      0  5  0  0     W  -  P  - 
000  000  000  100     -S-  ---  B--  ---      2  4  6  0     -  -  -  - 
000  000  200  111     ---  B--  ---  ---      1  3  0  0     -  -  P  - 
------------------------------------------------------------------------
