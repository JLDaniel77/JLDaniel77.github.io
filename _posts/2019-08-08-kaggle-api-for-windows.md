---
title: "Kaggle API for Windows Users"
date: 2019-08-08
tags: [kaggle api, machine learning competition]
---

### Accessing the Kaggle.com API with Jupyter Notebook on Windows

This week is project week at [Lambda School](https://lambdaschool.com/), and our
project was an in-class Kaggle competition. I wanted to be able to download the
data and submit files using the Kaggle API, but the tutorials I found were for
setting up the Kaggle API on Google Colab, using a Mac, or using Linux operating
system. I searched Google for hours and finally figured it out, so I wanted to
share this with other Windows users working locally with Jupyter Notebook.

First, you need to pip install the Kaggle library. In the Windows search bar
type cmd and open a command prompt window. At the prompt, type “pip install
kaggle” as shown below (your prompt will look slightly different).

![](https://cdn-images-1.medium.com/max/800/1*miwHdY0DyQiWz1xvPKxrMQ.jpeg)

*****

Next, go to your Kaggle account (or create one if you haven’t yet), click the
profile icon in the top right corner of the screen, and select “my profile” from
the dropdown list. Scroll down to about middle of the page, and click on “Create
a New API Token”. Then, a file named kaggle.json will automatically download to
your downloads folder. This file contains your sign-in credentials to allow you
to access the API. Once the download is complete, go back to the command prompt
window.

*****

Pretty simple so far, right? Now for the tricky part. You need to create a
directory to put the API token in, so the Kaggle library will know where to look
for your sign-in credentials when you try to access the API from your notebook.
The problem is, you can’t just add this directory using the Windows file
explorer. It must be done from the command line because you can’t create a
“.file_name” from the GUI. So, from your home directory type:

![](https://cdn-images-1.medium.com/max/800/1*oXsaT62S5pT655pDL3zzBw.jpeg)

This file must be named “.kaggle” and it must be in the same directory as your
installation of Python, which is typically the home directory.

*****

Once you have created the .kaggle file, navigate to your downloads directory as
shown below:

![](https://cdn-images-1.medium.com/max/800/1*fnH-rjUzx31APxcvcV-0oA.jpeg)

Once you are in the downloads directory, you need to move the kaggle.json file
to the new .kaggle directory. From the command prompt type:

![](https://cdn-images-1.medium.com/max/800/1*FgbiWGIP062HzcvK_yV58A.jpeg)

*****

Press enter and you are now ready to use the Kaggle API. To test that everything
is working, type:

![](https://cdn-images-1.medium.com/max/800/1*jos8aIAQSTEVz5afHcD8Gw.jpeg)

This should bring up a list of all the active Kaggle competitions.

*****

Next, go back to Kaggle.com, join the competition of your choice, accept the
rules, click on the data tab, then scroll down and find the API link. Click on
the link to save it to the clipboard, then open a Jupyter Notebook or Jupyter
Lab, import kaggle, then import the data for your competition by typing
“!paste-kaggle-api-link-here” as seen below:

![](https://cdn-images-1.medium.com/max/800/1*a9W-NclSu9wbNEYMqIp8JA.jpeg)

Finally, you will need to unzip the data files. Usually, you will receive the
train_features, test_features, and train_labels files, but inspect your
downloaded files to make sure you have the correct file names, then unzip the
files with the “!unzip” command as seen below:

![](https://cdn-images-1.medium.com/max/800/1*o4S-9uEuJ323KbftzjBQpw.jpeg)

Congratulations! You are now ready to start exploring your dataset. This might
seem like a lot of trouble if you are only planning on entering one competition,
but the real value of using the Kaggle API is seen when making competition
submissions.