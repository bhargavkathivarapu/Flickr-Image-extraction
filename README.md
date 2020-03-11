# Flickr-Image-extraction
Script for getting images from Flickr for image classification and restructure them into to PyTorch Folder structure 

This consists of two parts 

1. Fetching images form Flikr for each class you want to classify 

2. Restructuring the data retrived into pytorch Image folder structure 

## Part I : Fetching images form Flikr

There are two ways to fetch results from Flicker 
 ### 1. Using the python FlickerAPI module .
 Where you sign-in register in Flickr website and get API_KEY to do queries
 Link for this approach 
 Register - 
 API documnetation - 
 Exmaple usage - 

 ### 2. Using python requests to Flickr REST API without registering in Flickr

We are using Method 2
### python requests without registering in Flickr

For this Requests method we need to API KEY 
Steps to get API_KEY without signing in to Flickr
1. Open Firefox
2. Navigate to www.flickr.com
3. Do a sample search ( ex: tiger ) 
4. Now right click any where and select 'Inspect element'
5. Go to the Network tab . Enable Persist logs options .Select the XHR tab 
    - Now slowly start scrolling the web page 
    - You will see some GET and POST requests getting generated in the Network tab
    - Find the GET request with file name startig as "rest?sort=relevance&parse_tags"
    - See the GET request and copy the api_key from it 
    - Once we have API_KEY ( it will be valid for 12 - 24 hours ) . We can pass it to our python script and retrive images


Running the python script
```python
python Flikcr.py --api_key  "c986393632f57c7267cc382e5d351b8c" --search "lion" --n 500 
```



Assuming you are running in a empty folder ( Let say 'Data' ) 
Run all you Flickr image extraction from there 
The folder will be named after the query and all image will be in it 

Now to convert this folder into PyTorch Image Folder 
Run below comand

```python
python Torchify.py --src_path  "./data" --dest_path "./classfication" --train 0.6 --val 0.2
```
The script will shuffle the images and stores them in pytorch Image Folder structure
Train and validation arguments will deicided the number of train , validation and test images  for all clases

Once it finished you are good to go.

You can load this in pytorch as below
```python
img_trans - transforms.Compose([transforms.Resize((64,64),transforms.ToTensor(),transforms.Normalize()]
train_data = torchvision.datasets.ImageFolder("./classification" , transforms = img_transforms)
```

