1. Dataset:
- Nguồn : https://spamassassin.apache.org/old/publiccorpus/?utm_source=zalo&utm_
- Mô tả dataset : 
	* Tổng ~11000 emails
	* Email rác (Spam): bao gồm 3793 email, chia trong 4 thư mục. Trong đó có 1542 email có nội dung ở dạng html.
	* Email thường (Easy Ham): gồm 6451 email, chia trong 3 folder. Không có nội dung ở dạng html. 
	* Email thường khó phân loại (Hard Ham): 500 email, chia trong 2 folder. Trong đó có 238 email có nội dung dạng html. 
2. Tiền xử lý:
- Strip email header.
- Lower-casing.
- Strip html symbols (ex: &nbsp;,etc)
- Strip html tags.
- Strip urls.
- Strip email address.
- Strip punctuation.
- Strip numeric.
- Strip multiple whitespaces.
- Remove short words.
- Remove stopwords.
- Word stemming using Porter Stemmer
	* Thư viện sử dụng : gensim
3. Cách sử dụng:
- git clone https://github.com/phanthanhdat1902/Email-Classifier.git
- Môi trường : Python 3.8.3 trên Anaconda
- Editor : Jupyter notebook
- Cài đặt các thư viện liên quan :
	* Mở anaconda : pip install gensim
			pip install EmailParser
			pip install regex
- Mở file SpamEmailClassLatest.ipynb
- Chạy lần lượt từng câu lệnh:
- Các 3 file tiền xử lý (spam_clean.txt,hardHam_clean.txt,easyHam_clean.txt) sẽ được sinh ra
- Các file xác suất của tập từ điển sẽ được sinh ra.
- Dự đoán 1 email:
Example:Code python (Khi các dòng đã được chạy lần lượt)

message = '''NEED Health Insurance? 
 In addition to featuring the largest selection of major medical 
health plans from leading companies, our service also
offers a wide selection of quality dental plans.  You can obtain 
FREE instant quotes, side-by-side comparisons, the best available 
prices, online applications, and a knowledgeable Customer Care 
team to help you find the plan that is right for you.
If you would like more information please email
surefiremarketing@btamail.net.cn?subject=healthinsurance
with "Send me health insurance info" in the body of the email
***************************************************************
If you do not wish to correspond with us, reply to 
surefiremarketing@btamail.net.cn  with remove as your subject. '''

word_in_ham_probs, word_in_spam_probs, spam_prob, ham_prob=load_model()
label=classify(message,word_in_ham_probs, word_in_spam_probs, spam_prob, ham_prob)
if label == 1:
    print('spam')
else:
    print('ham')
