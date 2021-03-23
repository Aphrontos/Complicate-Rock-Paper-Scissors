# Introduction

The traditional game of rock paper scissors only has 3 weapons. 
Have you ever wondered how a variant with more than 3 weapons work, but are too lazy to compute the strength and weaknesses?
Well wonder no long, since this code generalizes the game to any variant that has a fair strengths and weaknesses (SW) chart up to rotation.

Okay, what does a "fair SW chart" mean? 
A rock-paper-scissors variant must have:
* n number of weapons, where n ≡ 1 (mod 2) ∧ n ≥ 3 ∧ n ∈ ℤ
* each weapon must be:
  * strong against one half of weapons
  * weak to the remaining half of weapons.

The "up to rotation" part will be explained later.

SW chart of Normal rock-paper-scissors:

X            | Rock | Paper | Scissors
------------ | ---- | ----- | --------
**Rock**     | D    | W     | L
**Paper**    | L    | D     | W
**Scissors** | W    | L     | D

Variant:

X            | Paper | Rock | Scissors
------------ | ----- | ---- | --------
**Paper**    | D	   | L	  | W
**Rock**     | W	   | D	  | L
**Scissors** | L	   | W	  | D

As is, this table is the same as the above table, so we need to relabel the column and row headers:

X            | Rock | Paper | Scissors
------------ | ---- | ----- | --------
**Rock**     | D    | L     | W
**Paper**    | W    | D     | L
**Scissors** | L    | W     | D

As you can see, this doesn’t really make any sense. So relabeling again so that the weapons have numbers as names:

X     | 1 | 2 | 3
----- | - | - | -
**1** | D | L | W
**2** | W | D | L
**3** | L | W | D

An example with 5 weapons:

X     | 1 | 2 | 3 | 4 | 5
----- | - | - | - | - | -
**1** | D | W | W | L | L
**2** | L | D | W | W | L
**3** | L | L | D | W | W
**4** | W | L | L | D | W
**5** | W | W | L | L | D

The above is the "base" 5 weapon SW chart. As discussed earlier, each weapon is weak to 2 other and strong against the remaining 2.

If the rows and columns are rearranged and headers are relabeled, this gives a new but fair SW chart.

X     | 1 | 2 | 3 | 4 | 5
----- | - | - | - | - | -
**1** | D | L | W | W | L
**2** | W | D | W | L | L
**3** | L | L | D | W | W
**4** | L | W | L | D | W
**5** | W | W | L | L | D

But, unfortunately, we lost information. We don't know the variant code any more. To fix this:

X     | X     | 1 | 2 | 3 | 4 | 5
----- | ----- | - | - | - | - | -
**X** | **X** | 2 | 1 | 3 | 4 | 5
**1** | 2     | D | L | W | W | L
**2** | 1     | W | D | W | L | L
**3** | 3     | L | L | D | W | W
**4** | 4     | L | W | L | D | W
**5** | 5     | W | W | L | L | D

The column and row in bold are the weapon names, while the column and row in italics are the variant code.

Now, given this you may think that there would be 5! variations, but no there are actually only 4! variations, since each variation has 5 rotations.
For example: 12345 and 23451 are the same SW chart because they're rotations of each other.
So in general, for n weapons, there are (n-1)! SW chart variations.

# Patch Notes:
1.0 Initial Commit

# USAGE
1. Download the Jupyter Notebook. Make sure your Python version is at least 3.9
2. 
