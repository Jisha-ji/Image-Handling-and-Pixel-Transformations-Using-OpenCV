# EX NO 1 : Image-Handling-and-Pixel-Transformations-Using-OpenCV
## Name: JISHA BOSSNE SJ  
## Reg. No: 212224230106


## **Aim**
Write a Python program using OpenCV that performs the following tasks:

1.Read and Display an Image.

2.Adjust the brightness of an image.

3.Modify the image contrast.

4.Generate a third image using bitwise operations.

---
## **Software Required:**
1.Anaconda - Python 3.7

2.Jupyter Notebook (for interactive development and execution)

---

## **Algorithm:**
**Step 1:**

Load an image from your local directory and display it.

**Step 2:**

Create a matrix of ones (with data type float64) to adjust brightness.

**Step 3:**

Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

**Step 4:**

Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

**Step 5:**

Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** JISHA BOSSNE SJ
- **Register Number:** 212224230106


#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
img =cv2.imread('ex1.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img=cv2.imread("ex1.jpg" )
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```
<img width="135" height="42" alt="Screenshot 2026-04-30 132234" src="https://github.com/user-attachments/assets/0fc61400-d016-41f0-ba21-8449ef86dbcb" />

#### 3. Display the image using matplotlib imshow().
```python
img_gray = cv2.cvtColor(img_rgb, cv2.COLOR_RGB2GRAY)
plt.imshow(img_gray,cmap='grey')
plt.show()
```

<img width="728" height="534" alt="Screenshot 2026-04-30 132330" src="https://github.com/user-attachments/assets/8db32d70-619b-4cd0-8d20-ada761a14d18" />

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
img=cv2.imread('ex1.jpg')
cv2.imwrite('ex1.jpg',img)
```
<img width="61" height="44" alt="Screenshot 2026-04-30 132347" src="https://github.com/user-attachments/assets/69890b06-3d56-47ca-83f1-e5d6fe369e84" />

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img=cv2.imread('ex1.jpg')
cv2.imwrite('ex1.jpg',img)
```
<img width="61" height="44" alt="Screenshot 2026-04-30 132347" src="https://github.com/user-attachments/assets/61862321-61da-44d0-bfd3-07f42b4ef879" />

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img)
plt.show()
img.shape
```
<img width="704" height="565" alt="Screenshot 2026-04-30 132412" src="https://github.com/user-attachments/assets/34a8d366-5c6a-4b29-ba50-c12132d55251" />

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
crop = img_rgb[0:450,200:550] 
plt.imshow(crop[:,:,::-1])
plt.title("Cropped Region")
plt.axis("off")
plt.show()
crop.shape
```
<img width="451" height="572" alt="Screenshot 2026-04-30 132447" src="https://github.com/user-attachments/assets/171ed591-ceaa-4c8a-8963-cdd8f0be3624" />

#### 8. Resize the image up by a factor of 2x.
```python
res= cv2.resize(crop,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```
<img width="681" height="572" alt="Screenshot 2026-04-30 132505" src="https://github.com/user-attachments/assets/3aa52d6e-6434-4456-a4ee-0ec978eb342f" />

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python

img=cv2.imread('Apollo-11-launch.jpg',cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```
<img width="139" height="40" alt="Screenshot 2026-04-30 132520" src="https://github.com/user-attachments/assets/cd0dbdd7-c0c9-4ab0-ad19-c36455fe2f45" />

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()  
```
<img width="744" height="427" alt="Screenshot 2026-04-30 132538" src="https://github.com/user-attachments/assets/70e82318-3487-4ade-b2dc-99d04a9440bc" />

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```
<img width="523" height="847" alt="Screenshot 2026-04-30 132654" src="https://github.com/user-attachments/assets/6de3bbe4-317a-44dc-b075-b04398110387" />

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()

```
<img width="724" height="465" alt="Screenshot 2026-04-30 132714" src="https://github.com/user-attachments/assets/cdb93d16-832b-4240-b685-7a773a40ccf5" />

#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('boy.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m) 
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```
<img width="1003" height="287" alt="Screenshot 2026-04-30 132738" src="https://github.com/user-attachments/assets/a43fcd13-b6dc-4e91-a15b-18dfee8eda47" />

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```
<img width="1023" height="288" alt="Screenshot 2026-04-30 132755" src="https://github.com/user-attachments/assets/653c4d6d-317e-4d60-9a11-6c629512b05d" />

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python

b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
<img width="999" height="269" alt="Screenshot 2026-04-30 132810" src="https://github.com/user-attachments/assets/ccaa1e0b-63a4-41ca-b759-95e147641cd8" />

#### 21. Merged the R, G, B , displays along with the original image
```python

merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```
<img width="513" height="432" alt="Screenshot 2026-04-30 132823" src="https://github.com/user-attachments/assets/d7943e1f-29c3-41dd-b8ff-958b7edc0226" />

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
<img width="1000" height="272" alt="Screenshot 2026-04-30 132843" src="https://github.com/user-attachments/assets/a6d40ade-a6a4-4d02-b556-4631695b6121" />

#### 23. Merged the H, S, V, displays along with original image.
```python

merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```
<img width="986" height="441" alt="Screenshot 2026-04-30 132921" src="https://github.com/user-attachments/assets/1a50887c-a8cb-4115-afa7-faf22af6799d" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
