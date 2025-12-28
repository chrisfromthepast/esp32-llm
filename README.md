This is a Fork, obviously, I only understand a smal portion of the code that I changed. 
We're standing on the shoulders of Giants here, I just want to have fun with their tools.

I first encountered this approach with this project by Root kid, which is fascinating due to the interesting prompting, and the limited hardware:
https://rootkid.me/works/latent-reflection

check it out that project is very very cool!

I had heard of using the esp32 hardware for machine learning, object detection, and finally started seeing LLM models being shrunk down for the esp32:
David Bannet created a project that is pretty much everything I need, see the project this was forked from

but it doesn't loop and the story starts in the same spot every time. 
SO, there is room for improvement but first we need to port to the version of ESP32 I used, which is the S3 N8R2
this device has more ram, so the menuconfig needs to be changed to match the chip's specs.
This is essential for performance, and since it is hardware dependent, please don't assume that my settings will be optimized for your hardwre


The "Large" Language Model used is actually quite small. It is a 260K parameter [tinyllamas checkpoint](https://huggingface.co/karpathy/tinyllamas/tree/main/stories260K) trained on the [tiny stories](https://huggingface.co/datasets/roneneldan/TinyStories) dataset.





___________________________________________________________________________________________________________________________
building for intel mac
__________________________________________________________________________________________________________________________
I am not using an IDE for this, strctly the terminal IDF.py
setting this up is not so bad, if you are into comand line stuff, but I had to make myself some notes, so I may as well share them:

oh, and, I built this on a intel mac so, if you have another type of machine, adjust accordingly

From: https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/linux-macos-setup.html
do the intall like the website says, then don't forget this:

Step 4. Set up the Environment Variables
The installed tools are not yet added to the PATH environment variable. To make the tools usable from the command line, some environment variables must be set. ESP-IDF provides another script which does that.

. $HOME/esp/esp-idf/export.sh

Project is the project directory you will be working in, you should already be there honestly

cd ~/esp/Project
idf.py set-target esp32s3
idf.py menuconfig

idf.py build

idf.py -p PORT flash

and, of course this page helps too:
https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/establish-serial-connection.html#troubleshooting

To find the port:

ls /dev/cu.*

To view the serial:
Baud rate of 115200 is normal for idf.py projects

screen /dev/cu.device_name 115200

