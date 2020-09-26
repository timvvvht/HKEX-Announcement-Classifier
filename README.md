# HKEx Announcement Classifier

HKEx Announcement Classifier is a project on data exploration, analysis and finally training a recurrent neural network (RNN) to ~93% validation accuracy to classify disclosure announcements submitted by listed companies on the Hong Kong Stock Exchange (HKEx).

![Image of Prediction](/images/prediction.png)

In this project, I scraped data corresponding to 6 types of announcements, namely:

(1) Trading Halt; 

(2) Notifiable Transactions; 

(3) Connected Transactions; 

(4) Announcement of Annual Results; 

(5) Notice of Annual General Meeting; and 

(6) Takeover Offers.

# Motivation 
The ability to accurate identify categories of legal text data is an immensely useful building block for legaltech or quantitative trading applications. 

For example: 
- Accurately classifying legal texts can help lawyers drastically increase their efficiency in AI-assisted legal due diligence. 
- The ability to classify important disclosure announcements on different stock exchanges is incredibly useful in news-based quantitative trading algorithms. 

# Future Implementations
The types of data can, in a future iteration of this project, include different types of contracts such as loan agreements, lease agreements, joint venture agreements, so on and so forth. The scope of jurisdiction can easily extend beyond Hong Kong, such as to include offshore jurisdictions (British Virgin Islands, Cayman Islands etc.) and international trading hubs (US, UK, EU, China) for a more powerful legal text classifier. 

# Data Exploration and Analysis
Includes bi-gram analysis and average word count analysis across different types of announcements. The implementation and markdown write-up can be found <a href='Data%20Exploration%20for%20HKEX%20Announcements.ipynb'>here</a>.

## Bigram Analysis
**Bigrams for Announcements of Annual General Meetings:**
![Image of AGM Bigrams](/images/bigrams_agm.png)

**Bigrams for Announcements of Annual Results:**
![Image of AR Bigrams](/images/bigrams_ar.png)

**Bigrams for Announcements of Trading Halts:**
![Image of TH Bigrams](/images/bigrams_th.png)

**Bigrams for Announcements of Connected Transactions:**
![Image of CT Bigrams](/images/bigrams_cct.png)

**Bigrams for Announcements of Notifiable Transactions:**
![Image of NT Bigrams](/images/bigrams_nt.png)

**Bigrams for Announcements of Takeover Offers:**
![Image of TK Bigrams](/images/bigrams_tk.png)

## Analysis of Mean Word Count across Announcements
![Image of MWC](/images/word_count_comparison.png)

# Training a Recurrent Neural Network 
I implemented a recurrent neural network with a bidirectional LSTM layer after an embedding layer using pre-trained GloVe embeddings of 300 dimensions. The details of my implementation can can be found <a href='HKEX_Announcement_Classifier.ipynb'>here</a>.

The model architecture is as follows: 
![Image of Model](/images/model.png)

The trained neural network was able to accurately classify 93.55% of announcements in the validation set and it was able to accurately identify new announcements on the HKEx, provided that the categories of such announcements were within the training data. 

# Improving the Model 
Further improvements on the model would include more data from different jurisdictions, and from different types of legal documents, so as to create a more general and more accurate legal text classifier.

