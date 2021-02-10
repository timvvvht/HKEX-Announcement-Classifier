# HKEx Announcement Classifier

HKEx Announcement Classifier is a project on data exploration, analysis and finally training a recurrent neural network (RNN) to ~93-94% validation accuracy to classify disclosure announcements submitted by listed companies on the Hong Kong Stock Exchange (HKEx). **Jan 2021 Update**: The transformer architecture is unreasonably effective - not only surpassing the validation accuracy of RNN, but also requiring far fewer parameters.

<img src="/images/prediction.png" width="600">

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
The types of data can, in a future iteration of this project, include different types of contracts such as loan agreements, lease agreements, joint venture agreements, so on and so forth. The scope of jurisdiction can easily extend beyond Hong Kong, such as to include offshore jurisdictions (British Virgin Islands, Cayman Islands etc.) and international stock exchanges (e.g. NYSE, NASDAQ, LSE) for a more powerful legal text classifier. 

# Data Exploration and Analysis
Includes bi-gram analysis and average word count analysis across different types of announcements. The implementation and markdown write-up can be found <a href='Data%20Exploration%20for%20HKEX%20Announcements.ipynb'>here</a>.

## Bigram Analysis
**Bigrams for Announcements of Annual General Meetings:**
![Image of AGM Bigrams](/images/bigrams_agm.png)

No surprise here, that the bigrams "general meeting" and "annual general" are the most frequent ones for this category.

**Bigrams for Announcements of Annual Results:**
![Image of AR Bigrams](/images/bigrams_ar.png)

Announcements of Annual Results is related to bigrams such as "31 december" or "year ended" as they signify the end of the year.

**Bigrams for Announcements of Trading Halts:**
![Image of TH Bigrams](/images/bigrams_th.png)

As for this type of announcement, the most common bigrams are words that are common across *any* types of announcement, which is an observation in line with the relatively shorter length of Trading Halt announcements as we shall see below.

**Bigrams for Announcements of Connected Transactions:**
![Image of CT Bigrams](/images/bigrams_cct.png)

As we can see above, the bigram "chapter 14a" is the 5th most common bigram in the 'Connected Transactions' dataset. Given my experience representing listed companies in Hong Kong legally, I am aware that 'Connected Transactions' are governed by Chapter 14A of the Listing Rules of the Stock Exchange.

**Bigrams for Announcements of Notifiable Transactions:**
![Image of NT Bigrams](/images/bigrams_nt.png)

'Notifiable Transactions' usually involve mergers and acquisitions, so seeing the bigram "target company" in 4th place is not too surprising. The bigrams "percentage ratios" and "applicable percentage" relate to the requirement for companies to publish these types of announcements only when the proposed transactions meet a certain percentage threshold of equity transfer in the transactions.

**Bigrams for Announcements of Takeover Offers:**
![Image of TK Bigrams](/images/bigrams_tk.png)

Takeover offers are governed by the Takeovers Code, as expected.

## Analysis of Mean Word Count Across Announcements
![Image of MWC](/images/word_count_comparison.png)

Annual results occupy the number 1 spot in terms of length of announcement. This is due to the sheer amount of financial metrics to disclose as part of annual results.

'Connected Transactions' and 'Notifiable Transactions' have the two highest mean word counts after annual results. This is due to these types of announcements often having to disclose the background of entering into such transactions at length.

# Training a Recurrent Neural Network 
I implemented a recurrent neural network with a bidirectional LSTM layer after an embedding layer using pre-trained GloVe embeddings of 300 dimensions. The details of my implementation can be found <a href='HKEx_Announcement_Classifier.ipynb'>here</a>.

Through fine-tuning hyperparameters of the model, I was able to improve on the initial training and validation accuracy of the model (72.3%, 60.0%) to（95.0%, 93.6%).

# Training a Transformer 

The transformer architecture was able to easily reach training accuracy of ~100% and validation accuracy of 95-96% with little fine-tuning. The implementation can be found <a href='Transformers - HKEX Annt Classifier.ipynb'>here</a>.

## Comparison of RNN vs Transformer 
### RNN 
![Image of Training Plot](/images/training_plot.png)

### Transformer 
![Image of Transformer Training](/images/transformers_performance.png)

The recurrent neural network was able to accurately classify 93.6% of announcements in the validation set, and it was able to accurately identify new announcements on the HKEx passed into it, provided that the categories of such announcements were within the scope of the training data. 

# Improving the Model 
Further improvements on the model would include more data from different jurisdictions, and from different types of legal documents, so as to create a more general and more accurate legal text classifier.

# Application
As someone working in the legal industry, a legal text classifier would be immensely helpful to my day-to-day workflow, saving significant amounts of time spent on manually filing different types of legal texts. This type of classifier can save both time and costs in legal due diligence for Initial Public Offerings on Stock Exchanges. 


