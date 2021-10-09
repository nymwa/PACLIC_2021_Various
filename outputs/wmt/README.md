# WMT

## how to score

```
sacremoses -l en detokenize < deen.txt | sacrebleu -t wmt14/full -l de-en
sacremoses -l de detokenize < ende.txt | sacrebleu -t wmt14/full -l en-de

sacremoses -l en detokenize < fien.txt | sacrebleu -t wmt17 -l fi-en
sacremoses -l fi detokenize < enfi.txt | sacrebleu -t wmt17 -l en-fi

sacremoses -l en detokenize < fren.txt | sacrebleu -t wmt14/full -l fr-en
sacremoses -l fr detokenize < enfr.txt | sacrebleu -t wmt14/full -l en-fr

sacremoses -l en detokenize < lven.txt | sacrebleu -t wmt17 -l lv-en
sacremoses -l lv detokenize < enlv.txt | sacrebleu -t wmt17 -l en-lv
```

