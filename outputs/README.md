# how to score

## BEA 19 

### BEA 19 valid

```
wget -nc https://www.cl.cam.ac.uk/research/nl/bea2019st/data/ABCN.dev.bea19.orig

wget -nc https://www.cl.cam.ac.uk/research/nl/bea2019st/data/wi+locness_v2.1.bea19.tar.gz
tar -zxvf wi+locness_v2.1.bea19.tar.gz

errant_parallel -orig ABCN.dev.bea19.orig -cor output.txt -out hyp.m2
errant_compare -ref wi+locness/m2/ABCN.dev.gold.bea19.m2 -hyp hyp.m2
```

### BEA 19 test

```
zip output.zip output.txt
```

Then, upload `output.zip` to https://competitions.codalab.org/competitions/20228

## CoNLL 13 / CoNLL 14

```
wget -nc https://www.comp.nus.edu.sg/~nlp/conll13st/release2.3.1.tar.gz
tar -zxvf release2.3.1.tar.gz

wget -nc https://www.comp.nus.edu.sg/~nlp/conll14st/conll14st-test-data.tar.gz
tar -zxvf conll14st-test-data.tar.gz

wget https://www.comp.nus.edu.sg/~nlp/sw/m2scorer.tar.gz
tar zxvf m2scorer.tar.gz

python2 m2scorer/scripts/m2scorer.py conll13_output.txt release2.3.1/original/data/official-preprocessed.m2
python2 m2scorer/scripts/m2scorer.py conll14_output.txt conll14st-test-data/noalt/official-2014.combined.m2
```

## FCE valid / test

```
wget -nc https://www.cl.cam.ac.uk/research/nl/bea2019st/data/fce_v2.1.bea19.tar.gz
tar -zxvf fce_v2.1.bea19.tar.gz


grep '^S' < fce/m2/fce.dev.gold.bea19.m2 | cut -c 3- > fce.valid.src
grep '^S' < fce/m2/fce.test.gold.bea19.m2 | cut -c 3- > fce.test.src

errant_parallel -orig fce.valid.src -cor output.fce.valid.txt -out valid.hyp.m2
errant_compare -ref fce/m2/fce.dev.gold.bea19.m2 -hyp valid.hyp.m2

errant_parallel -orig fce.test.src -cor output.fce.test.txt -out test.hyp.m2
errant_compare -ref fce/m2/fce.test.gold.bea19.m2 -hyp test.hyp.m2
```

## JFLEG valid / test

```
git clone https://github.com/keisks/jfleg.git

python jfleg/eval/gleu.py -r jfleg/dev/dev.ref0 jfleg/dev/dev.ref1 jfleg/dev/dev.ref2 jfleg/dev/dev.ref3 -s jfleg/dev/dev.src --hyp output.txt
python jfleg/eval/gleu.py -r jfleg/test/test.ref0 jfleg/test/test.ref1 jfleg/test/test.ref2 jfleg/test/test.ref3 -s jfleg/test/test.src --hyp output.txt
```

