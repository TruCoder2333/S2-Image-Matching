This is a realization of a task to match Sentinel-2 satelite imagery of the same area in different seasons

The imagery is manually downloaded from the https://browser.dataspace.copernicus.eu

I decided to download 2(more in the future to improve performance) picture of the same area in winter and summer

The image is then split into smaller images, as the resolution is around 10k by 10k, this picture can be split in many different pictures that can be analyzed for image matching
I decided to go with 256 by 256, 512x512 or other resolutions might work better
After the split we have around 1800 images 256 by 256 for each season

I decided to use a ready made D2 net model https://github.com/mihaidusmanu/d2-net, works wonderfully, though needs to be fine-tuned for this case for ideal performance
Average matching score is 0.04 which is not too good at all but we can see from model inference file and demo that it is because of the few matching keypoints found on the images themselves
the actual keypoints are pretty solid
I am no expert in image matching, but when I tested SIFT for the same task it was pretty awful, I can provide notebooks with that if needed 
If a model is actually fine tuned on satelite imagery, and if we had around 5000 image pairs I think it would do pretty good job overall, unfortunate that I do not have a lot of time to do this for the test task

D2 model - https://github.com/mihaidusmanu/d2-net
model weigths -  https://dusmanu.com/files/d2-net/d2_ots.pth -O models/d2_ots.pth
                 https://dusmanu.com/files/d2-net/d2_tf.pth -O models/d2_tf.pth
                https://dusmanu.com/files/d2-net/d2_tf_no_phototourism.pth -O models/d2_tf_no_phototourism.pth
data - https://drive.google.com/drive/folders/18TxCYbi-Kgn9n58--glb112-Ncpbj1yB?usp=sharing
