# Stove Ownership

**Category:** Crypto

**Points:** 150

**Solves:** 5

**Description:**

A **T**YP**E**
**O**F SAL
**T** CU**R**E
D P**ORK**

AN **E**N**G**
LI**S**H P
HIL**OS**
**O**P**H**ER
**S**TA**TE**
S**MAN S**
C**IE**NT
**IS**T J**U**
**RI**ST O
R**ATO**R
A**N**D **AU**
THOR B
O**R**N 15
61 DI**E**
**D** 162**6**

**C**A**LVI**
N **A**N**D** H
O**BB**E**S**
**A**N**D P**A
NTS **A**R
**E** O**V**E**R**
RA**TE**D

```
NKVNKVNKVNKVNKVNK! IDF XSQCJM EOPZ QC ISFFXIE{UVNWOFGZF_QC_JNWFS}
```


## Write-up
Each of the paragraphs - "A type of salt-cured pork," "An English philosopher, statesman, scientist, jurist, orator, and author (born 1561, died 1626)," and "Calvin and Hobbes and Pants are Overrated" - is a clue for the word BACON. The first paragraph is a [culinary description](https://en.wikipedia.org/wiki/Bacon) of bacon; the second paragraph is from the [biography of  Sir Francis Bacon](https://en.wikipedia.org/wiki/Francis_Bacon); and the final paragraph is a reference to [these](http://www.pantsareoverrated.com/archive/2011/05/10/hobbes-and-bacon/) [lovely](http://www.pantsareoverrated.com/archive/2011/05/12/hobbes-and-bacon-002/) [comic](http://www.pantsareoverrated.com/archive/2011/10/11/hobbes-and-bacon-03-2/) [strips](http://www.pantsareoverrated.com/archive/2011/10/13/hobbes-and-bacon-04-2/). Furthermore, the title of the puzzle, 'Stove Ownership', is a reference to [this xkcd](https://xkcd.com/418/) about bacon.

The Bacon cipher (invented by Sir Francis Bacon!) is a cipher that encodes 5-bit patterns in chunks of 5 symbols using any binary feature (italics, capitalization, color, etc.) For example, suppose the encoding is that a lowercase letter encodes a 0 and an uppercase letter encodes a 1. In this case, the 5-letter word bAcON encodes the message 01011.

In this problem, the bit pattern is determined by the bold and normal letters in each 5 symbol line, where a normal symbol encodes a 0 and a bold symbol encodes a 1.

Thus, the lines of text in the clues correspond to the following bit patterns:

```
01001  # e.g. normal, bold, normal, normal, bold
10000
10010
00111
00101
00100
00011
10100
10011
01111
01100
11001
11000
01110
01011
00000
01000
00001
10001
10111
01010
01101
10110
00010
10101
00110
```

Next, note that there are 26 of these bit patterns, and their values are a permutation of [0..25]. This suggests a substitution cipher. Namely, the first entry - `01001` (= 9 in binary) - means that the letter with index 9 (= `'J'`) will encode to `'A'`, and the final entry - `00110` (= 6 in binary) - means that the letter with index 6 (= `'G'`) will encode to `'Z'`. We see that `'A'` will encode to `'P'`, because the `00000` row (of all normal text) corresponds to the 16th row, and `'P'` is the 16th letter. Overall, the encoding map generated by this process is:

```
{
	'A': 'P',
	'B': 'R',
	'C': 'X',
	'D': 'G',
	'E': 'F',
	'F': 'E',
	'G': 'Z',
	'H': 'D',
	'I': 'Q',
	'J': 'A',
	'K': 'U',
	'L': 'O',
	'M': 'K',
	'N': 'V',
	'O': 'N',
	'P': 'J',
	'Q': 'B',
	'R': 'S',
	'S': 'C',
	'T': 'I',
	'U': 'H',
	'V': 'Y',
	'W': 'W',
	'X': 'T',
	'Y': 'M',
	'Z': 'L'
}
```

Using this encoding map as a substitution cipher for the ciphertext in the puzzle yields the final plaintext:

OMNOMNOMNOMNOMNOM! THE CRISPY FLAG IS TREECTF{KNOWLEDGE_IS_POWER}

Therefore, the final flag is `TREECTF{KNOWLEDGE_IS_POWER}`.

## Additional Resources

- [Bacon's Cipher](https://en.wikipedia.org/wiki/Bacon%27s_cipher)
- See CTF participant data [here](treectf.2018-02-18.zip).