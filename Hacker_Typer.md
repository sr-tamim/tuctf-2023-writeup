## Challenge
Only the most leet hackers can type faster than my bot. Can you beat it?

https://hacker-typer.tuctf.com

#### Point = 50, Level = Easy

## How I got the flag
- I visited the webpage and there was something like typing speed calculator. I have to write the words correctly as fast as I can and maintain the streak upto 150.
  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/438d5ac1-062c-400b-a6e9-5777a4d48280)

- I tried to write some words and I figured out that 150 streak is not gonna easy work for me.
- I opened the network tab to see how it is measuring the speed and streak.
  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/f809794e-b958-4a28-90ea-6d50f8f859db)
- As we can see there is a function which sends a POST request to */check-word* api.
