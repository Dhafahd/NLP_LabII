### MST AIDS 2023-2024 (Département Génie Informatique)
**Subject : The main purpose behind this lab is to get familiar with ule-based techniques, Regex, and NLP Word Embedding.**\
**Realize by : Chibani Fahd.**\
**web source : Aljarida24r.**\
**Course : NLP.**\

## 1. Introduction
In this lab, our primary objective is to acquaint ourselves with NLP's Rule-based techniques, Regex, and NLP Word Embedding. Through hands-on exploration, we aim to gain proficiency in these essential aspects of Natural Language Processing, enabling us to understand and apply them effectively in various contexts.
## 2. Upload data from MongoDB Database
In this section, we accessed our MongoDB database to upload stored data. This data was gathered by scraping content from the Aljarida24 website, 
## 3. Rule Based NLP and Regex
Imagine a scenario where a business needs a streamlined way to generate bills from raw text provided by customers. In such cases, employing Python code with Regex capabilities can be invaluable. By utilizing Regex patterns, Python scripts can effectively extract relevant information such as item names, quantities, and prices from unstructured text. This enables businesses to automate the bill generation process, saving time and reducing errors.
### 3.1 Data pre-procecing 
Our workflow commences with the essential task of text refinement, focusing on the removal of stop words and adjectives such as 'new,' 'cool','fresh'... from the bill text. This meticulous cleansing is pivotal in simplifying the subsequent regex pattern matching process. By eliminating these unnecessary elements, we enhance the text's suitability for regex pattern matching, enabling more efficient and accurate extraction of relevant information. This initial cleaning phase optimizes the text for seamless integration into regex-based algorithms
```python
Before cleaning : ['I bought three hundred two thousand twenty seven Samsung smartphones 150,333 $ each and four kilos of fresh banana for 2,4 dollar a kilogram']
After cleaning : ['bought three hundred two thousand twenty seven Samsung smartphones 150,333 $ four kilos banana 2,4 dollar kilogram']
```
### 3.2 Regex pattern :
fter meticulously cleaning our text by removing extraneous elements such as stop words and adjectives, we proceed to employ regex for pattern matching. Utilizing regex, we define a pattern with three groups: the first capturing the price, the second identifying the product name, and the third representing the unit price. This systematic approach enables us to efficiently extract relevant information from the text and generate the bill.
```python
 pattern = r"((?:" + '|'.join(numbers) + r"|\d)(?:\s(?:" + '|'.join(numbers) + r"|\d|and))*)(.*?)(\d+[\.|\,]?\d*)\b\s*(\$|dollar)"
```
To convert textual numbers into their numerical values, we create a Python script (Word2num.py File )capable of intelligently parsing numbers up to 999,999,999,999. This script efficiently take the sentence, identifies numerical representations, and transforms them into their corresponding numeric values. 

