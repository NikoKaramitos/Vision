# Vision

# DocScanner Project

In the DocScanner Project, the main goal was to use the combination of our knowledge of edge detection and image warping skills in order to capture and “scan” a document from an input image. 

The process began by converting the image to grayscale, followed by thresholding and the detection of contours in order to detect the edges of our document. With the edges detected, I was able to approximate the document to a polygon (in which case was a rectangle for our project) which yields our four corners. 

After detecting the corners, I determined the mapping of those corners to the rectified image for our output. For this step I determined our homography matrix using our computeH() function which utilized a least squares method to outline how points in one image view correspond to another. 

Once the homography matrix is computed, the image undergoes a projective transformation, which warps the image such that the originally detected corners align with the target rectangle ([0,0],[H,0],[H,W],[0,W]) effectively rectifying the document’s perspective. After the transformation, the image is flipped so that the words in the document are not mirrored and therefore backwards. 

Lastly, using this overall method, the input image can undergo a manual and automated mode of corner detection. In manual mode, the user types in each corner of the document in the form ([0,0],[H,0],[H,W],[0,W]) which is then used to map the image for the transformation. In automated mode, we use our corner detection method described above for the transformation process. In the automated image, the input is displayed with red dots on the corners of the image to indicate where the corners were detected. 

Some improvements to the algorithm could be made too. To enhance the robustness against varying image types, adaptive thresholding could be implemented instead of a single global threshold (ie for uneven lighting conditions). Edge detection algorithms such as Canny could be potentially implemented for more accuracy. Potential machine learning models trained on images of documents so that it could better detect corners. For manual mode perhaps some graphical interface which allows the user to use a mouseclick to select the corners of the image. 

