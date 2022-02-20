# Mask-detection-
Creating a custom yolo v5 model to detect if a person is wearing a mask or not.

Create three folders (train,val,test)
• Add images to these three folders (train – 100images, val – 50 images)(images to include both with
mask and without mask people)(leave test folder blank)
• (YOU CAN INCREASE THE NUMBER OF IMAGES IN BOTH FOLDERS TO GET BETTER ACCURACY)
• From this google drive link https://drive.google.com/drive/folders/1hGk-Eo-ZMQmwt_C4mJ3-
grqXkN5vIT0D?usp=sharing, there is one one folder called as download these images, download the
images from this folder (photos of people wearing mask and not wearing mask)(rename all images in
numerical order to avoid confusion [1.jpg to 200.jpg])
• Label these images(or annotate these images) using an online annotation tool/website called as
“makesense.ai”
• Create two labels mask and no_mask
• Label all the images
• Then click on actions , click on export annotations, select zip package containing yolo format and
then export
• We get a .zip file
• Extract it to a new folder (we get all the annotations as .txt files)
• In yolo v5 folder, in data folder we can find “coco128.yaml”, download it, rename it to custom.yaml
and then make changes to it (changes are mentioned in next step)
• Remove those 80 classes and give two classes (mask and no_mask)
• Add folders train and val in your drive
• Change the train and val folders path inside it (search for these two folders path and then put it in
the custom.yaml file)
• Upload the “custom.yaml” file back to the data folder in yolov5
• Use this command to train your model
• ENABLE GPU
• $ python train.py --img 640 --batch 16 --epochs 50 --data custom.yaml --weights yolov5x.pt --nosave
--cache

• It will run all the epochs and train your model.(weights are created)
• Model name will be last.pt or sometimes best.pt (select any one)

• You can find the created model/weights in this folder (ex-
runs/train/exp5/weights/last.pt)

• Add 5 images in test folder[you can download from google](3 with mask images, 2 without mask
images), upload this folder to drive.
• Then run the below command
• !python detect.py --weights runs/train/exp7/weights/last.pt --img 640 --conf 0.25 --source /content/
test/test1.jpg # (put your image location from test folder,any of the 5 images path)
