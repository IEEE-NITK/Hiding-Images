<h1 align = 'center'>HIDING IMAGES IN IMAGES</h1> 


<p align= 'center'>
<img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/Photo_thumbnail.jpg" style="zoom:50%" />
</p>


Steganography is the practice of hiding a secret message inside of something that is not secret. That something which is not secret can be an image, word document or even an excel sheet.



<p float="left">
    <img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/Steganography_original.png" width="250" align = 'left'/>
    <img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/Steganography_recovered.png" width="250" align = 'right'/>
</p>













<pre class = tab>Steganographical image of tree 				 				Recovered image of cat</pre>



Advantage of steganography over cryptography is that the intended secret message does not attract attention to itself. Cryptography is a science that enables privacy, steganography is a practice that enables secrecy.



<h2 align = 'center'>OUR PROJECT</h2>

Our project aims to hide images in images using 3 different approaches. 

* K-LSB method
* DFT approach
* Deep learning





## K- LSB METHOD

An image is a matrix of 'pixels'. A pixel is a small block in the image which has a single color. This color of the pixel is effect of combination of red, green and blue components (abbreviated as RGB) of the pixel. Values of these components are generally represented by 8 bit binary numbers.
For example, RGB components of the red color are 11111111, 00000000, 00000000 respectively. A black colored pixel will have RGB values 00000000, 00000000, and 00000000 respectively. 

The K-LSB method of hiding images in images is based on the observation that a slight change in the RGB values of a color does not produce a visible change in the color. 



For an example of the K-LSB method consider the 4 pixels below

<img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/grayscale_image.png" style="zoom:80%;" />     

The 8 bit representations of the pixels are respectively 01111000, 00001010, 10100000, 11110000

Suppose we want to hide the letter H in the image. ASCII code of H is <span style='color:red'>01000111</span>.  After hiding the pixel values will be
011110<span style='color:red'>01</span>, 000010<span style='color:red'>00</span>, 10100000<span style='color:red'>01</span>, 111100<span style='color:red'>11</span>. Constructing the image from new 4 pixels,

<img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/hidden.png"  align = 'left'  />



The new image is hardly distinguishable from older image!



To hide an RGB image in an RGB image former will have to be atleast 4 times smaller than the latter if we use the above method. 





## DISCRETE FOURIER TRANSFORM (DFT) METHOD

We perceive an image in terms of its brightness and colors. The Fourier transform is a tool which helps us to visualize an image in terms of its frequency contents.  

The discrete Fourier transform can be obtained by sampling the Fourier transform of an image at certain frequencies.  The discrete Fourier transform of an image has the same size as the image. Using the inverse discrete Fourier transform  it is possible to recover the image from frequency domain.

<img src="https://github.com/IEEE-NITK/Hiding-Images/blob/main/Blog/Images/dft.gif" style="zoom:80%;"/>

<p align = 'center'> Images and discrete fourier transform pairs</p>

The DFT of an image results in a matrix of complex numbers. When plotting DFT we plot only the magnitude of the DFT. 

In this approach we use the DFT to hide an image. To avoid complications due to complex numbers we will not use DFT of entire host image to hide an image. We will take DFT of 2x2 blocks in the image and add to it scaled pixel values of hidden image. Then taking the IDFT of the 2x2 block will give the corresponding 2x2 block in steganographic image. 

