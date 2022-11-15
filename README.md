# Humdrum Analysis of 370 Bach Chorales 





# Preface



The analysis via humdrum/ terminal is focused on seven voice leading fields/topics:

1. Perfect/diminished fifth (`/res1a/+b`)
2. Hidden unison/fifth/octaves `(/res2a/+b+c)`
3. Consecutive fifths `(/res3a/+b)`
4. Consecutive octaves `(res4a/+b+c+d)`
5. Parallel fifths  `(/res5/)`
6. Parallel octaves `(/res6/)`
7. Melodic Intervals `(/res5/)`

============================================================================

The state of the project is still **in progress** and needs additional examination and checks...

============================================================================ 

# Usage



1. Just looking at the results:
   - download the folders and just drag an drop the kern files (*.krn) onto [verovio.humdrum](https://verovio.humdrum.org/) to see thew analys results (in red colour)

2. Eval humdrum code via terminal:
   - install humdrum https://github.com/humdrum-tools/humdrum-tools
   - get the source files (the 370 chorales in kern format): https://github.com/craigsapp/bach-370-chorales/tree/master/kern 



# Analysis



 

## 1a: Perfect/diminished fifth (p5/d5)

Code (terminal)[^1]

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales  --chromatic --search "^d5.[^0].[^0].p5$"  -k "${array1[$i]}" --count)
   echo "d5/p5: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
d5/p5: 0 times

1,3:
bass,alto:
d5/p5: 0 times

1,4:
bass,soprano:
d5/p5: 0 times

2,3:
tenor,alto:
d5/p5: 2 times

2,4:
tenor,soprano:
d5/p5: 2 times

3,4:
alto,soprano:
d5/p5: 0 times



## 1b: Diminished/perfect fifth (d5/p5)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var=$(cint h://370chorales --chromatic --search "^d5.[^0].[^0].p5$" -k "${array1[$i]}" --count)
   echo "d5/p5: $var times\n"
done
```

*output:*

1,2:
bass,tenor:
d5/p5: 0 times

1,3:
bass,alto:
d5/p5: 0 times

1,4:
bass,soprano:
d5/p5: 0 times

2,3:
tenor,alto:
d5/p5: 2 times

2,4:
tenor,soprano:
d5/p5: 2 times

3,4:
alto,soprano:
d5/p5: 0 times



## • res2a: Hidden unison (../p1)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -tUo --search "^\d\s[^0]\s[^0]\s0"  -k "${array1[$i]}" --count)
   echo "xx/p1: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
xx/p1: 112 times

1,3:
bass,alto:
xx/p1: 2 times

1,4:
bass,soprano:
xx/p1: 0 times

2,3:
tenor,alto:
xx/p1: 8 times

2,4:
tenor,soprano:
../p1: 0 times

3,4:
alto,soprano:
xx/p1: 8 times



## • res2b: Hidden fifth (xx/p5)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -tUo --search "^\d\s[^0]\s[^0]\s7"  -k "${array1[$i]}" --count)
   echo "xx/p5: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
xx/p5: 54 times

1,3:
bass,alto:
xx/p5: 7 times

1,4:
bass,soprano:
xx/p5: 0 times

2,3:
tenor,alto:
xx/p5: 246 times

2,4:
tenor,soprano:
xx/p5: 139 times

3,4:
alto,soprano:
xx/p5: 237 times



## • res2c: Hidden octave (xx/p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -tUo --search "^\d\s[^0]\s[^0]\s12"  -k "${array1[$i]}" --count)
   echo "xx/p8: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
xx/p8: 176 times

1,3:
bass,alto:
xx/p8: 40 times

1,4:
bass,soprano:
xx/p8: 1 times

2,3:
tenor,alto:
xx/p8: 6 times

2,4:
tenor,soprano:
xx/p8: 179 times

3,4:
alto,soprano:
xx/p8: 20 times



## • res3a: Consecutive fifths (p5/p5+p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^7\s-?[^0]+\s[^0]+\s19"  -k "${array1[$i]}" --count)
   echo "p5/p5+p8: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p5/p5+p8: 7 times

1,3:
bass,alto:
p5/p5+p8: 13 times

1,4:
bass,soprano:
p5/p5+p8: 0 times

2,3:
tenor,alto:
p5/p5+p8: 0 times

2,4:
tenor,soprano:
p5/p5+p8: 3 times

3,4:
alto,soprano:
p5/p5+p8: 0 times



## • res3b: Consecutive fifths (p5+p8/p5)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^19\s-?[^0]+\s[^0]+\s7"  -k "${array1[$i]}" --count)
   echo "p5+p8/p5: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p5+p8/p5: 7 times

1,3:
bass,alto:
p5+p8/p5: 6 times

1,4:
bass,soprano:
p5+p8/p5: 6 times

2,3:
tenor,alto:
p5+p8/p5: 0 times

2,4:
tenor,soprano:
p5+p8/p5: 15 times

3,4:
alto,soprano:
p5+p8/p5: 0 times



## • res4a: Consecutive octaves (p8/p8+p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^12\s-?[^0]+\s[^0]+\s24"  -k "${array1[$i]}" --count)
   echo "p8/p8+p8: $var2 times\n"
done
```

