# Huffman coding

This code is based on Michael Dipperstein's [LGPL](http://www.gnu.org/licenses/licenses.html#LGPL) Huffman Code implementation at http://michael.dipperstein.com/huffman/ . The initial commit of the code was taken from his zipfile at http://michael.dipperstein.com/huffman/huffman-0.9.zip

Michael's original README is [here](README_original)


## Purpose

The code retains it's original ability to compress and decompress files.

The code can now output the Huffman table in C code format, for inclusion into another program. The particular motivation was for including the Huffman table in [betaflight](https://github.com/betaflight/betaflight), in particular this (issue)[https://github.com/betaflight/betaflight/issues/1198]: compressing the black box log file for download.

I've made the minimum number of changes necessary to acheive my goals.


## Usage

Compile the program using `make`. This produces a program called `sample`

Show options
```
sample -h
```

Compress file `blackboxlog.txt` using canonical Huffman form to produce `bbcompressed.bin`
```
sample -C -c -iblackboxlog.txt -obcompressed.bin
```

Decompress file `blackboxlog.bin` using canonical Huffman form to produce `blackboxlog2.txt`
```
sample -C -d-ibcompressed.bin -oblackboxlog2.txt
```


Parse file `blackboxlog.txt` to produce a canonical Huffman table that can be used in a C compression program.
```
sample -C -s -iblackboxlog.txt -ohuffmantable.c
```

Parse file `blackboxlog.txt` to produce a canonical Huffman tree that can be used in a C decompression program.
```
sample -C -t -iblackboxlog.txt -ohuffmantree.c
```