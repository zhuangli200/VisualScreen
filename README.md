**Introduction:**

This bash script allows users to inspect the motion-corrected EM images (*.mrc).
It uses eman2 to convert mrc images to png, start the image navigator for users to navigate images, and record the images user deleted.
The script works in a continuing mode, which means you only have to inspect the newly imported images.

**Steps:**
1. Make sure the eman2 is callable, otherwise it fails. 
2. cd to the folder containing all the motion-corrected EM images(*.mrc). 
3. Start the program visual_screen.sh, and it takes about 1 sec to convert 3 mrc image to png with multithreading. After the conversion, a minions image will pop out as a flagger. 
4. You start to navigate the images by "left/right arrow" keys, and mark bad images by deleting the png files with "Delete" keys. After  a round of inspection, you go back to the minions image, which is the time you close the image viewer. After this, three files will be generated, namely good.list bad.list batch.list. If you want to quit this boring job, use Ctrl-C in the terminal to kill the image viewer, but if you only close the window, the program will assume you finished the inspection.
5. If there are new images imported into this folder, you can run the visual_screen.sh again. The program will only convert the new images for you to inspect.
6. Use the final bad.list file to filter out the bad images from a star file. 
For example,  `grep -v -f path/to/bad.list particles.star > good.star`