*output:*


1,2:
bass,tenor:
p8/p8+p8: 0 times

1,3:
bass,alto:
p8/p8+p8: 1 times

1,4:
bass,soprano:
p8/p8+p8: 0 times

2,3:
tenor,alto:
p8/p8+p8: 0 times

2,4:
tenor,soprano:
p8/p8+p8: 0 times

3,4:
alto,soprano:
p8/p8+p8: 0 times





## • res4b: Consecutive octaves (p8+p8/p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^24\s-?[^0]+\s[^0]+\s12"  -k "${array1[$i]}" --count)
   echo "p8+p8/p8: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p8+p8/p8: 0 times

1,3:
bass,alto:
p8+p8/p8: 4 times

1,4:
bass,soprano:
p8+p8/p8: 1 times

2,3:
tenor,alto:
p8+p8/p8: 0 times

2,4:
tenor,soprano:
p8+p8/p8: 0 times

3,4:
alto,soprano:
p8+p8/p8: 0 times



## • res4c: Consecutive octaves (p8/p1)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^12\s-?[^0]+\s[^0]+\s0"  -k "${array1[$i]}" --count)
   echo "p8/p1: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p8/p1: 0 times

1,3:
bass,alto:
p8/p1: 0 times

1,4:
bass,soprano:
p8/p1: 0 times

2,3:
tenor,alto:
p8/p1: 2 times

2,4:
tenor,soprano:
p8/p1: 1 times

3,4:
alto,soprano:
p8/p1: 2 times



## • res4d: Consecutive octaves (p1/p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^0\s-?[^0]+\s[^0]+\s12"  -k "${array1[$i]}" --count)
   echo "p1/p8: $var2 times\n"
