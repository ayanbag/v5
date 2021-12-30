---
layout: post
title: "Lossy Image Compression Using Singular Value Decomposition And Fast Fourier Transform"
author: "Ayan Bag" 
categories: journal
tags: [Pattern Recognition,Compression,Singular Value Decomposition,Fourier Transform]
image:
---

# Abstract

With the rapid development of technology, image information is growing, and we often need to transmit and store those images in many applications. A large size image can take a lot of transmission time and storage. To reduce the transmission time and required storage without degrading the image quality, image compression algorithms are studied and applied. This paper proposes a new image compression algorithm that combines the Singular Value Decomposition (SVD) technique and Fast Fourier Transform (FFT). The image is first decomposed using the Singular Value Decomposition technique and then compressed by using the Fast Fourier Transform technique. SSIM and Peak Signal-to-Noise Ratio are used as performance metrics with the result of CT compression algorithm.

<br/>

# 1. Introduction

With the rapid development of technology, large volumes of data are being generated daily. This data can be of various forms, such as text, audio, video, images, and so on. Images are one of the most popular data sharing methods. Storing the uncompressed data prove to be very expensive in terms of storage cost and also, the transmission of uncompressed data requires a large bandwidth. Because of these reasons, techniques of compressing data before storage and transmission have become a significant area of interest in the research community; particularly in the fields such as artificial intelligence, pattern recognition, and so on. In this paper, we propose a new algorithm using the technique of singular value decomposition and Fast Fourier transformation. 

Image compression techniques can be broadly classified into two categories: Lossless compression and Lossy compression. Lossless compression techniques define entropy, which limits the reduction in the image. It tends to produce the same copy as that of the original data. Lossless compression is known as reversible as it doesn’t degrade the quality of the image. Lossy compression techniques identify the minute details and variations in the system which the human eye is not fine-tuned to recognize. The amount of storage required to store the image file can be reduced by eliminating such features. Lossy compression often compromises the quality of the image. However, it can be used to achieve the storage space requirements. Lossy compression is irreversible because it degrades the data. 

<br/>

# 2. Image Compression based on Singular Value Decomposition and Fast Fourier Transform

## 2.1 Singular Value Decomposition of Image

The goal of SVD is to find the best approximation of the original data points that is of large dimensions, using fewer dimensions. This is possible by identifying regions of maximum variations. So when a high dimensional, highly variable set of data points is taken, SVD is employed to reduce it to a lower dimensional space that exposes the substructure of the original data more clearly and orders it
from most variation to the least. In this way, the region of most variation can be found and its dimensions can be reduced using the method of SVD. In other words, SVD can be seen as a method for data reduction.

The singular value decomposition is defined as a factorization of a real or complex, square or non-square matrix. The basic concept is to represent an image with size *m* by *n* as a two-dimentional *m* by *n* matrix. SVD is then applied to this matrix to obtain the **U**, **S**, and **V** matrices. **S** is a diagnoal *m* by *n* matrix whose number of non-zero elements on the diagnoal determine the rank of the original matrix. The fundamental concept of the SVD based image compression technique is to use a smaller number of rank to approximate the original matrix.

Assume a sample set X, contains *m* samples, the dimension of each sample is *n*,

$$
\begin{equation}
    X = \{X_1, X_2, ...., X_m\}
\end{equation}
$$

$$
\begin{equation}
    X_i = \{X_{i1}, X_{i2}, ....,X_{in}\} \in R^n
\end{equation}
$$

As we know, Singular Value Decomposition (SVD) is a linear image matrix transformation in which an image matrix X is decomposed into 3 component matrices U, S & V such that,

$$

\begin{equation}
X = USV^T
\end{equation}

$$

where **U** is *m* x *m*  orthogonal matrix, **V** is *n* x *n* orthogonal matrix, and **S** is *n* x *m* matrix with the diagonal elements represents the singular values, $ s_i $ of X.

Therefore,

$$

\begin{equation}
    X = \begin{bmatrix}
    u_1 & u_2 & ...... & u_m
    \end{bmatrix}

    \begin{bmatrix}
    s_1 & 0 & 0 & ... & 0 \\
    0 & s_2 & 0 & ... & 0 \\
    \vdots &  & \ddots & &\vdots \\
    0 & 0 & 0 & ... & s_n
    \end{bmatrix}

    \begin{bmatrix}
    v_1^T\\
    v_2^T\\
    \vdots\\
    v_n^T
    \end{bmatrix}
\end{equation}

$$

The values $ s_1>s_2>s_3> ... >s_n>0 $ and they arranged in decreasing order of magnitude, so the last values of matrix S is approximately equal so zero. Therefore they can be removed.

