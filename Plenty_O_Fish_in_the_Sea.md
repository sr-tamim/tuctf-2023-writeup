# Plenty O Fish in the Sea

### Challenge
You have embarked on a quest to find the One Bit! Your first step is to find the scattered pieces of the treasure map on this here abandoned island!

[**lost_map.zip**](https://github.com/sr-tamim/tuctf-2023-writeup/files/13537962/lost_map.zip)

#### Point = 50, Level = Easy

## How I got the flag
- I extracted the zip file and there was a log file inside it. I opened the log file in text editor and there was so many texts.

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/1d8ae99d-c673-4496-8e5e-5d6cd7c955bf)

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/3ac77945-f4c4-4f9b-abf9-fc379bfaab66)

- There are exactly 18531 lines in that file. Interesting thing is most of the lines are common and duplicate.
- So I searched for a line and replaced with empty string. After repeating this several times, there is nothing left except the flag.

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/82e466f2-7e52-4985-a203-5ae1b274b3df)

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/17ffcf3e-abcf-46a6-892f-5441b7dfa729)

- Now I replaced all the newlines with empty string in VS Code and now parts of the flag got closer to each other.

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/1fb579d7-f197-4147-a9b0-dd89f5fa4a3b)

- It is an URL-encoded string. Here, `%7B` represents `{` and `%7D` represents `}`. Similarly, `%21` represents `!`, `%40` represents `@`.
- I decoded the string to normal text and got the flag.

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/93ebaad9-d14d-479a-8da3-f9bcaa4ec9fd)

### Regards
[**SR Tamim**](https://sr-tamim.vercel.app)
