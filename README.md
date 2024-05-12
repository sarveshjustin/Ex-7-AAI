
## Implementation of Text  Summarization
### Aim: 
To perform automatic text summarization using Natural Language Processing (NLP) techniques. 

### Algorithm:
#### Step 1 
Import necessary libraries for natural language processing tasks.
#### Step 2: 
Download NLTK resources, including the punkt tokenizer and stopwords.
#### Step 3: 
Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.
#### Step 4: 
Define the Text Summarization Function using a simple frequency-based approach.
    - Calculate the frequency of each word in the preprocessed text.
    - Calculate a score for each sentence based on the sum of word frequencies.
    - Select the top N sentences with the highest scores to form the summary.
#### Step 5: 
Construct the main program to read the paragraph  and perform text summarization
      - Generate and print the original text.
      - Generate and print the text summary using the  Text Summarization function
### Program:
~~~
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize,sent_tokenize
from nltk.stem import PorterStemmer
nltk.download( 'punkt' )
nltk.download( 'stopwords' )

def preprocess_text(text):
	# Tokenize the text into words
	words = word_tokenize(text)
	# Remove stopwords and punctuation
	stop_words= set(stopwords.words( 'english'))
	filtered_words= [word for word in words if word. lower() not in stop_words and word.isalnum()]

	# Stemming
	stemmer = PorterStemmer()

	stemmed_words= [stemmer. stem(word) for word in filtered_words]
	return stemmed_words

def generate_summary(text,num_sentences=3):
	sentences= sent_tokenize(text)
	preprocessed_text = preprocess_text(text)
	# Calculate the frequency of each word
	word_frequencies =nltk. FreqDist (preprocessed_text)

	# Calculate the score for each sentence based on word frequency
	sentence_scores ={}
	for sentence in sentences:
		for word, freq in word_frequencies.items():
			if word in sentence.lower():
				if sentence not in sentence_scores:
					sentence_scores[sentence] = freq
				else:
					sentence_scores[sentence]+= freq
	# Select top N sentences with highest scores
	summary_sentences= sorted(sentence_scores, key=sentence_scores.get,reverse=True) [ : num_sentences]

	return ' '. join(summary_sentences)

if __name__=="__main__":
	input_text ="""
	Natural language processing (NLP) is a subfield of artificial intelligence.
	It involves the development of algorithms and models that enact NLP.
	NLP is used in various applications, including chatbots, language Understanding, and language generation.
	This program demonstrates a simple text summarization using NLP"""
summary = generate_summary(input_text)
print("Origina1 Text: ")
print (input_text )
print( " \nSummary : " )
print(summary)

~~~

### Output
![image](https://github.com/21005984/Ex-7-AAI/assets/94748389/6bdb0c81-1f8b-4826-83f2-31b8addf7459)

### Result:
Thus ,the program to perform the Text summarization is executed sucessfully.


