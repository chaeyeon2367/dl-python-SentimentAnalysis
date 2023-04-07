</br>
</br>

# Sentiment Analysis with NSMC and LSTM 😝
</br>

## 1. Crawling - get NAVER News data

 - Crawl article URL with NAVER Open API
 - Crawl article title and content with bs4 + selenium

</br>

## 2. KONLPY Stemmer

 ### 1-1. Installing the requirements

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
Install Gensim for topic modeling
```
$pip install gensim
$conda install -c conda-forge gensim
```

KoNLPy Webpage: https://konlpy.org/en/latest/install/#id1

</br>

 ### 1-2. KONLPY Stemmer Performance Comparison
: compare with Kkma, Komoran , Hannanum, Mecab, Okt(Twitter Morphological Analyzer)



  -> "Mecab" does a good job analyzing poorly spaced sentences. On the other hand, "hannanum" is
  barely categorized. 

  -> Misspellings make a big difference in the performance of stemming. 

  -> If you have a lot of typos, "komoran" is a better. 

  -> In the speed comparison, Kkma is the slowest and Mecab is significantly faster. Komoran and Hannanum are about the same speed.  
  Kkma < Komoran < okt < Hannanum < Mecab


</br>

## 3. Topic Modeling 

### 1.1 Definition

 - The process of finding topics (keywords) in an article
 - The process of finding a "set of k words" from a combination of words that make up a document (sentence).
 - It is a Bayesian probability model, and the result of topic modeling is the probability that each word belongs to each topic. 


### 1.2 History 

- LSI (Latent Semantic Indexing): 
  - SVD on the document word matrix. 
  - Vectors converted to low dimensions by SVD represent the semantics.

- pLSA (Probabilistic Latent Semantic Analysis) 
  - keeps the document-word matrix in place
  - Representation based on probability of occurrence, not frequency per document

- LDA (Latent Dirichlet Allocation)
  - Utilize the Dirichlet distribution
  - In this project, using LDA for Topic Modeling

  - Model Assumptions in LDA

    - Each document can contain multiple topics. 

    - Each topic can contain multiple words. 

    - Every word that exists in a document is necessarily contained in some topic. 

    - The process of human writing is defined as a generative model. 

  - LDA Model Process 

    1. Select the topics to be used in the documents. (K topics)

    2. Select a topic from one of the topics. 

    3. select one of the words in that topic. 

    4. add the word to the document (write).

    5. Repeat from step 2. 

</br>

## 4. NSMC Sentiment Analysis 

  ### 1-1. NSMC (Naver Sentiment Movie Corpus v1.0) 
   - url : https://github.com/e9t/nsmc
   - size : 19MB
   - Data source: Naver
   - No more than 100 140 ratings (reviews) per movie
   - Total 200,000 reviews (sampled from 640,000 collected)
      - 'ratings_train.txt : 150,000 , 'ratings_test.txt : 50,000
      - Equally sampling the percentage of positive/negative reviews (i.e. random guess yields 50% accuracy)
      - Does not include neutral reviews

