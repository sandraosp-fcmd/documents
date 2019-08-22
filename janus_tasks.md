# Mini-project for testing the Janus system

This is a mini-project intended for you to get familiar with the janus software and also give you and intro into different types of projects we have here at Fraunhofer.

### Part 1 - Installing the system

This part involves installing all the necessary dependencies and requirements needed by the software.

First, you will need access to the server using the [pulse secure vpn](https://wiki.umiacs.umd.edu/umiacs/index.php/Network/VPN). If you already have a umiacs account, go ahead and use it. If not, ask Jason for credentials. 

In chapter 1, there are instructions on how to run the installation scripts and install the software. Try installing everything and ask if you have any questions.

### Part 2 - Testing the command line interface

Here we will test the command line interface of the software.

This is the picture we will be looking at (Harrison Ford):

> image1

![](https://resizing.flixster.com/G7JCnmXIVqTjhiJz9JUX4S3GBo8=/300x300/v1.bjsxMzU3MTQ7ajsxODEzNjsxMjAwOzEwMTE7MTIwMA)

We will be creating an identity of Harrison Ford with this image and checking if the identity matches any of the identities in these pictures:

> image2

![](https://img1.looper.com/img/gallery/the-most-terrible-things-luke-skywalker-has-ever-done/intro-1495558220.jpg)

> image3

![](https://am22.akamaized.net/tms/cnt/uploads/2017/08/leiatop1-650x574.jpg)

> image4

![](https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/articles/2015/11/mh-raiders-ark-ford-1487266332.jpeg?resize=480:*)

As you can see, it should match the identity in image 4 and not the ones in images 2 and 3. Next, you will complete some tasks to verify this.
The tasks will involve using the command line tools of the software and require you to read certain sections of the manual. The sections will be 
given to you and it is up to you to read their descriptions. First, create your own folder in the **/scratch0/workspace** directory for the inputs and
outputs you will generate. For the pictures and videos we will be using, they will all be located in **/scratch0/workspace/images**.
For other input files, you can create them on your own. The command line tools are located in **/scratch0/vc/janice-v7/build/harness**.

# Task 1 - creating template files from images.

The first step in using this software is to detect faces in a given image. Then, using the information from the detection, we must create templates of the detected face.

* You will first detect the face (creating an identity for the image) by using **janice_detect** as described in section 2.2.1. Read the description of the command and how to use it. The images you will be using will be located in **/scratch1/workspace/images**. You should then have a csv file containing the details of image 1.

* Next, we will use **janice_enroll_detections** to create template files that the software uses to search for people in different pictures. Read about and use this function as described in section 2.2.2 to create a template from the csv file created previously.

* Now we will repeat what we just did with one command, **janice_enroll_media**. Use this function to generate template files from images 2, 3, 4 and 5 using only one command.

# Task 2 - Verification of identities

Now we will use the template files we just created to verify whether or not the person in image 1 matches the person in images 2-4.

* All we have to do is run the **janice_verify** command (section 2.3)  using the templates generated in task 1. In your output, there should be low scores for images 2, and 3 and a high score for image 3.

# Task 3 - Creating a gallery

In order to search for a person in a set of images or a video, we must first create a gal file (collection of templates).

* We have a video file called video1.mp4, and we want to know if the person in image 1 is present in this video. First, we must create template files from this video and can easily done by using *janice_enroll_media*.

* Then, using **janice_create_gallery** (ch. 2.4) on the templates we just created, we can create a gal file that represents all the people in the video (should just be one person in the video).

# Task 4 - Searching for a person

Now that we have the gal file for the video, we can search for the person in image 1 in the video.

* Using **janice_search**, search for the person in image 1 using the template we created from it against the gal file created in task 3.

You should get high confidence scores since video1 contains the person in image1. Next, we will see if video2 contains the person in image1 (it doesn't).

* Repeat the steps to create the gal file for video2 and search for the person in image1 in this gal file. You should get low confidence scores.

# Task 5 - Clustering media

TODO
