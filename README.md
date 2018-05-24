# Preface

As a travel enthusiast with passion in experiencing stylish airbnb apartments, finding my favorite apartment sometimes is not enjoyable. Being stucked by describing what I am looking for in words(not mention looking for apartments in non-english speaking places), I have this come out...


# Eye BnB 

## Business Prospect

•	This project will help users find their favorite lodging during their travel, based on images or some descriptions uploaded by the users

•	It would provide value to:

 o	People who are looking for stylish, funky, fancy airbnb apartment for their travel
 
 o	Apartment owners who want to know how many apartments in the same city looks like theirs so that they can make their apartments either discriminative or closer to the apartments which are already popular. 

## Data sources

•	Airbnb publicized their own datasets which provide lists of all the apartments in certain cities in the U.S. with lots details (http://insideairbnb.com/get-the-data.html)

•	With the lists above, images and highlight tags of each apartment were scraped with urllib2

## Data Preparation

•	*Online collection*

  o The raw data is basic information of Airbnb apartment (location, descriptions, price range, webpage URL) which can be found in the datasets publicated by Airbnb.It is saved in MongoDB running on AWS
  

o	Images of each apartment were scraped from Airbnb and saved to MongoDB
  
  o	Highlight tags and some reviews will also be scraped and saved

•	*Offline processing*

  o	For each apartment in the DB, extract certain features from its images and save to an excel spreadsheet (with its ID) 
  
  o	Put highlight reviews to the excel spreadsheet for further uses
  
## Modeling

•	*Similarities calculation*
  
  o	Cosine Distance
  
  o	Pearson correlation


  
•	*Image feature extraction*
  
  o	HSV-Histgram
  
  o	GIST

  o CNN
  
  o	others

## Evaluation - conceptually and quantitatively

• *Model Validation*：Image features and similarity measurements was tested on a subset of Indoor Scene Recognition dataset publicated by MIT, for more details: http://web.mit.edu/torralba/www/indoor.html

Examples in the dataset:
For scene florist:
<img> https://github.com/starfoe/Eye-bnb/blob/master/iconImage/Picture2.png </img>

•  *Principle*: features from the same category(bedroom/bookstore/florist/dining room..) should be closer to each other than to features from other categories. In a mathmatical way, the higher the number of dis(within clusters)/dis(between clusters) , the better the feature is.
  Calinski_harabaz was used to evaluate the features quantitatively. For comparation, a baseline case was generated by shuffling the labels of the true data to make the labels random. The performance of the feature was as follows:

  
  Calinski_harabaz for the true case is 22.816
  Calinski_harabaz for the random case is 0.986
  
  Its clear that Calinski_harabaz of feature is quite higher than that of the baseline case, indicating that the feature could be used to represent images
  
Calinski_harabaz: <url> http://scikit-learn.org/stable/modules/generated/sklearn.metrics.calinski_harabaz_score.html</url>

•	*Visualization*: look at all the recommendations and conceptually check if they make sense

## Deployment

•	Step1: given a picture, the system can return places looks similar (of the same style)

•	(To do) Step2: users can add some word descriptions to what they dream of going ( industrial style, splendid..) to make the searching more precise

## Techiques 

•	MongoDB

•	AWS EC2 and S3

• (To do) Keras/TensorFlow 


## References for the techniques involved in the project:

### Gist feature: 

  • MatthijsDouze,HervéJégou,SandhawaliaHarsimrat,LaurentAmsaleg,CordeliaSchmid. Evaluation of GIST descriptors for web-scale image search. CIVR 2009 - International Conference on Image and Video Retrieval, Jul 2009, Santorini, Greece. ACM, pp.19:1-8, 2009
  
  • Gist/Context of a Scene: <url> http://ilab.usc.edu/siagian/Research/Gist/Gist.html </url>

  • A. Oliva and A. Torralba. Modeling the shape of the scene: a holistic representation of the spatial envelope. IJCV, 42(3):145–175, 2001.
  
### Similarity measurement:

 • Similarity measurement between images: <url> https://ieeexplore.ieee.org/document/1508081/</url>
 
### Clustering evaluation:

 • <url> http://www.ims.uni-stuttgart.de/institut/mitarbeiter/schulte/theses/phd/algorithm.pdf </url>
 
 • Calinski-Harabasz Index and Boostrap Evaluation with Clustering Methods: <url> http://ethen8181.github.io/machine-learning/clustering_old/clustering/clustering.html </url>

### Packages/librarys:
Pymongo, cv2, fftw3, urlib2, boto3,SciPy, Sklearn, PIL, flask
 





