* This is a writeup to the sonic-hide-and-seek challenge from forensics category.*

We get a *hideandseek.wav* file.

This challenge felt very similar to the moonwalk challenge in picoCTF, so i tried to follow the steps given here:
https://mregraoncyber.com/picoctf-writeup-m00nwalk/

We get the follwing:
![Screenshot from 2023-12-17 01-55-19](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/76ea475c-6875-4542-9985-51fdaffacdcd)
> Part2 : \_4r3\_c00l\_

From this , i figured that there must be 3 parts of the flag.

Then i used the software Audacity to generate a spectogram of the .wav file.
Then we get this:
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/d80e7946-7a5f-487b-bab5-9bcb89da02ef)
> Part1 : flag{aud105

Then from the description, the description we get to see there's a little emphasis on the word 'Deep'
>From the apollo moon landing in 1969 to people using Deepfake to fool others, the use of technology has changed. Anyways, use your skills to uncover the deep secrets of the moon landing >from the given data. Adios amigo.

I started searching tools related to 'Deep' and having the word 'Deep' in them.
I came across this software called DeepAudio. Putting the audio in it, we get '3.txt'
After opening the .txt file , we get this:

> Part3: 4r5n't\_th3y?}

Hence the flag is ```flag{aud105\_4r3\_c00l\_4r5n't\_th3y?}```

Happy hacking!