done
```

*output:*


1,2:
bass,tenor:
p1/p8: 1 times

1,3:
bass,alto:
p1/p8: 0 times

1,4:
bass,soprano:
p1/p8: 0 times

2,3:
tenor,alto:
p1/p8: 3 times

2,4:
tenor,soprano:
p1/p8: 0 times

3,4:
alto,soprano:
p1/p8: 1 times




## • res5: parallel fifths (p5/p5)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^7.[^0].[^0].7$"  -k "${array1[$i]}" --count)
   echo "p5/p5: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p5/p5: 1 times

1,3:
bass,alto:
p5/p5: 0 times

1,4:
bass,soprano:
p5/p5: 0 times

2,3:
tenor,alto:
p5/p5: 3 times

2,4:
tenor,soprano:
p5/p5: 1 times

3,4:
alto,soprano:
p5/p5: 1 times



## • res6: parallel octaves (p8/p8)

Code (terminal):

```shell 
array1=("1,2" "1,3" "1,4" "2,3" "2,4" "3,4")
array2=("bass,tenor" "bass,alto" "bass,soprano" "tenor,alto" "tenor,soprano" "alto,soprano")
for ((i=1; i<=${#array1[@]}; i++)); do 
   echo "${array1[$i]}:"
   echo "${array2[$i]}:"
   var2=$(cint h://370chorales --12 -t --search "^12.[^0].[^0].12$"  -k "${array1[$i]}" --count)
   echo "p8/p8: $var2 times\n"
done
```

*output:*

1,2:
bass,tenor:
p8/p8: 2 times

1,3:
bass,alto:
p8/p8: 2 times

1,4:
bass,soprano:
p8/p8: 0 times

2,3:
tenor,alto:
p8/p8: 0 times

2,4:
tenor,soprano:
p8/p8: 2 times

3,4:
alto,soprano:
p8/p8: 0 times




## • res7: melodic intervals (statistical appearance)

Code (terminal):


```shell
humcat h://370chorales | extract -f 1 | serialize | mint | ridx -H | grep -v r | grep -v '[[]' | sortcount -t 
humcat h://370chorales | extract -f 2 | serialize | mint | ridx -H | grep -v r | grep -v '[[]' | sortcount -t 
humcat h://370chorales | extract -f 3 | serialize | mint | ridx -H | grep -v r | grep -v '[[]' | sortcount -t 
humcat h://370chorales | extract -f 4 | serialize | mint | ridx -H | grep -v r | grep -v '[[]' | sortcount -t 
```

*output:*


| Bass | Tenor | Alto | Soprano |
| ---- | ---- | ---- | ---- |
| 4260    +M2  |  4597    -M2   |  5008  P1  | 4724    -M2   |
| 4141    -M2  |  4299    P1    |  4067  -M2 | 3696    +M2  |
| 2980    +m2  |  3861    +M2   |  3501  +M2 | 2769    P1  |
| 2602    -m2  |  2869    -m2   |  3216  -m2 | 2373    -m2  |
| 1826    +P4  |  2227    +m2   |  2444  +m2 | 1939    +m2  |
| 1403    -P5  |  1076    +P4   |  904   +P4 | 601     +P4  |
| 800     P1   |  543     -m3   |  787   -M3 | 495     -m3  |
| 730     -P4  |  486     -M3   |  378   -m3 | 343     -M3  |
| 676     -m3  |  451     -P5   |  300   +m3 | 298     +m3  |
| 561     -M3  |  357     +m3   |  264   -P4 | 258     -P4  |
| 517     +P8  |  356     -P4   |  244   +M3 | 224     +P5  |
| 508     +P5  |  265     +P5   |  182   -P5 | 186     +M3  |
| 416     -P8  |  234     +M3   |  124   +P5 | 119     -P5  |
| 254     A1   |  109     -d5   |  59    A1  | 41      +P8  |
| 176     +M3  |  79      +m6   |  53    +M6 | 27      +m6  |
| 150     +m3  |  71      +M6   |  48    d1  | 16      -m6  |
| 138     -d5  |  61      A1    |  41    +m6 | 15      +M6  |
| 72      -m6  |  54      +P8   |  25    +P8 | 4       -d5  |
| 69      -d4  |  39      d1    |  20    -d5 | 4       +d4  |
| 62      +M6  |  30      -P8   |  15    -P8 | 4       -P8  |
| 43      +m6  |  24      -M6   |  11    -d4 | 3       +m7  |
| 34      d1   |  23      +d4   |  10    -m6 | 3       A1  |
| 26      +m7  |  19      -m6   |  7     +d4 | 3       d1  |
| 22      -M6  |  16      +d5   |  4     +m7 | 1       -d4  |
| 18      -d7  |  10      -d4   |  3     +d5 | 1       +d5  |
| 17      +M7  |  5       +m7   |  3     -M6 | 1       -M6  |
| 16      -m7  |  1       +d7   |  1     +d3 | TOTAL:  18148  |
| 15      +A4  |  1       -d7   |  1     +M9 |                |
| 8       +M9  |  1       -A4   |  1     -A5 |              |
| 8       +A5  |  TOTAL:  22164 |  1     +M7 |              |
| 7       -M9  |                |  1     +A4 |              |
| 6       +P11 |                |TOTAL:  21723|             |
| 6       +M10 |                |           |               |
| 5       +A8  |                |           |               |
| 5       -M7  |                |           |               |
| 4       +P12 |                |           |               |
| 2       -d3  |                |           |               |
| 2       +m10 |                |           |               |
| 1       +d4  |                |           |               |
| 1       +d5  |                |           |               |
| 1       -m10 |                |           |               |
| 1       +P15 |                |           |               |
| 1       -A8  |                |           |               |
| 1       +d7  |                |           |               |
| 1       +d3  |                |           |               |
| 1       -M10 |                |           |               |
| TOTAL:  22593|                |           |               |



----

[^1]: to run the code inside the terminal, you need to install humdrum first! 
