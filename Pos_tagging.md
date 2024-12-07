#POS Tagging:
##Part of Speech tagging is used in text processing to avoid confusion between two same words that have different meanings. With respect to the definition and context, we give each word a particular tag and process them. Two Steps are used here:

Tokenize text (word_tokenize).
Apply the pos_tag from NLTK to the above step.
##Part of Speech Tagging with Stop words using NLTK in python

The Natural Language Toolkit (NLTK) is a platform used for building programs for text analysis. One of the more powerful aspects of the NLTK module is the Part of Speech tagging.
In order to run the below python program you must have to install NLTK. Please follow the installation steps. 
 

Open your terminal, run pip install nltk.
Write python in the command prompt so python Interactive Shell is ready to execute your code/Script.
Type import nltk
nltk.download()
A GUI will pop up then choose to download “all” for all packages, and then click ‘download’. This will give you all of the tokenizers, chunkers, other algorithms, and all of the corpora, so that’s why installation will take quite time. 

##Examples: 

import nltk
nltk.download()

*let’s knock out some quick vocabulary:*
Corpus : Body of text, singular. Corpora is the plural of this. 
Lexicon : Words and their meanings. 
Token : Each “entity” that is a part of whatever was split up based on rules.
In corpus linguistics, part-of-speech tagging (POS tagging or PoS tagging or POST), also called grammatical tagging or word-category disambiguation.
 

Input: Everything is all about money.
Output: [('Everything', 'NN'), ('is', 'VBZ'), 
          ('all', 'DT'),('about', 'IN'), 
          ('money', 'NN'), ('.', '.')] 
Here’s a list of the tags, what they mean, and some examples:
 


CC coordinating conjunction 
CD cardinal digit 
DT determiner 
EX existential there (like: “there is” … think of it like “there exists”) 
FW foreign word 
IN preposition/subordinating conjunction 
JJ adjective – ‘big’ 
JJR adjective, comparative – ‘bigger’ 
JJS adjective, superlative – ‘biggest’ 
LS list marker 1) 
MD modal – could, will 
NN noun, singular ‘- desk’ 
NNS noun plural – ‘desks’ 
NNP proper noun, singular – ‘Harrison’ 
NNPS proper noun, plural – ‘Americans’ 
PDT predeterminer – ‘all the kids’ 
POS possessive ending parent’s 
PRP personal pronoun –  I, he, she 
PRP$ possessive pronoun – my, his, hers 
RB adverb – very, silently, 
RBR adverb, comparative – better 
RBS adverb, superlative – best 
RP particle – give up 
TO – to go ‘to’ the store. 
UH interjection – errrrrrrrm 
VB verb, base form – take 
VBD verb, past tense – took 
VBG verb, gerund/present participle – taking 
VBN verb, past participle – taken 
VBP verb, sing. present, non-3d – take 
VBZ verb, 3rd person sing. present – takes 
WDT wh-determiner – which 
WP wh-pronoun – who, what 
WP$ possessive wh-pronoun, eg- whose 
WRB wh-adverb, eg- where, when


Text may contain stop words like ‘the’, ‘is’, ‘are’. Stop words can be filtered from the text to be processed. There is no universal list of stop words in nlp research, however the nltk module contains a list of stop words. 
You can add your own Stop word. Go to your NLTK download directory path -> corpora -> stopwords -> update the stop word file depends on your language which one you are using. Here we are using english (stopwords.words(‘english’)).
 

Python
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
stop_words = set(stopwords.words('english'))
 
// Dummy text
txt = "Sukanya, Rajib and Naba are my good friends. " \
    "Sukanya is getting married next year. " \
    "Marriage is a big step in one’s life." \
    "It is both exciting and frightening. " \
    "But friendship is a sacred bond between people." \
    "It is a special kind of love between us. " \
    "Many of you must have tried searching for a friend "\
    "but never found the right one."
 
# sent_tokenize is one of instances of 
# PunktSentenceTokenizer from the nltk.tokenize.punkt module
 
tokenized = sent_tokenize(txt)
for i in tokenized:
     
    # Word tokenizers is used to find the words 
    # and punctuation in a string
    wordsList = nltk.word_tokenize(i)
 
    # removing stop words from wordList
    wordsList = [w for w in wordsList if not w in stop_words] 
 
    #  Using a Tagger. Which is part-of-speech 
    # tagger or POS-tagger. 
    tagged = nltk.pos_tag(wordsList)
 
    print(tagged)
Output: 
 

[('Sukanya', 'NNP'), ('Rajib', 'NNP'), ('Naba', 'NNP'), ('good', 'JJ'), ('friends', 'NNS')]
[('Sukanya', 'NNP'), ('getting', 'VBG'), ('married', 'VBN'), ('next', 'JJ'), ('year', 'NN')]
[('Marriage', 'NN'), ('big', 'JJ'), ('step', 'NN'), ('one', 'CD'), ('’', 'NN'), ('life', 'NN')]
[('It', 'PRP'), ('exciting', 'VBG'), ('frightening', 'VBG')]
[('But', 'CC'), ('friendship', 'NN'), ('sacred', 'VBD'), ('bond', 'NN'), ('people', 'NNS')]
[('It', 'PRP'), ('special', 'JJ'), ('kind', 'NN'), ('love', 'VB'), ('us', 'PRP')]
[('Many', 'JJ'), ('must', 'MD'), ('tried', 'VB'), ('searching', 'VBG'), ('friend', 'NN'), 
('never', 'RB'), ('found', 'VBD'), ('right', 'RB'), ('one', 'CD')]
Basically, the goal of a POS tagger is to assign linguistic (mostly grammatical) information to sub-sentential units. Such units are called tokens and, most of the time, correspond to words and symbols (e.g. punctuation)
