</br>
</br>

# Sentiment Analysis with NSMC and LSTM 😝
</br>

### 1. Crawling - get NAVER News data

 - Crawl article URL with NAVER Open API
 - Crawl article title and content with bs4 + selenium

### 2. KONLPY Stemmer

 #### 1-1. Development Environment

python 3.6
```
$conda create -n text_analysis python=3.6 anaconda
```
Install KoNLPy
```
$pip install konlpy
```
Install MeCab (optional)
```
$bash <(curl -s https://raw.githubusercontent.com/konlpy/konlpy/master/scripts/mecab.sh)
```

</br>

#### 1-2. KONLPY Stemmer Performance Comparison
: compare with Kkma, Komoran , Hannanum, Mecab, Okt(Twitter Morphological Analyzer)



  -> "Mecab" does a good job analyzing poorly spaced sentences. On the other hand, "hannanum" is
  barely categorized. 

  -> Misspellings make a big difference in the performance of stemming. 

  -> If you have a lot of typos, "komoran" is a better. 

  -> In the speed comparison, Kkma is the slowest and Mecab is significantly faster. Komoran and Hannanum are about the same speed.  
  Kkma < Komoran < okt < Hannanum < Mecab