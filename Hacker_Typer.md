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
  
- As we can see there is a function which sends a POST request to */check_word* api with *word* in payload. It gets three properties in response.

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/44bee191-e0b0-4f21-bbcb-f1d074899ac2)
  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/4e8424a9-3381-4b0e-8daa-d6402e70d705)

- Here the next word is in the response of the submission of the previous word.
- So, I wrote a recursive function which sends a POST request to */check_word* api and the function calls itself again after getting next word in response.

  ```javascript
  function getfetch(word) {
        var wordInput = word;
        var xhr = new XMLHttpRequest();
        xhr.open("POST", "/check_word");
        xhr.setRequestHeader(
          "Content-Type",
          "application/x-www-form-urlencoded"
        );
        xhr.onload = function () {
          var wordElement = document.querySelector('strong[name="word-title"]');
          var speedElement = document.querySelector(
            'strong[name="speed-title"]'
          );
          var streakElement = document.querySelector(
            'strong[name="streak-title"]'
          );
          var statusElement = document.querySelector(
            'strong[name="status-title"]'
          );
          var inputElement = document.getElementsByName("word")[0];
          if (xhr.status === 200) {
            var response = JSON.parse(xhr.responseText);
              console.log(response);
            response.next_word && getfetch(response.next_word);
          } else {
            statusElement.textContent = "Session Expired";
            inputElement.focus();
          }
        };
        xhr.send("word=" + encodeURIComponent(wordInput));
  }
  ```

- This function done everything for me. I called this function once in browser console and after awhile the streak became 150 and I found the flag.
  
  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/39913864-328d-4103-874b-6d9bd4854954)

  ![image](https://github.com/sr-tamim/tuctf-2023-writeup/assets/86656406/116fa142-4800-4920-9c90-59d0df8abcfb)

