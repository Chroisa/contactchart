
(Way) below is a contact chart composed from [this source](https://gist.github.com/lydell/c439049abac2c9226e53), which itself was composed from the Google corpus.  The contact chart is an old codebreaker tool that assembles frequencies of bigrams (two letters together).  Consider this sentence fragment:

Twas brillig and the slithy toves

Here, we can see that 't' is followed by the following letters:

w (once)  
h (twice)  
o (once)  

And was preceded by these letters:

d (once)  
i (once)  
y (once)  

The original contact chart used a format similar to the following:
<pre>
 (the letter that precedes  (the letter that follows
  our letter of interest)    our letter of interest)
ABCDEFGHIJKLMNOPQRSTUVWXYZ ABCDEFGHIJKLMNOPQRSTUVWXYZ
   1    1               1 T              1    2  1   
  (quantity of times  (our letter     (quantity of times
   each preceding      of interest)    each following
   letter appeared)                    letter appeared)
</pre>

Assembling this for the other letters in that sentence results in:
<pre>
ABCDEFGHIJKLMNOPQRSTUVWXYZ ABCDEFGHIJKLMNOPQRSTUVWXYZ
      1               1   A             1    1       
                  1       B                 1        
             1            D                   1      
       1             1    E                  2       
        1                 G1                         
                   2      H    1                   1 
           2     1        I      1    1       1      
        1  2              L        1  1       1      
                   1      O                     1    
1                     1   N   1              1       
 1                        R        1                 
1   2                     S 1         1              
   1    1               1 T              1    2  1   
              1           V    1                     
                   1      W1                         
       1                  Y                   1      
</pre>
Note that this ignores punctuation and spaces.  These could have been considered, resulting in a slightly different table.

I use a mildly modified format of this that removes the numbers and merely preserves the order.  In the "pre" table, if you start with the letter 'a', it is most likely to be preceded by an 'H', then by an 'E', then by an 'R', etc. (I use UPPERCASE and lowercase to distinguish input from output).

<ul>ab</ul>  
<pre>
HA
EI
RO
MM
CU
TE
LR
..
..
..
</pRE>

Similarly, in the "post" table, if you start with an 'a', it is most likely FOLLOWED by 'N', then by a 'T', then by an 'L', etc.
<ul>ab...</ul>  
<pre>
NE...
TL...
LO...
RU...
SY...
CA...
DR...
..
..
..
</pre>

For reference, the intermediate tables that show counts from the original dataset are also included (intermedPRE and intermedPOST).  You can see how this is sorted by comparing the first few values in column B (the 'a' column): 79794787 (A), 6479202253 (B) matches with lines 399 ("aa") and 121 ("ab") of bigrams.json.

The data below is constructed from the aforementioned English bigram source and was remarkably easy to construct:

1) Sort bigrams by last letter and consider the frequencies.  When the FIRST letters are sorted alphabetically, these are the "PRE" part of the contact chart for one letter - order those numbers in a horizontal strip BEFORE the central letter 'A' in the chart.
2) Repeat for the remaining 25 letters.
3) Sort bigrams by the FIRST letter and consider the frequencies.  When the LAST letters are sorted alphabetically, these are the "POST" part of the contact chart for one letter - order those numbers in a horizontal strip AFTER the central letter 'A' in the chart.
4) Repeat for the remaining 25 letters.

So this is not so much production of a new data set as a very minor rearrangement of an existing data set into a familiar data structure - the contact chart.

It is presented in CSV so that your [LOOKUPs](https://support.office.com/en-us/article/LOOKUP-function-446D94AF-663B-451D-8251-369D5E3864CB) may be productive!

Special thanks to:
* [Helen Gaines](https://en.wikipedia.org/wiki/Helen_Fouch%C3%A9_Gaines), author of Cryptanalysis ([archive.org](https://archive.org/details/cryptanalysis00hele), [Amazon](https://www.amazon.com/Cryptanalysis-Study-Ciphers-Their-Solution/dp/0486200973)) for many things, including a great contact chart at the back of the book.
* [@lydell](https://gist.github.com/lydell)
