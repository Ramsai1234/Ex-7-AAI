<H3>NAME : P Ramsai</H3>
<H3>REGISTER NO : 212221240041 </H3>
<H3>EX. NO.7</H3>
<H3>DATE: 28/4/2024</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim: </H3> 
 to perform automatic text summarization using Natural Language Processing (NLP) techniques.
 <BR>
<h3>Algorithm:</h3>
Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>

```
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer

nltk.download('punkt')
nltk.download('stopwords')

def preprocess_text(text):
  words = word_tokenize(text)
  stop_words = set(stopwords.words('english'))
  filtered_words = [word for word in words if word.lower() not in stop_words and word.isalnum()]

  stemmer = PorterStemmer()
  stemmer_words=[stemmer.stem(word) for word in filtered_words]

  return stemmer_words


def generate_summary(text,num_sentences=3):
  sentences = sent_tokenize(text)

  preprocessed_text = preprocess_text(text)

  word_frequencies = nltk.FreqDist(preprocessed_text)

  sentence_scores = {}

  for sentence in sentences:
    for word, freq in word_frequencies.items():
      if word in sentence.lower():
        if sentence not in sentence_scores:
          sentence_scores[sentence] = freq
        else:
          sentence_scores[sentence] +=freq

  summary_sentences = sorted(sentence_scores, key=sentence_scores.get, reverse =True)[:num_sentences]
  return ' '.join(summary_sentences)

if __name__ == "__main__":
  input_text = "hi 
i am ramsai from aiml dept.
i need to develop some applications and websites which are useful to the people.
applications can be develop in android and ios.
websites are useful to companies and managements."
  summary = generate_summary(input_text)
  print("Original Text :")
  print(input_text)

  print("\nSummary")
  print(summary)



```
<H3>Output</H3>


![image](https://github.com/Ramsai1234/Ex-7-AAI/assets/94269989/c32341a6-1e7d-420d-8e32-ebb5f9022d05)

<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.
