**Introduction:**

This bash script allows users to inspect the motion-corrected EM images (*.mrc).
It uses eman2 to convert mrc images to png, start the image viewer for users to navigate images, and mark those images the user deleted as bad. The script works in a skipping-inspected way, which means you only have to inspect the newly imported images.

**Steps:**
1. Make sure the eman2 is callable, otherwise it fails. 
2. cd to the folder containing all the motion-corrected EM images(*.mrc). 
3. Start the program visual_screen.sh, and it takes about 1 sec to convert 3 mrc image to png with multithreading. After the conversion, a minions image will pop out as a flagger. 
4. You start to navigate the images by "left/right arrow" keys, and mark bad images by deleting the png files with "Delete" keys. After  a round of inspection, you go back to the minions image, which is the time you close the image viewer. After this, three files will be generated, namely good.list, bad.list and batch.list. The bad.list records the marked bad imaged, and the batch.list record the new batch of imported files. If you want to quit this tedious work, use Ctrl-C in the terminal to kill the image viewer.
5. Run the scrirpt repeatly to inspect the newly imported images.
6. Use the final bad.list file to filter out the bad images from a star file. 
For example,  `grep -v -f path/to/bad.list particles.star > good.star`