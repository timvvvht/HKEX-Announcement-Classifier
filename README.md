# HKEX Announcement Classifier

HKEX Announcement Classifier is a project on data exploration, analysis and finally training a recurrent neural network (RNN) to classify disclosure announcements submitted by listed companies on the Hong Kong Stock Exchange (HKEX).

In this project, I scraped data of 6 types of announcements, namely:
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
Includes bi-gram analysis and average word count analysis across different types of announcements. More details can be found in <a href='www.google.com'> this iPython notebook</a>
[PICTURE]


# <a href='HKEX_Announcement_Classifier.ipynb'>Training a Recurrent Neural Network </a>
The model architecture is as follows: 
[PICTURE]

The trained neural network was able to accurately classify X% of announcements in the validation test. 
Try it yourself <a href='HKEX_Announcement_Classifer.ipynb'>here</a>!
