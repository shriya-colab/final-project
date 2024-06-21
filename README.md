# final-project
Project name: detect-mask

Description: The purpose of this project is to detect whether someone is wearing a mask or not
to enter any facility because wearing a mask promotes safety. The code can be utilized on any
image to detect someone wearing a mask or not and with some further commands
this can aid in restricting their entry into the facility by giving a message like “Entry is Restricted”
OR take it a little further and aid in “Opening the door or not”.
This is the image of my output after testing and completing all the steps for a human wearing a mask: https://drive.google.com/file/d/1VhMlTh77a93Iw4Q9otKb2y7imCyE-isK/view?usp=sharing

Algorithm: The concept of this project is based on AI image recognition and Training the
network. We train the network to recognize the face mask and anytime the network sees a
a person's face the code will run to see if they have a mask or not by testing the image. I have a with_mask folder and a without_mask folder. 

Running the project: This whole project is done in a few steps as listed below.

In order to start this process, first we need to find datasets (mostly filled with images), which can be found in Kaggle. After finding your dataset with images, download them and it should be saved somewhere in your file (I did people with a mask and without a mask) and make sure that the files are dragged in whatever program you are using, and make sure to unzip.
In google colab  run git clone https://github.com/dusty-nv/pytorch-classification.git
Then also run cd pytorch-classification; pip install -r requirements.txt
Classification: Then you should create 3 folders called train, test, and val (I did this in both google colab and vs code). You can do this by typing in a specific code which is shown in the organizer.py folder in my repository, and if you do this on google colab then it will create those three folders and each folder will have images from your data set, and if that doesn’t happen then just put some images into each folder, and also make sure to unzip the image files if you haven’t already. This classifies the images into 3 folders.
Training: Now it’s time to train these images. (I used google colab because there is more space) . So type cd /content/pytorch-classification; python3 train.py --model-dir=models data/data
And then for ONNX exportation do  pip install onnx onnxruntime
Then cd /content/pytorch-classification;python3 onnx_export.py --model-dir=models. 
Then type in exactly what is in the following link: https://drive.google.com/file/d/16XA2Zckt15LtqSshFcsbeqLgMoPrZDMg/view?usp=sharing
Next type in exactly what is in the following link: https://drive.google.com/file/d/1KlxexPFLc_lWhVmnhaP1B2JVO-Evm5XM/view?usp=sharing
Then type exactly what is in the following link: https://drive.google.com/file/d/1H3uXsduhy_LjdUyrkjIaE3gc-vPq-oPW/view?usp=sharing
This will give you a ONNX file in return which you would have to download then drag it into VS Code into your folder and file. 
Now that we are done with training, now we have to test the images. In VS code first navigate to your jetson inference by typing cd jetson-inference/python/training/classification.
Then set the NET and DATASET variables. So type NET=models/(first file_second file) and then also type DATASET=data/(first file_second file).
Make a place for our output files to go and then in order to test one single image, type in  imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/<Name of Image>/.jpg .jpg
If you want to test all the images instead in one or both of your files then just type in imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/<File 1 or 2 Name> $DATASET/test_output_<File 1 or 2 Name>
You can finally view the results! To see them, go to jetson-inference → python → training → classification → data, and you should see your output image or file depending on whether you tested a whole file or image. The image(s) will show AI’s detection on whether the human is wearing a mask or not.  I uploaded my result/output in my GitHub repository called detectmask.jpg, and it is also linked right after the project description.


Link to video: https://drive.google.com/file/d/1EjfLEpwAik1rQDP6UG9LXsU_JbhSO4W_/view?usp=sharing
