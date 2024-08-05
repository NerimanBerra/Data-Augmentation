###################-SALT PEPPER-##################################

import random 
import cv2 
image = cv2.imread(r"C:\Users\berra\Desktop\RKSoft\3\opencv.png")  
def add_noise(image): 
  
    # Getting the dimensions of the image 
    row , col = image.shape 
      
    # Randomly pick some pixels in the 
    # image for coloring them white 
    # Pick a random number between 300 and 10000 
    number_of_pixels = random.randint(300, 10000) 
    for i in range(number_of_pixels): 
        
        # Pick a random y coordinate 
        y_coord=random.randint(0, row - 1) 
          
        # Pick a random x coordinate 
        x_coord=random.randint(0, col - 1) 
          
        # Color that pixel to white 
        image[y_coord][x_coord] = 255
          
    # Randomly pick some pixels in 
    # the image for coloring them black 
    # Pick a random number between 300 and 10000 
    number_of_pixels = random.randint(300 , 10000) 
    for i in range(number_of_pixels): 
        
        # Pick a random y coordinate 
        y_coord=random.randint(0, row - 1) 
          
        # Pick a random x coordinate 
        x_coord=random.randint(0, col - 1) 
          
        # Color that pixel to black 
        image[y_coord][x_coord] = 0
          
    return image
  
# salt-and-pepper noise can 
# be applied only to grayscale images 
cv2.imwrite(r"C:\Users\berra\Desktop\RKSoft\3\salt_pepper.png", image)


################################################-Contrast Limited Adaptive Histogram Equalization-########################
import cv2
import numpy as np
from matplotlib import pyplot as plt


image = cv2.imread(r"C:\Users\berra\Desktop\RKSoft\3\opencv.png")


image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Görüntünün kontrastını artır
lab = cv2.cvtColor(image_rgb, cv2.COLOR_RGB2LAB)
l, a, b = cv2.split(lab)

# CLAHE (Contrast Limited Adaptive Histogram Equalization) uygulayarak kontrast artırma
clahe = cv2.createCLAHE(clipLimit=3.0, tileGridSize=(8, 8))
cl = clahe.apply(l)

img = cv2.merge((cl, a, b))
enhanced_image = cv2.cvtColor(img, cv2.COLOR_LAB2RGB)

# Sonuçları görselleştir
plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.title('Orijinal Görüntü')
plt.imshow(image_rgb)
plt.axis('off')

plt.subplot(1, 2, 2)
plt.title('Kontrast Arttırılmış Görüntü')
plt.imshow(enhanced_image)
plt.axis('off')

plt.show()


################################################-RESIZE-###########################################3
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\berra\Desktop\RKSoft\3\opencv.png")
# Loading the image

half = cv2.resize(image, (0, 0), fx = 0.1, fy = 0.1)
bigger = cv2.resize(image, (1050, 1610))

stretch_near = cv2.resize(image, (780, 540), 
            interpolation = cv2.INTER_LINEAR)


Titles =["Original", "Half", "Bigger", "Interpolation Nearest"]
images =[image, half, bigger, stretch_near]
count = 4
for i in range(count):
    plt.subplot(2, 2, i + 1)
    plt.title(Titles[i])
    plt.imshow(images[i])

plt.show()





import cv2
import numpy as np
import matplotlib.pyplot as plt

# path 
image = cv2.imread(r"C:\Users\berra\Desktop\RKSoft\3\opencv.png") 

# Using cv2.flip() method 
# Use Flip code 0 to flip vertically 
image1 = cv2.flip(image, 0) 

# Converting BGR image to RGB
image_rgb = cv2.cvtColor(image1, cv2.COLOR_BGR2RGB)

# Displaying the image using matplotlib

plt.subplot(1, 2, 1)
plt.title('Orijinal Görüntü')
plt.imshow(image)
plt.axis('off')
plt.show()

plt.imshow(image_rgb)
plt.axis('off') 
plt.show()

