Download Link: https://assignmentchef.com/product/solved-cv1-assignment-1
<br>
<strong>Task 1: </strong>Appearance based classification (programming) Training:

<ul>

 <li>Download the CIFAR-10 dataset (Python version) at <a href="https://www.cs.toronto.edu/~kriz/cifar.html">https://www.cs.toronto.edu/ </a><a href="https://www.cs.toronto.edu/~kriz/cifar.html">~</a><a href="https://www.cs.toronto.edu/~kriz/cifar.html">kriz/cifar.html</a><a href="https://www.cs.toronto.edu/~kriz/cifar.html">.</a></li>

 <li>Read the first data batch in file data batch 1 as instructed on the webpage.</li>

 <li>For each of the classes “automobile”, “deer”, and “ship” (labels 1, 4, and 8, respectively), extract the 30 first images.</li>

 <li>Calculate and store the grayscale histograms of all of these images. First convert the images to grayscale by the averaging method. That is, for every pixel, the grayscale value is calculated as (<em>R</em>+<em>G</em>+<em>B</em>)<em>/</em> Then calculate the histogram using a fixed set of 51 bins covering the range 0 − 255, each bin has length 5. <strong>Do not take the automatically chosen bins by numpy.histogram </strong>(Why?).</li>

</ul>

Testing:

<ul>

 <li>Read the test batch in file test batch. For the same classes as above, extract the 10 first images.</li>

 <li>Calculate the histograms of all the images in the same way as above. Classify each image in the test set by finding its nearest neighbour in the training set. For each test image:

  <ol>

   <li>Calculate the Euclidean (<em>L</em><sub>2</sub>) distances of the histogram of the test image and the histogram of <em>every </em>training image. If you have <em>n </em>training images, you should calculate <em>n </em>distances for every test image.</li>

   <li>Classify the test image by finding the minimum of the distances. Once you find the minimum distance, the predicted class of the test image is the class of the nearest training image.</li>

  </ol></li>

 <li>Calculate the classification accuracy as the ratio of the number of correctly classified testing images and the total number of testing images.</li>

 <li>Feel free to change the bins to some other lengths like 1, 10 or 255, and see how the classification accuracy varies.</li>

</ul>

Hints:

<ul>

 <li>When you have loaded the data (in the dictionary called train), this is how you can access the color channels of the i’th image.</li>

</ul>

<table width="604">

 <tbody>

  <tr>

   <td width="604">raw_data = train[“data”][i,:] red = raw_data[:1024].reshape((32,32)) green = raw_data[1024:2048].reshape((32,32)) blue = raw_data[2048:].reshape((32,32))</td>

  </tr>

 </tbody>

</table>

1

2

3

4

<ul>

 <li>Be careful with the data types. Do not directly sum uint8 arrays, but first convert them to floating point to avoid overflow.</li>

</ul>

<strong>Task 2: </strong>Saliency map computation (programming)

Figure 1: Flower

A saliency map highlights what visually stands out in an image from its neighbouring surrounding and immediately grabs our attention (e.g. this white flower amidst the green leaves in Fig. 1). A saliency map can be computed by sliding a center-surround window over the entire image, computing center-surround contrast at each step (i.e. the difference between center and surround values), and storing that value in a new matrix.

<ul>

 <li>Compute the saliency map for the <strong>intensity image </strong>for the image in Fig. 1. The image can be found in Moodle under the name“visual attention.png”:

  <ol>

   <li>Convert the image to grayscale.</li>

   <li>For every pixel, get the center-surround window and calculate the integral images (summed-area table) for both windows Use sizes 30 × 30 and 40 × 40 for the center and surround windows, respectively.</li>

   <li>Subtract the center-surround values to compute a saliency value.</li>

   <li>Construct the saliency map by placing the saliency value of that pixel in its corresponding position in a new matrix.</li>

   <li>Display the saliency map</li>

  </ol></li>

 <li>What happens if the sizes of the center-surround windows were <strong>smaller</strong>, say 10 × 10 for the center window, and 20 × 20 for the surround window? Construct and show the new saliency map.</li>

 <li>What happens if the sizes of the center-surround windows were <strong>larger</strong>, say 100×100 for the center window and 150×150 for the surround window? Construct and show the new saliency map.</li>

</ul>

<strong>Task 3: </strong>Histograms (pen &amp; paper).

<ol>

 <li>Figure 2 shows a normalized histogram <em>p</em>(<em>X</em>) of pixel intensity in a grayscale image.

  <ul>

   <li>Find the expected value of <em>X</em>, i.e., E[<em>X</em>].</li>

   <li>Write down a table that describes the cumulative histogram of <em>X</em>. The table should have two rows, one for the bins and the other for the cumulative histogram value.</li>

  </ul></li>

</ol>

Figure 2: A normalized histogram <em>p</em>(<em>X</em>).

<ol>

 <li>Calculate the <em>L</em><sub>1 </sub>(Manhattan) distance between <em>p</em>(<em>X</em>) and <em>q</em>(<em>X</em>) (Figure 3).</li>

</ol>

<em>X</em>

Figure 3: A normalized histogram <em>q</em>(<em>X</em>).