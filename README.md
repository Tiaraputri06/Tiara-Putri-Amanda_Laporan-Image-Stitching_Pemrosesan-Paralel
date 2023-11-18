# Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel
# Cara Image Stitching dengan Menggunakan Python dan OpenCV
Image stitching adalah proses menggabungkan beberapa gambar yang saling tumpang tindih menjadi satu gambar yang lebih besar dan utuh. Gambar yang digunakan dalam proses ini biasanya diambil dari sudut pandang atau posisi yang berbeda, dan seringkali memiliki tumpang tindih atau area bersama. Tujuan utama dari image stitching adalah membuat gambar yang lebih lengkap atau lebih luas daripada yang dapat dihasilkan oleh satu gambar saja.
# Daftar isi
- [Tools Requirements](Tools-Requirements)
- [Input Image](Input-Image)
- [Codingan Python](Codingan-Python)
- [Execute the Code](Execute-the-Code)
- [Output](Output)

# Tools Requirements
1. Pertama-tama, sebelumnya pastikan update terlebih dahulu Operating Sistem dengan cara
   ```
   sudo apt update
2. Langkah selanjutnya Install tools terlebih dahulu sebelum menjalankan stitching
   ```
   pip3 install numpy
  ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/0d0f9886-b38d-404c-ae11-853547366392)

3. Jika sudah terinstall lanjut ke tools yang kedua, dengan perintah
   ```
   pip3 install opencv-python
  OpenCV menyediakan algoritma untuk visi komputer, seperti ekstraksi fitur, pencocokan pola, dan analisis objek. Ini dapat digunakan dalam berbagai aplikasi, termasuk pengenalan objek, pelacakan objek, dan segmentasi objek. 

4. Selanjutnya tools yang ketiga
   ```
   pip3 install imutils
  ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/fe1a97bf-bc13-4fe3-a8b3-d3d02295b38d)


# Input Image
![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/8ce0a9ea-4410-4689-b814-8737ebdd2bd7) ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/205ae057-bca9-4a63-9d66-6a005bd7d74d) ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/88ade842-eb99-47d2-ba41-8e6854c1658d) ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/90bf0a3d-d02e-4b53-859e-ce17aa8bf553) ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/aa507ec2-2587-40a4-b529-e1199d205337) ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/bb68a0e6-6037-4f51-a2f3-7b51fd8003e2)
# Codingan Pyhton
  1. Buatlah codingan image stitching pyhton dengan OpenCV
     ```
    from imutils import paths
    import numpy as np
    import argparse
    import imutils
    import cv2

    ap = argparse.ArgumentParser()
    ap.add_argument("-i", "--images", type=str, required=True,
            help="path to input directory of images to stitch")
    ap.add_argument("-o", "--output", type=str, required=True,
            help="path to the output image")
    args = vars(ap.parse_args())

    print("[INFO] loading images...")
    imagePaths = sorted(list(paths.list_images(args["images"])))
    images = []

    for imagePath in imagePaths:
            image = cv2.imread(imagePath)
            images.append(image)

    print("[INFO] stitching images...")
    stitcher = cv2.createStitcher() if imutils.is_cv3() else cv2.Stitcher_create()
    (status, stitched) = stitcher.stitch(images)


    if status == 0:
            cv2.imwrite(args["output"], stitched)
            print("[INFO] Image stitched and saved to {}".format(args["output"]))

    else:
            print("[INFO] image stitching failed ({})".format(status))
            
     
    
 # Execute the Code
 1. Langkah selanjutnya jalankan codingan pythonnya
    ```
    python3 <image stitching file> --images <images input direcotry> --output <image output directory>/<output name.png>
 2. contoh :
     ```
     python3 image_stitching.py --images image-input/image1 --output image-output/image1/output.png

   Jika berhasil akan menghasilkan command seperti ini
   ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/8b1e332d-68be-48d3-9f62-b21a8dde02fd)

  # Output
  ![image](https://github.com/Tiaraputri06/Tiara-Putri-Amanda_Laporan-Image-Stitching_Pemrosesan-Paralel/assets/150508674/80085f00-ed80-49ac-ba16-911ab0ee4348)

   



 










            
 






    
