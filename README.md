# Applied Machine Learning Hackathon by Krenicki Center at Krannert ahd Google
Original file is located at: https://colab.research.google.com/drive/1saDlVpwlR1Eg1KfGKfb0Iu_8YYnDykOR?usp=sharing

* Awarded 1st position for implementing cloud based ML framework to predict US household income for real-estate brokerage firm
* Identified target segments for promoting low-cost housing options and used smote for oversampling to achieve AUC of 90.6

## BAIM team wins hackathon with Krenicki Center for Business Analytics and Machine Learning:
**Official Krannert News featured on** - https://krannert.purdue.edu/news/features/?story=5773

**Purdue Krenicki Center for BA and ML tweets - @PurdueKrenicki:**

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Abhishek Kumar, Technical Lead at Google AI, discussing <a href="https://twitter.com/hashtag/MachineLearning?src=hash&amp;ref_src=twsrc%5Etfw">#MachineLearning</a> for decision making at <a href="https://twitter.com/PurdueKrannert?ref_src=twsrc%5Etfw">@PurdueKrannert</a>. The event is organized by <a href="https://twitter.com/PurdueKrenicki?ref_src=twsrc%5Etfw">@PurdueKrenicki</a>. It also consists of a hackathon in which 42 MS-BAIM students participate. <a href="https://t.co/AoEe0xAW6S">pic.twitter.com/AoEe0xAW6S</a></p>&mdash; Purdue Krenicki Center for BA and ML (@PurdueKrenicki) <a href="https://twitter.com/PurdueKrenicki/status/1187712241208037377?ref_src=twsrc%5Etfw">October 25, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

**Purdue MBA tweets - @PurdueMBA:**

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">A team of MS Business Analytics &amp; Information Management program students, Akshay Madar, Robin Jindal, Karthik, Dibyamshu Shrestha, and Mehul Zawar, won the Applied Machine Learning Hackathon hosted by Krenicki Center last week! Great job team! <a href="https://twitter.com/hashtag/BoilerUp?src=hash&amp;ref_src=twsrc%5Etfw">#BoilerUp</a>! <a href="https://t.co/bssruNkIxb">pic.twitter.com/bssruNkIxb</a></p>&mdash; Purdue MBA (@PurdueMBA) <a href="https://twitter.com/PurdueMBA/status/1190253859270213632?ref_src=twsrc%5Etfw">November 1, 2019</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

## Machine Learning algorithms used: 
Logistic Regression, SVM, Decision Tree, Random Forest, Neural Networks

## Why Google Colaboratory?
Colaboratory, or **"Colab"** for short, allows you to write and execute Python in your browser, with
* Zero configuration required
* Free access to GPUs
* Easy sharing
Whether you're a student, a data scientist or an AI researcher, Colab can make your work easier. You can also harness the full power of popular Python libraries to analyze and visualize data.

## Why Amazon S3?
Amazon Simple Storage Service (Amazon **S3**) is an object storage service that offers industry-leading scalability, data availability, security, and performance. This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides easy-to-use management features so you can organize your data and configure finely-tuned access controls to meet your specific business, organizational, and compliance requirements.

## Boto 3:
Boto is the Amazon Web Services (AWS) SDK for Python. It enables Python developers to create, configure, and manage AWS services, such as EC2 and S3. Boto provides an easy to use, object-oriented API, as well as low-level access to AWS services.

```
#@title Set up Boto credentials to pull data from S3
 import boto3  
 import botocore  
 BUCKET_NAME = 'amazing-bucket-am-1' # replace with your bucket name
 
 # enter authentication credentials
 #  Credentials for your AWS account can be found in the IAM Console. You can create or use an existing user. Go to manage access keys and generate a new set of keys.
 s3 = boto3.resource('s3', aws_access_key_id = 'ENTER YOUR ACCESS KEY', aws_secret_access_key= 'ENTER YOUR SECRET KEY')  
 ```
 
 ```
  #@title Download "training.csv" from S3
 KEY = 'hackathon/training.csv' # replace with your object key  

 try:  
   # we are trying to download training set from s3 with name `training.csv` to colab dir with name `training.csv`  
   s3.Bucket(BUCKET_NAME).download_file(KEY, 'training.csv')  
 except botocore.exceptions.ClientError as e:  
   if e.response['Error']['Code'] == "404":  
     print("The object does not exist.")  
   else:  
     raise  
 ```
 
 



