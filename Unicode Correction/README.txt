Assumptions:

Characters like क्ष are not available in unicode, and are instead read as क्‍ष i.e. combination of क and ष.

ं, the anusvar character doesnt have a vowel counterpart in unicode, but it exists in marathi so, ं is being replaced by अं 

Since, no consonant can be complete as क = क् + अ. So, all the unicode corrected words are in the format as follows हलंत = ह अ ल अं त अ. 

It is to be understood that all these consonants are with halant (्).

While calculating syllables, if a consonant is having 2 vowels eg. मांडवळ, here म आ अं  will be considered one syllable.

Output of questions requiring token frequencies are put in the unicode corrected format.

Input to the notebooks for question 4 is the "pped_txt.txt" file which is preprocessed by removing all non-marathi characters from there.

Since the wording was not clear, both the frequencies of characters and syllables in tokens only and whole corpus are put in their files.
_______________________________________________________________
How to run:

The python notebooks for each question are present inside the respective folders.

For question 4, there is a different notebook for each model.

In those notebooks, change the filepaths accordingly. Preferably, use google colab to run the notebooks.

Each notebook also contains the code for question 5, so each model will also run the text from q3 present in "q3.txt".

The notebooks will output txt files for bigram_tokens, unigram_tokens, bigram_characters, bigram_syllables and the metrics file for Q5.

The files with vocab_size, max_length differences will also be produced.
________________________________________________________________

Q.2

unigram_syllables

तअ : 639124
रअ : 615485
अं : 514062
आ : 497840
नअ : 421269
वअ : 366043
सअ : 364500
पअ : 303356
लअ : 292975
अ : 288520
मअ : 285366
कआ : 283541
लआ : 249552
यआ : 235705
नआ : 213585
हए : 212887
वआ : 198987
रआ : 191237
सआ : 186849
लए : 180708

bigram_syllables

आहए : 169576
आणइ : 81495
वअरअ : 69974
अंनई : 65862
यआअं : 65362
तअरअ : 58460
असअ : 54232
सआठई : 50482
अंनआ : 50020
अंचयआ : 49709
मअधयए : 44539
कआरअ : 44472
तईलअ : 43775
नआहई : 42357
तयआअं : 41298
करअणयआ : 35670
णयआतअ : 34146
हएतअ : 32537
आपअ : 32412
कआअं : 30573

unigram_characters

अ : 6291674
आ : 4599084
र : 1917797
ए : 1768964
त : 1626666
य : 1437596
ई : 1428993
क : 1317338
ल : 1165316
न : 1122360
स : 1065723
व : 1002441
इ : 990454
म : 863970
ह : 840999
अं : 840690
प : 786570
च : 745553
ण : 582253
द : 537860

bigram_characters

यआ : 962736
रअ : 943328
तअ : 715221
अर : 609157
नअ : 476794
सअ : 473396
वअ : 427721
आर : 387314
आअ : 352184
पअ : 336892
मअ : 336017
लअ : 331151
अत : 329216
अक : 321767
आह : 321146
आत : 318496
अल : 315511
यअ : 303867
अण : 303468
कआ : 293937
_____________________________________________________

Q.6

From comparing the ground truths with the tokenizers, we get the following statistics.

Average Precision(best to worst): whitespace(36.98%), unigram_no_limit(13.71%), unigram_2k(8.66%), BPE_2k(5.06%), BPE_1k(2.85%), mbert(2.03%), indicbert(0.68%)

Average Recall(best to worst): whitespace(52.13%), unigram_no_limit(29.12%), unigram_2k(22.84%), BPE_2k(14.32%), BPE_1k(9.32%), mbert(7.18%), indicbert(1.52%)

Average f_score(best to worst): whitespace(42.98), unigram_no_limit(18.52), unigram_2k(12.47), BPE_2k(7.44), BPE_1k(4.35), mbert(3.15), indicbert(0.93)

From this, we can say that though naive, the whitespace tokenizer performs better when trying to encounter word groups. 
But, it will only perform better when the word groups are closer to length 1.
So, for complex or more word groups, it will not be that great.

BPE on the other hand, would peform better than the current performance with more vocabulary size and a bigger corpus, as it will cover more and more common terms.

Advanced models like mbert and indicbert, while performing better on other tasks which require smaller tokens. The result for tokenizing word groups is really poor.

All these models, still arent geared toward promoting word groups as tokens.
______________________________________________________