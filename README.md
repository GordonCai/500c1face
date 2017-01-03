### WITCH: EC500C1/EC601 Face Recognition/Makeup Project

> Hello World. We're team "Witch" from ECE department, Boston University.
Witch is a curriculum-based software application team project. A core technology objective was given to us, face recognition, and we have sucessfully transformed it in terms of building a real-world executable and marketable application. 
#####The idea is to utilize facial landmark detection for virtual makeup, and beyond that, we wanted to make recommendations or suggestions based on the makeups that our customer have just tried on. We believe that technology have simlified a lot of things and Witch will be another proof- it reduces the time cost and eliminates hygene concerns for women shopping for beauty products and who knows, men could also use our "witchcraft" to pick out a *perfect* present for their girls. ;)

>Witch Tells You Which. 


#### Introduction
So far, we have pulled out a web-based application hosted by cloudfront computer server. Such main functionalities are
lipcolor/eyebrow virtual try-out and live-time recommendation that leads you to the purchasing page. These are achieved by:

* Website frontend design, in conjunction with backend 
* Dynamic web hosting
* Facial landmard detection and virtual effect  with dlib and OpenCV bindings
* A dedicated database 

--------------------------------------------------------------------------------------
#### How to use the web app:
* open it with firefox: http://ec2-54-173-250-109.compute-1.amazonaws.com
* open develop tools to inspect the files and data transfer between the front end and server
* click 'try witcha now' to test the facial effect
* click 'snap photo' to take a photo
* click 'upload' to send the picture to server; for the best result, make sure there is sufficient lighting in the room
* choose to change lipstick or eyebrow
* choose the color to apply

The following files in the repository are used to maintian all subject related documents

1. AWS EC2 -- Dynamic Web hosting(Zhe Cai, QiuXuan Lin)
2. Datebase -- Misc. files construsting DB (QiuXuan Lin)
3. Python code -- Python code (Yang Ming, YuanKun Li)
4. Webdesign -- all files related to dynamic website design (Zhe Cai, QiuXuan Lin)


--------------------------------------------------------------------------------------
#### AWS -- Dynamic Web hosting (Zhe Cai, QiuXuan Lin)

This sections contains some general setup on the server side. Learning to use and deploy an app on Amazon AWS could be a very useful skillset during the process of agile software development.

In our project, the web application is essentially made of four parts:

1. A linux machine as host
2. Apache server
3. MySQL as database
4. PHP and python, as well as dlib and OpenCV bindings


In short, this is usually called a LAMP server. In this folder I am presenting mostly tutorials for setting up the forementioned environments. The important thing is to ensure backend-frontend connection through the following, see detailed files and tutorial at the following folder

* PHP_MySQL
* LAMP_installation
* API_tutorial



--------------------------------------------------------------------------------------
#### Datebase --  Misc. files construsting DB (QiuXuan Lin)

We have built a make up database exclusively for Witch. 

#####One of our major problem in this project is that there is NO EXISTING similar dataset for beauty products. That means, you can not find any database that contains all of the below:
1. Product color in hex or RGB
2. Product name, brand, price or other essential info
3. Purchase Link
4. Image of that prodduct

#####Our game-changer business concept MUST consists of the above- one could easily change color randomly, just use a random number generator, but could not make recommendations without such a well-stacked database.

To achive this, I've been looking into different approaches such as the Amazon API and reseached into web crawler. For the time being, we have constructed the database by using exhaustive search and Amazon ItemLookup API, which is good enough during our developing process this semester. This section contains the following folders:

* WITCH101_LipsticksDB: our primary DB in use
* test_connection.jpg: real-time demo
* backlog: misc. DB examples that worth looking into
* timecoverspider: detailed tutorial for python scapy


To move forward, we must consider using a crawler/spider that could scrapy pictures from websites automatically so that our database could be huge!

--------------------------------------------------------------------------------------
#### Python code -- Python code (Yang Ming, YuanKun Li)

#####Sprint 1:
* Get face land mark detection done(Yuankun Li)
* Setting the environmental of Opencv and dlib(YuanKun Li,Yang Ming)

#####Sprint2:

* Make the program of getting the area of lips and eyebrows cut from original photo(Yuankun Li)
* Achieve the basic function of color change(Yang Ming)

#####Sprint3:

* Make the program of blending the features from the photo that is color-changed to the original photo(Yuankun Li)  
* Make the program of adjusting two photos by aligning two faces(Yuankun Li)
* Obtain details of picture and add mixed color on lips(Yang Ming)

#####Sprint4:

* Make the program of reading color information from other txt files(Yuankun Li)
* Make the program of converting hex code to rgb code(Yuankun Li)
* Improve the accuracy of face land mark detection(Yuankun Li)
* Make the program of error-detecting(Yuankun Li)
* Add lustre on lips.(Yang Ming)
* Add color on eyebrown.(Yang Ming)




--------------------------------------------------------------------------------------
#### Webdesign -- (Zhe Cai, QiuXuan Lin)

There are five folders, the first one is the learning notes for building dynamic website. And the subsequent folders are the four versions of the websites I have done for the four sprints.

Each sprint has more features added to it:

* sprint 1: static website for the front end
* sprint 2: estabilish first dynamic website on local host with a simple GET image function
* sprint 3: upload website on AWS; connect to webcam; send and get images to and from server; connect to MySQL and send data to frontend; trigger python at AWS
* sprint 4: be able to run python-opencv-dlib at server; display product data at frontend; better frontend UI
* This README.txt file is mainly focusing on the final version (pres4 website).

##### AWS content tree
* EC2
  * Python/opencv
  * Apache server
    * MySQL
      * mysqli_connection.php
    * PHP
      * css
      * img
      * js
      * dlib
        * eyebrow.py/facedect.py
      * cc.txt / contact.php / error.jpg / eyebrow.json / faceEffect.php / getcolorindo.php / geteyebrow.php / index.php / nav.php / protfolio.php / savePicture.php / sendpyimg.php / sendpyimgeye.php

* AWS screenshot -- the screenshot of content in AWS
* cc.txt -- the color code the frontend sent for python script
* contact.php -- all webpages use this, it is the contact section of the frontend
* error.jpg -- these error pictures are sent to frontend if no face or more than one face is detected
* eyebrow.json -- due to the limited time, this is used to replace the actual database section for eyebrow
* eyebrow.py -- done by Yang Ming and Yuankun Li. It is the python script for changing eyebrow color
* facedect.py -- done by Yang Ming and Yuankun Li. It is the python script for lip color
* faceEffect.php -- the webpage for changing color
* getcolorindo.php -- extract lipstick data from database and send to frontend
* geteyebrow.php -- send eyebrow data to frontend
* index.php -- homepage
* mysqli_connection.php -- done by Qiuxuan Lin. log into database
* nav.php -- all webpages use this, it is the nav section of the frontend
* protfolio.php -- all webpage use this, it is the protfolio section of the frontend
* savePicture.php -- receive the picture from the frontend and save it in local folder
* sendpyimg.php -- triggered by the frontend; receive the color code and save it to cc.txt; evoke python script; send processed picture to frontend
* sendpyimgeye.php -- similar to sendpyimg, but process eyebrow instead of lips
