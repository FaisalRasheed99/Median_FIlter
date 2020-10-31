# Median_FIlter


def median_pool(image):
    import cv2
    import numpy as np
    # reading the image using cv2 library in 3 channels(RGB)
    img=cv2.imread(image,1)
    # Padding the input image using edge padding
    padded_img = np.pad(img, (1,), 'edge')
    # initialising the median filter with a 3d tensor with all the elements 0
    median_filter = np.zeros((img.shape[0],img.shape[0],3))
    # filling this tensor using median values of image array
    for i in range(median_filter.shape[0]):
        for j in range(median_filter.shape[0]):
            for k in range(3):
                median_filter[i][j][k] = np.median([padded_img[i][j][k],padded_img[i][j+1][k],padded_img[i][j+2][k],
                                                    padded_img[i+1][j][k],padded_img[i+1][j+1][k],padded_img[i+1][j+2][k],
                                                    padded_img[i+2][j][k],padded_img[i+2][j+1][k],padded_img[i+2][j+2][k]])
    cv2.imshow("bn",median_filter)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
    
    
    median_pool("Photo.jpg")
