# CAR_PLATE_NO_DETECTION
A system that can detect and extract car number plates from images and read the text using EasyOCR.
Steps Involved:
Image Preprocessing:

1.Read the image using OpenCV (cv2.imread()).

2.Convert the image to grayscale for easier processing (cv2.cvtColor()).

3.Noise Reduction:Apply bilateral filter to smooth the image and reduce noise (cv2.bilateralFilter()).

4.Edge Detection:Use Canny edge detection to highlight the edges of objects in the image (cv2.Canny()).

5.Contour Detection:Find contours in the edge-detected image using cv2.findContours() to locate potential number plate areas.

6.Sort the contours by area and identify the contour that approximates a quadrilateral shape (since number plates are usually rectangular).

7.Mask Creation:Create a binary mask where the detected number plate region is filled with white (255), and the rest is black (0).

8.Use cv2.drawContours() to update the mask with the white-filled region of the detected number plate.

9.License Plate Localization:Use the mask to extract only the region corresponding to the number plate from the original image.

10.Apply bitwise AND operation between the original image and the mask to isolate the license plate region.

11.License Plate Cropping:Use np.where() to find the coordinates of the white pixels in the mask (representing the number plate).

12.Crop the detected license plate region from the grayscale image.

13.Text Recognition (OCR):Pass the cropped image to EasyOCR (reader.readtext()) to extract the text (number plate).
Extract the detected text from the OCR output.

14.Text Overlay:Overlay the detected number plate text on the original image using OpenCV’s cv2.putText().
Draw a bounding box around the detected number plate for visualization using cv2.rectangle().

Done!!