So, after removing those values, we get:

$$

\begin{equation}
    X = US^1V^T
\end{equation}

$$

$$

\begin{equation}
    X = \begin{bmatrix}
    u_1 & u_2 & ... & u_m
    \end{bmatrix}
    \begin{bmatrix}
    s_1 & 0 & 0 & ... & 0 \\
    0 & \ddots &  & ... & \vdots \\
    \vdots & ... & s_r & ... & \vdots\\
    \vdots & ... &  &\ddots &\vdots \\
    0 & 0 & 0 & ... & 0
    \end{bmatrix}
    \begin{bmatrix}
    v_1^T\\
    v_2^T\\
    \vdots\\
    \vdots\\
    v_n^T
    \end{bmatrix}
\end{equation}

$$

Now in the above matrix, the terms above $r$ is removed and replaced with zero, so multiplication of terms greater than $r$ will be zero. If m=n, then the above matrix can be represented as,

$$

\begin{equation}
    X = \begin{bmatrix}
    s_1u_1 & s_2u_2 & ... & s_ru_r & 0 & ... & 0
    \end{bmatrix}
    \begin{bmatrix}
    v_1^T\\
    v_2^T\\
    \vdots\\
    v_n^T
    \end{bmatrix}
\end{equation}
$$

$$
\begin{equation}
    X = s_1u_1v_1^T + s_2u_2v_2^T + s_3u_3v_3^T + ... + s_ru_rv_r^T 
\end{equation}
$$

$$
\begin{equation}
    =  \sum_{n=1}^{r} s_iu_iv_i^T
\end{equation}
$$

As we know, the rank of a singular matrix is equal to the number of non zero singular values. The rank of above matrix will now be obviously reduced as the number of S values is approximated to ‘r’ terms. Therefore, size of the matrix is reduced, which in turn reduces the memory occupied by the image. We have to select optimum ‘r’ such that there is no significant degradation of image quality and a same time storage occupied by the image is reduced.

<br/>

## 2.2 Fast Fourier Transform for Image Compression

The Fourier Transform is an important image processing tool which is used to decompose an image into its sine and cosine components. The output of the transformation represents
the image in the Fourier or frequency domain, while the input image is the spatial domain equivalent. In the Fourier domain image, each point represents a particular frequency contained in the spatial domain image. Image reconstruction using FFT/IFFT is also possible.

The Fourier Transform is used in a wide range of applications, such as image analysis, image filtering, image reconstruction and image compression. 

The Fourier transformation is generally needed to transform a signal from the spatial dimension into the frequency dimension. The frequency domain representation is exactly the same signal, in a different form. Using the Inverse Fourier transformation the converted signal can be restored from frequency dimension. 

The Fast Fourier Transform (FFT) is another method for calculating the DFT. While it produces the same result as the other approaches, it is incredibly more efficient, often reducing the computation time by hundreds. 

The Fourier Transform produces a complex number valued output image which can be displayed with two images, either with the real and imaginary part or with magnitude and phase.
In image processing, often only the magnitude of the Fourier Transform is displayed, as it contains most of the information of the geometric structure of the spatial domain image. However, if we want to re-transform the Fourier image into the correct spatial domain after some processing in the frequency domain, we must make sure to preserve both magnitude and phase of the Fourier image 

<br/>

## 2.3 Proposed Algorithm for Image Compression

To ensure the image compression quality, this paper combines the Singular Value Decomposition and Fast Fourier Transform, and the image is compressed in two steps. Specific algorithm is shown in Figure 1.

<figure><p style="text-align:center;"><img src="../assets/img/compression/flch.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.1 - Block diagram of the proposed image compression algorithm</figcaption></figure>

The image data is decomposed into three color channels red, blue and green. Each channels represent a matrix with the values ranging from 0 to 255. Now, we compute an approximation of each color channel matrix, which take only fraction of space to store the data. Now selecting only r larger singular values of both orthogonal matrix and diagonal matrix for each color channel to realize the first-stage compression of the image. Now, applying Fast Fourier Transform on each resultant matrix, to compress the data. Now the image is reconstructed using Inverse Fast Fourier Transform, and keeping only k\% of data. The image is reconstructed. 

<br/>

# 4. Experiments and Discussions

In order to measure the effectiveness of our proposed algorithm, 6 images of the compression experiments were carried out. All images are 512 x
512 color images. By changing the contribution of the singular value of the image signal and the FFT coefficient quantization threshold, the reconstructed images are obtained under different compression ratios, and the PNSR and SSIM are calculated.

