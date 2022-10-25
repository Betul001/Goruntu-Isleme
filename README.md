# Goruntu-Isleme

#02200201062
#FATIMA BETÜL MEMDUHOĞLU



import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt


def Histogram_Computation(Image):
    Image_Height = Image.shape[0]
    Image_Width = Image.shape[1]
    Image_Channels = Image.shape[2]

    Histogram = np.zeros([256, Image_Channels], np.int32)

    for x in range(0, Image_Height):
        for y in range(0, Image_Width):
            for c in range(0, Image_Channels):
                Histogram[Image[x, y, c], c] += 1

    return Histogram


def Plot_Histogram(Histogram):
    plt.figure()
    plt.title("Color Image Histogram")
    plt.xlabel("Intensity Level")
    plt.ylabel("Intensity Frequency")
    plt.xlim([0, 256])
    plt.plot(Histogram[:, 0], 'b')
    plt.plot(Histogram[:, 1], 'g')
    plt.plot(Histogram[:, 2], 'r')
    plt.savefig("Histogram_Grafigi.jpg")


def main():
    Input_Image = cv.imread("C:\\Users\Bilgisayar\Desktop\Python\\istanbul.jpg")  # görüntüyü okuyan kısım

    Histogram = Histogram_Computation(Input_Image)


    for i in range(0, Histogram.shape[0]):
        for c in range(0, Histogram.shape[1]):
            print("Histogram[", i, ", ", c, "]: ", Histogram[i, c])

    Plot_Histogram(Histogram)
    input("Please Enter to Continue...")


if __name__ == '__main__':
    main()
