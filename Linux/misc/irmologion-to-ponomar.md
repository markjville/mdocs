# Proceedure to convert Irmologion to Ponomar font

1. Install [Lingua-cu utilities](https://github.com/typiconman/Perl-Lingua-CU)

Note- there were many dependencies needed to complete installation:

```
perl-ExtUtils-MakeMaker 
perl-Unicode-Collate
perl-Test-Simple
perl-Tie-IxHash
perl-Unicode-Collate
ucviewer
```

Then one can install this utility;

```
perl Makefile.PL
make
make test
make install
```

2. Convert Irmologion doc to a unicode text which then can be used for Ponomor font:
`
   ucs2unicode document.txt
`

4. It will output `document.utf`

One can select all text and change to ponomar font.