## 4.  word Embedding :
To better understand word embedding in Arabic text, we attempt to apply it to the paragraphs that we scraped in Lab 1.
## 4.1. one hot encoding :
One-hot encoding is a technique used in machine learning to represent categorical data numerically. Each category is represented as a binary vector, where only one bit is activated (set to 1) for the corresponding category, and all other bits are set to 0.
```python
Sentence : ['طالب نواب المعارضة البرلمانية']
binary representation : [[1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], [0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]]
```
## 4.2. bag of words :
The Bag of Words model represents text by counting the occurrence of words without considering grammar or order, forming a sparse numerical matrix used in various natural language processing tasks.
```python
Sentence : ['طالب نواب المعارضة البرلمانية']
Our vocabulary :{'طالب': 60, 'نواب': 72, 'المعارضة': 30, 'البرلمانية': 16, 'بالكشف': 42, 'سبل': 57, 'تيسير': 50, 'الحصول': 19, 'الدعم': 20, 'الاجتماعي': 10, 'المباشر': 29, 'ظهور': 61, 'عدد': 62, 'الاشكاليات': 14, 'ووجه': 83, 'إدريس': 5, 'السنتيسي': 21, 'رئيس': 53, 'الفريق': 27, 'الحركي': 18, 'بمجلس': 46, 'النواب': 37, 'فوزي': 64, 'لقجع': 67, 'الوزير': 39, 'المنتدب': 34, 'المكلف': 33, 'بالميزانية': 43, 'سؤالا': 55, 'كتابيا': 66, 'مفاده': 70, 'سحب': 58, 'المواطنين': 36, 'شروعهم': 59, 'الاستفادة': 12, 'وأكد': 74, 'سؤاله': 56, 'العديد': 25, 'المواطنات': 35, 'والمواطنين': 76, 'فوجئوا': 63, 'بسحب': 44, 'ومعها': 82, 'نظام': 71, 'أمو': 2, 'تضامن': 48, 'الشروع': 23, 'أشهر': 1, 'الأمر': 8, 'أثار': 0, 'امتعاض': 40, 'الفئات': 26, 'المعنية': 31, 'تقرر': 49, 'إبعادها': 4, 'البرنامج': 17, 'بمبرر': 45, 'ارتفاع': 6, 'مؤشرهم': 69, 'رغم': 54, 'أنه': 3, 'يمكن': 84, 'تتغير': 47, 'وضعيتهم': 79, 'الاجتماعية': 11, 'والاقتصادية': 75, 'الظرف': 24, 'الوجيز': 38, 'وساءل': 78, 'حقيقة': 51, 'الإجراء': 9, 'وأسبابه': 73, 'ودوافعه': 77, 'وعدد': 80, 'المعنيين': 32, 'وكذا': 81, 'انعكاساته': 41, 'الأشخاص': 7, 'قدرة': 65, 'الانخراط': 15, 'الشامل': 22, 'للأشخاص': 68, 'القادرين': 28, 'دفع': 52, 'الاشتراكات': 13}
BoW representation : [[0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 0]]
```
## 4.3. TF-IDF :
TF-IDF (Term Frequency-Inverse Document Frequency) measures word importance in a document by considering both the frequency of the term within the document and its rarity across the entire document collection, aiding in tasks like text mining and information retrieval.
```python
Sentence : ['طالب نواب المعارضة البرلمانية']
Our vocabulary :'['أثار' 'أشهر' 'أمو' 'أنه' 'إبعادها' 'إدريس' 'ارتفاع' 'الأشخاص' 'الأمر''الإجراء' 'الاجتماعي' 'الاجتماعية' 'الاستفادة' 'الاشتراكات' 'الاشكاليات''الانخراط' 'البرلمانية' 'البرنامج' 'الحركي' 'الحصول' 'الدعم' 'السنتيسي''الشامل' 'الشروع' 'الظرف' 'العديد' 'الفئات' 'الفريق' 'القادرين' 'المباشر''المعارضة' 'المعنية' 'المعنيين' 'المكلف' 'المنتدب' 'المواطنات''المواطنين' 'النواب' 'الوجيز' 'الوزير' 'امتعاض' 'انعكاساته' 'بالكشف''بالميزانية' 'بسحب' 'بمبرر' 'بمجلس' 'تتغير' 'تضامن' 'تقرر' 'تيسير''حقيقة' 'دفع' 'رئيس' 'رغم' 'سؤالا' 'سؤاله' 'سبل' 'سحب' 'شروعهم' 'طالب''ظهور' 'عدد' 'فوجئوا' 'فوزي' 'قدرة' 'كتابيا' 'لقجع' 'للأشخاص' 'مؤشرهم''مفاده' 'نظام' 'نواب' 'وأسبابه' 'وأكد' 'والاقتصادية' 'والمواطنين''ودوافعه' 'وساءل' 'وضعيتهم' 'وعدد' 'وكذا' 'ومعها' 'ووجه' 'يمكن']
TFIDF representation : [[0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.5 0. 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.5 0.  0.  0.  0.  0. 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.
  0.  0.  0.  0.  0.  0.  0.  0. 0.  0.  0.  0.  0.  0.  0.5 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0. 0.5 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0. ]]
```
## 4.4. one hot encoding :
## 4.5. one hot encoding :








