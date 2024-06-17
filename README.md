I put code from various projects here, sometimes :worried:

```
Total Physical Source Lines of Code (SLOC) = 68,408

Totals grouped by language (dominant language first):
python:       38441 (56.19%)
sh:           22519 (32.92%)
fortran:       4752 (6.95%)
java:          2353 (3.44%)
ansic:          279 (0.41%)
perl:            64 (0.09%)

SLOC	Directory	SLOC-by-Language (Sorted)
15012   supernova-radiation-transfer sh=6124,fortran=4752,python=4136
9823    supernova-shock-breakout python=8132,sh=1691
8911    87a-nustar      sh=5804,python=3107
7891    87a-limits      python=5583,sh=2244,perl=64
6401    telescope-pipelines sh=6220,python=181
5421    astro-utils     python=4768,sh=374,ansic=279
4983    exoplanet-refraction python=4983
1944    supernova-absorption python=1944
1303    dota2-bot       java=1303
1200    amethyst        python=1188,sh=12
1108    mauve           python=1100,sh=8
1085    music-generator python=1085
1050    stm-postprocess java=1050
826     jupiter         python=826
417     neptune         python=399,sh=18
253     qrosswind       python=245,sh=8
252     lilac           python=252
170     orchid          python=162,sh=8
140     purpure         python=140
109     lavender        python=101,sh=8
109     tesla-valuation-model python=109
```

<!---
https://dwheeler.com/sloccount/
sloccount 87a-limits \
          87a-nustar \
          amethyst \
          astro-utils \
          dota2-bot \
          exoplanet-refraction \
          jupiter \
          lavender \
          lilac \
          mauve \
          music-generator \
          neptune \
          orchid \
          purpure \
          qrosswind \
          stm-postprocess \
          supernova-absorption \
          supernova-radiation-transfer \
          supernova-shock-breakout \
          telescope-pipelines \
          tesla-valuation-model
--->


# Useful Commands

## `pip freeze`
```
pip freeze > requirements.txt
```

## searching
```
grep -ri --include='*.py' --exclude-dir=.git --exclude-dir=__pycache__ --exclude-dir=.* "create_sample"
find . -type f -name '*.py' ! -path '*/__pycache__/*' ! -path '*/.*' -exec grep -i "latest_only" {} +
```

## A successful `sed`, note exclusion of hidden folders to prevent a `.git` distaster
```
find . \( -type d -name .git -prune \) -o -type f -a -name "*.py" -print0 | xargs -0 sed -i 's/cc\.WEIGHT_DECAY/self\.weight_decay/g'
grep -nr --include \*.sql "ANBI\." .
grep -nr --include \*.sql -E "[A-Z]{4}\." .
```

## Remove all notebook checkpoints
```
find . -name ".ipynb_checkpoints" -type d -exec rm -rf {} +
```

## Check encodings
```
for f in `find | egrep -v *.sql`; do echo "$f" ' -- ' `file -bi "$f"` ; done
```
## Convert encoding
```
iconv -f utf8 -t iso88591 umlaut-utf8.txt > umlaut-iso88591.txt
```

## Compress
```
tar -czvf out.tar.gz */out/*
```

## Replace "line feed" with "carriage return line feed"
```
CR=$(printf '\r')
find AF* -type f -exec sed -i "s/\$/$CR/" {} \;
```

## Usage of Python logging
```
logging.basicConfig(filename='example.log', encoding='utf-8', level=logging.DEBUG)
```
