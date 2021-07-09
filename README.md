# CrypticMessage
## Introduction
Applying Steganography followed by Visual Cryptography.The proposed work is basically a framework designed with two modules i.e. Steganography using Genetic
Algorithm and Visual Cryptography. An input image is accepted as cover image for the input message in plain text format. After embedding the secret message in LSB (least
significant bit) of the cover image, the pixel values of the steg-image are modified by the visual cryptography to keep their statistic characters.

Steganography is the method of hiding secret data inside any form of digital media. The main idea behind steganography is to hide the existence of a data in any medium like audio, video, image etc.

Visual cryptography is a cryptographic technique which allows visual information (pictures, text, etc.) to be encrypted in such a way that the decrypted information appears as a visual image.

## Architecture
![image](https://user-images.githubusercontent.com/56619771/125083171-ae387400-e0e5-11eb-861c-3f71b43b8152.png)


![image](https://i.imgur.com/nh0J1Sn.png)


## Project


### File description
| File          | Description                                    |
|---------------|-----------------------------------------------------------|
| lsb_stegno.py | Methods to Encode and Decode data using LSB Steganography |
| n_share.py    | Methods to Split and Compress LSB Encoded images          |

### Algorithms
##### Steganography
###### Encoding data in image
```python
# Putting modified pixels in the new image
newimg.putpixel((x, y), pixel)
if (x == w - 1):
    x = 0
    y += 1
else:
    x += 1
```

###### Decoding data from image
```python
# string of binary data
binstr = ''

for i in pixels[:8]:
    if (i % 2 == 0):
        binstr += '0'
    else:
        binstr += '1'

data += chr(int(binstr, 2))
if (pixels[-1] % 2 != 0):
    return data
```
##### Visual Cryptography
###### Generating shares
```python
# Split image based on random factor
n = int(np.random.randint(data[i, j, k] + 1))
img1[i, j, k] = n
img2[i, j, k] = data[i, j, k] - n
```

###### Compressing shares
```python
img[i, j, k] = img1[i, j, k] + img2[i, j, k]
```