### 3.2 Removing punctuation
Removing punctuation is a crucial step in the NLP pipeline as it cleans the text, reducing unnecessary computation. However, Arabic has some special characters for punctuation, such as the comma `،` and quotes `”`, which is why I included an Arabic punctuation string to handle punctuation removal.
```python
ar_punct = ''')(+`÷×؛<>_()*&^%][ـ،/:"؟.,'{}~¦+|!”،.”…“–ـ”.'''
```
Here's an example for punctuation removal:
```python
Tokenized text with punctuation : ['ومقارنها', 'بالسنة', 'الماضية', '،']
Tokenized text without punctuation: ['ومقارنها', 'بالسنة', 'الماضية']
Sentence tokenized text with punctuation: ['ومقارنها بالسنة الماضية،']
Sentence tokenized text without punctuation: ['ومقارنها بالسنة الماضية']
```









### 3.3 Removing stopwords
Stopwords reomval saves computation and keeping them doesn't provide much information in the NLP process, that's why it is recommended to eliminate them. Removing them is a simple process, simlified by the `NLTK` library which includes a corpus for Arabic stopwords.
Here's an example of the output:
```python
Tokenized text with stopwords: ['في', 'افتتاحية', 'النشرة', 'الفصلية', 'الأولى', 'ضمان', 'الاستثمار', 'لسنة', '2024']
Tokenized text without stopwords: ['افتتاحية', 'النشرة', 'الفصلية', 'الأولى', 'ضمان', 'الاستثمار', 'لسنة', '2024']
Sentence tokenized text with stopwords: 'في افتتاحية النشرة الفصلية الأولى ضمان الاستثمار لسنة 2024'
Sentence tokenized text without stopwords: [' افتتاحية النشرة الفصلية الأولى ضمان الاستثمار لسنة 2024']
```
### 3.4 Converting numbers to Arabic words
Converting numbers to Arabic words is an optional step in this pipeline as they are considered as stopwords. Due to this, I deleted them from the token list even though I had converted them from numbers to Arabic word numbers.\
```python
number in token list : ['2023']
number in words in the token list : ['ألفان و ثلاث و عشرون']
```
### 3.5 Normalization
Normalization in Arabic differs from other languages it includes diacritization, stripping tatweel, normalizing Hamza (e.g. `أ` to `ء`), normalizing Lam Alef, normalizing Teh Marbuta and Alef Maksura.\
Here's an example of the output:
```python
Original token list: ['العربية', 'مؤشري']
Normalized token list: ['العربيه', 'مءشري']
```
## 4. Stemming
Stemming is an important step, it provides the root of a word but can sometimes give words without meaning (e.g. stem of `وكاله` is `ال`), this problem persists even in Arabic NLP. I chose to use an Arabic stemmer from the `tashaphyne`[[2]](#2) library.\
Here's an example of the output:
```python
Origial token list: ['العربيه', 'مءشري', 'فيتش']
Stemmed token list: ['عربيه', 'مءشر', 'تش']
```
## 5. Lemmatization
Lemmatization is similar to stemming but provides more meaningful words (e.g. lemma of `الشركات` is `شركة`) which may be useful in use cases where meaning is important. However, lemmatizers are more computationally expensive than stemmers. I chose to use an Arabic lemmatizer from the `qalsadi`[[3]](#3) library.\
Here's an example of the output:
```python
Origial token list: ['الشركات', 'متعدده', 'الجنسيات', 'ومءسسات']
Lemmatized token list: ['شركة', 'متعدد', 'جنس', 'ومءسسات']
```
## 6. Stemming and lemmatization comparison
As mentioned before, the key difference between Stemming and lemmatization is that lemmatizers provide more meaningful roots of words. However lemmatizers are computationally expensive, and we can see the difference even in our small use case (300-500 words/article). In addition, if we thoroughly search through the lemmatized token list, we can notice the difference in word meaning between stemming and lemmatization.
## 7. PoS Tagging
PoS tagging is a process where we tag words with their particular part of speech (adverb, adjective, verb, etc.). Research done in English PoS tagging is quite advanced compared to Arabic, Arabic is quite a complex language and little research was done in this field, however, we'll try to provide two approaches to solve this problem.
### 7.1 ML approach
Creating a model for PoS tagging is quite a difficult a task to do, especially with the lack of datasets to train the model and the huge number of words in the Arabic language, which is why I sticked to using the `Farasa` [[4]](#4) library. This is a `Java` package in origin, but it has a Python wrapper. We'll stick to using this tagger on the original text because it takes 30+ minutes to use on the token list and we can see that the library is fairly heavy from the way it calls the jars each time.\
The PoS tagger seems quite accurate, let's see an example of the output:
```python
Tagged text: عن/PREP حلول/NOUN-FP ال+ مغرب/DET+NOUN-MS
```
### 7.2 RegEx approach
The Arabic language is quite a complex language with a huge number of patterns for verbs, nouns, adjectives, etc..., with some words not necessarily having patterns and others changing meaning if tashkeel changes [[5]](#5). However I tried to develop a small regex PoS tagger from the rules provided by Mr. Hjouj [[6]](#6), the tagger is simple, as it only has NOUN and VERB classes. the Arabic letters had to be converted to their ascii to be implemented in the regex pattern matcher, to extract the *Awzan* and patterns. The Tagger was given the lemmatized token list because of the advantages that lemmatization provides.\
In conclusion, after some evaluation the tagger seems to be not that accurate, however, it does get some words correctly tagged, especially for the ones that follow the patterns that it was supposed to handle.\
Here's an example of the output:
```python
Lemmatized token list: ['عالم', 'دول', 'العربيه', 'مءشري', 'فيتش']
Custom POS Tagged: ['NOUN', 'VERB', 'VERB', 'VERB', 'NOUN']
```
## 8. Named Entity Recognition
We finally applied the NER Tagger by `Ferasa`, I should note that the `Ferasa NER Tagger` is quite heavy on the machine.
However, it seems to be accurate in detecting entities in the text.\
Here's an example of the output:
```python
NER Tagged text: 'أعلنت/O المؤسسة/B-ORG العربية/I-ORG لضمان/I-ORG الاستثمار'
```
## 9. What I learned
To conclude what I have learned during this Lab, is that Arabic is far more complex than its Latin counterparts, tashkeel plays a huge role in determining the meaning of a word, also handling Arabic text seems to be quite tedious, in addition, the lack of research done in the field of Arabic NLP, consequently, the libraries for Arabic NLP seem to be quite limited and small in number.
## 10. References
<a id="1">[1]</a> Zerrouki, T., (2023). PyArabic: A Python package for Arabic text. Journal of Open Source Software, 8(84), 4886, https://doi.org/10.21105/joss.04886 \
<a id="2">[2]</a> Alkhatib, R. M., Zerrouki, T., Shquier, M. M. A., & Balla, A. (2023). Tashaphyne0.4: A new Arabic light stemmer based on rhizome modeling approach. Information Retrieval Journal, 26(14). doi: https://doi.org/10.1007/s10791-023-09429-y \
<a id="3">[3]</a> T. Zerrouki, Qalsadi, Arabic morphological analyzer Library for python.,  https://pypi.python.org/pypi/qalsadi/ \
<a id="4">[4]</a> MagedSaeed. (n.d.). GitHub - MagedSaeed/farasapy: A Python implementation of Farasa toolkit. GitHub. https://github.com/MagedSaeed/farasapy?tab=readme-ov-file#want-to-cite \
<a id="5">[5]</a> Sawalha, M., Atwell, E., & Abushariah, M. A. M. (2013). SALMA: Standard Arabic Language Morphological Analysis. 2013 1st International Conference on Communications, Signal Processing, and Their Applications (ICCSPA). https://doi.org/10.1109/iccspa.2013.6487311 \
<a id="6">[6]</a> Hjouj, M., Alarabeyyat, A., & Olab, I. (2016). Rule-based approach for Arabic part of speech tagging and name entity recognition. International Journal of Advanced Computer Science and Applications, 7(6). https://doi.org/10.14569/ijacsa.2016.070642