Table 1,2 and 3 shows the comparison of PSNR and SSIM values of the proposed and CT compression algorithm in 20:1, 40:1 and 80:1 compression ratio respectively. According to above mentioned table, it shows that the proposed algorithm is best out of two algorithms. Under same condition the PSNR and SSIM values of the proposed algorithm is much higher in comparison to CT compression algorithm.


|             |     Proposed                                         ||       CT       ||
|-------------|------------------------------|------------------------|-------|--------|
| **Image**       | **PSNR**                         | **SSIM**                   | **PSNR**  | **SSIM**   |
| airplane    | 77.46                        | 0.90                   | 27.24 | 0.252  |
| lena        | 77.95                        | 0.85                   | 27.86 | 0.278  |
| monarch     | 74.68                        | 0.88                   | 27.83 | 0.274  |
| tulips      | 75.04                        | 0.86                   | 27.84 | 0.316  |
| watch       | 75.41                        | 0.85                   | 27.93 | 0.285  |
| wildflowers | 66.29                        | 0.65                   | 28.75 | 0.6342 |

<p style="text-align:center;"> Table 1. PSNR values (in dB) and SSIM values for 20:1 compression </p>

|             |     Proposed                                         ||       CT       ||
|-------------|------------------------------|------------------------|-------|--------|
| **Image**       | **PSNR**                         | **SSIM**                   | **PSNR**  | **SSIM**   |
| airplane    | 75.01                        | 0.85                   | 27.75 | 0.25   |
| lena        | 76.06                        | 0.86                   | 27.86 | 0.27   |
| monarch     | 70.34                        | 0.76                   | 27.83 | 0.28   |
| tulips      | 72.77                        | 0.79                   | 27.84 | 0.32   |
| watch       | 73.63                        | 0.76                   | 27.92 | 0.29   |
| wildflowers | 64.30                        | 0.50                   | 28.53 | 0.4750 |

<p style="text-align:center;"> Table 2. PSNR values (in dB) and SSIM values for 40:1 compression </p>

|             |     Proposed                                         ||       CT       ||
|-------------|------------------------------|------------------------|-------|--------|
| **Image**       | **PSNR**                         | **SSIM**                   | **PSNR**  | **SSIM**   |
| airplane    | 72.89                        | 0.81                   | 27.76 | 0.27  |
| lena        | 74.43                        | 0.82                   | 27.87 | 0.27  |
| monarch     | 70.34                        | 0.76                   | 27.84 | 0.28  |
| tulips      | 70.78                        | 0.72                   | 27.85 | 0.34  |
| watch       | 72.39                        | 0.76                   | 27.90 | 0.32  |
| wildflowers | 62.93                        | 0.36                   | 28.40 | 0.350 |

<p style="text-align:center;"> Table 3. PSNR values (in dB) and SSIM values for 80:1 compression </p>


Figure 2 shows the image airplane is compressed by our proposed algorithm at different compression ratio i.e. 20:1, 40:1 and 80:1. Overall, quantitative and qualitative results show that the
proposed algorithm has better image quality and compression ratio. Because of the large singular value contribution to the image signal, SVD produce good image quality, so it can be combined with FFT compression algorithm to improve the image quality and SSIM value.

<figure><p style="text-align:center;"><img src="../assets/img/compression/tabop.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.2 - Original Airplane image, and compressed image by our proposed algorithm at various compression ratio</figcaption></figure>

<br/>

# 5. Conclusion

In this paper, a new lossy compression algorithms is proposed, which combines Singular Value Decomposition method with Fast Fourier Transform. The proposed algorithm uses SVD to ignore smaller singular values to reconstruct the image. The image is again compressed by Fast Fourier Transform. The advantages of both SVD and FFT are combined effectively. And the result of proposed algorithm is obviously better than CT compression algorithm, which has a certain application prospect. 

<br/>

# Other Links:


## 1. Cite as

>Bag, A., 2021. LOSSY IMAGE COMPRESSION USING SINGULAR VALUE DECOMPOSITION AND FAST FOURIER TRANSFORM. ([pdf](https://www.researchgate.net/profile/Ayan-Bag/publication/347983766_Lossy_Image_Compression_Using_Singular_Value_Decomposition_And_Fast_Fourier_Transform/links/5ff14b5892851c13fee303d3/Lossy-Image-Compression-Using-Singular-Value-Decomposition-And-Fast-Fourier-Transform.pdf))



*Bibtex :*
```
@article{bag2021lossy,
  title={LOSSY IMAGE COMPRESSION USING SINGULAR VALUE DECOMPOSITION AND FAST FOURIER TRANSFORM},
  author={Bag, Ayan},
  year={2021}
}
``` 
<br/>

## 2. Important Links:

- [Github](https://github.com/ayanbag/ImageCompressor)