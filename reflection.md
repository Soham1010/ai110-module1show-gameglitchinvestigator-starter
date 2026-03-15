# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start
  (for example: "the hints were backwards").

The game looked good, it was attractive with a bold title and use of emoji, and some features too, but somethings seemed off, like the reverse logic was not particularly right, as the higher lower logic was inverted, and  whenever we pressed submit, we the game would roll a dice and pick a new secret number.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

I used gemini 3 flash, becuase it was faster, teammates used claude and gpt, which was interesting to see.
I suggested during the debuging to antigravity editor (the editor I used for editing) I told i somethign was not right about secret number, and it told it wasn't being protected by Streamlit's session state, something new that I learned. Later implemented a suggestion specifically `if "secret" not in st.session_state:` to lock its value, instead of chaning it wherenver. I verified it manually by seeint the developer debug info panel and checked if the secret changed every time I clicked the button, and it worked the way it should, the number stayed exactly the same across multiple guesses.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?


I verified it with checking 2 things, first running the default set of pytests given, to make sure the logic was intact and working, and I verified things worked, by manually testing it.

I ran `python -m pytest tests/test_game_logic.py`, which  showed an AssertionError, that happened because the new function that was implemented returend a tuple, insteaed of string, so I fixed it. This showed that even though the logic was overall better, it wasn't aligned to the existing rules of the game.

Also I think understanding why the pytest crashed, and what specific error it throwed was really helpful too, that made me understand how the test works. After updating the test cases, the test finally ran and the test passed message was there. 


## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

I'd say its a bit differnet than normal python script, where the normal one is run only once, the streamlit reruns everytime something happens on the webpage making it more dynamic.

And for the session state, its a way to preserve the information between alternate script execution, as at every rerun the script is basically ran again, and previous data is forgotten, what session state does is if a script forgets everything, the data or what we call state is saved, which allows you to maintain continuity and rememeber or recall previous actions or values of some variables tc.

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

I think the debug feature is really useful, especially in the UI is really helpful and a must to use if working with bigger projects, as it exposes hidden session states like secret number and attempt counts, which is incredibly useful. Furthermore, I think not keeping it in agent mode, and planning mode, to better understand what is going on, instead of vibe code, which was responsibel for a few failures intiially, so I'll make a note to keep the lesson. I used to think, using ai only means vibe coding, but it can be troublesome like that. I feel like reviewing things can make life so much easier especially when working with some important data.