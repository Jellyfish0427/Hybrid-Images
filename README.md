## Hybrid_Images
By blending the high-frequency portion of one image with the low-frequency portion of another,  you get a hybrid image that leads to different interpretations at different distances.

### 1. Implementation
#### 1.1 Image filtering
In the file my_imfilter.py, use ```cv2.filter2D(image, -1, imfilter)``` to convolute the input image and Gaussian filter.  
The output image is low frequency.  

#### 1.2 Extract and combine the high-frequency and low-frequency signals
Do convolution with dog.bmp and Gaussian filter, the output image is low frequency.  
```low_frequencies = my_imfilter(image1, gaussian_filter)```  

![image](https://user-images.githubusercontent.com/128220508/226160239-f8883af9-9308-4e44-9ef8-28dfbd4143a2.png)  

If the low frequency part is subtracted from the original image, the high frequency will remain.  
```high_frequencies = image2 - my_imfilter(image2, gaussian_filter)```  
The image is negative values, so +0.5 is required to see it.   
```plt.imshow(normalize(high_frequencies + 0.5))```  

![image](https://user-images.githubusercontent.com/128220508/226160410-8139c154-35b6-4eb1-8845-4d74604c2e95.png)  

After combining the two images.  
```hybrid_image = low_frequencies + high_frequencies```  

![image](https://user-images.githubusercontent.com/128220508/226160439-7e1181d3-4ba5-4556-9e2a-06c3dd5a76c4.png)
![image](https://user-images.githubusercontent.com/128220508/226160444-9cd77cb7-e6ac-4be9-bdc4-14a2d2aa7fb0.png)  
It can be seen that the high-frequency part of the large picture is more obvious, and the cat is seen. 
The low-frequency part of the small picture is seen, and the dog is seen.

### 2. Experiments
Image1 : dog.bmp  
Image2 : cat.bmp  
![image](https://user-images.githubusercontent.com/128220508/226160913-ff59420a-481a-4029-8019-dcba20752f03.png)  

Image1 : plane.bmp 
Image2 : bird.bmp  
![image](https://user-images.githubusercontent.com/128220508/226160932-0be59721-fddf-4b77-846f-f949e8ad07a2.png)  

Image1 : bicycle.bmp  
Image2 : motorcycle.bmp   
![image](https://user-images.githubusercontent.com/128220508/226160965-81a04842-fdc5-4d2d-8a9d-89ebf429920d.png)  

Image1 : einstein.bmp  
Image2 : marilyn.bmp  
![image](https://user-images.githubusercontent.com/128220508/226160982-9823cd46-503a-478f-a3a7-86e50bbd16d9.png)  

Image1 : submarine.bmp   
Image2 : fish.bmp   
![image](https://user-images.githubusercontent.com/128220508/226160995-0e5897fd-446b-4e6f-b98d-3bc71c1a64c7.png)  

### 3. Discussion
I think this technology can be applied to watermarking. It is not obvious to put a low frequency watermark on the original image, but after filtering, it can prove that the picture belongs to you.
