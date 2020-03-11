# Flickr-Image-extraction
Script for getting images from Flickr for image classification and restructure them into to PyTorch Folder structure 

This consists of two parts 

1. Fetching images form Flikr for each class you want to classify 

2. Restructuring the data retrived into pytorch Image folder structure 

Part I : Fetching images form Flikr

There are two ways to fetch results from Flicker 
1. Using the python FlickerAPI module . Where you signin register in Flickr website and get API_KEY to do queries

2. Using python requests to Flickr REST API without registering in Flickr

We are using Method 2 : python requests without registering in Flickr

For this Requests method we need to API KEY 
Steps to get API_KEY without signing in to Flickr
1. Open browser
2. Navigate to www.flickr.com
3. Do a sample search ( ex: tiger ) 
4. 
