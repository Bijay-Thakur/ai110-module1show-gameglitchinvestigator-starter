# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
  => It looked like an number guessing game, like some simple programming project that we did in our courses but this time, the UI is pretty cool.

- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  => The two bugs in my game was:
  -1- The hint was actually backward. The secret number was lower than what I guessed initially and later on but the hint keeps stating to GO HIGHER, so the hint was backward.
   -2- When I choose the HARD mode the choices reduced by 50, that is actually giving less number choices, so logically that made it easier than before not harder, since the number of attempts remain constant. 
---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
=> Claude Code
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  => AI suggested me about the hint text being hardcoded to 1 and 100 and yeah it was correct, when I go back and change the difficulty level the ranger of choices changed but inside my input window the hint remain constant "1 to 100".
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
  =>Actually I did not find any such suggestion given by AI that was misleading.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  => I rerun the program and try to check the logic again for difficulty level and hint, now it seems to make sense. So, we can say that the error is fixed.

- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  => I switched to Hard mode and submitted a guess that was higher than the secret number. Before the fix, it said 'Go Higher!' — after the fix, it correctly said 'Go Lower!

- Did AI help you design or understand any tests? How?
  => I ask AI to fix my logic error but the test runs I did it myself. The bugs were not that diffult to fix so that I could have done it myself too without relying on AI.
---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
  => In our program, the secret number was generated with a plain random.randint() without any protection, so it run again on every rerun and produce a brand new number each time.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  => Imagine every time you click a button on a webpage, the whole page restarts from scratch and forgets everything. That's Streamlit — each interaction triggers a full re-execution of your Python file. st.session_state is like a sticky notepad that survives those restarts. Anything you store in it stays put between reruns, so your score, your guess count, and your secret number don't get wiped every time the user does something.
- What change did you make that finally gave the game a stable secret number?
  => The fix was wrapping the secret number generation inside a check:
  if "secret" not in st.session_state:
    st.session_state.secret = random.randint(low, high)
  This means the secret is only generated once — the very first time the app loads. On every rerun after that, "secret" already exists in session_state, so the line is skipped and the number stays the same throughout the game.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
- This could be a testing habit, a prompting strategy, or a way you used Git.
  => I want to try to guess the bug myself first, try to fix the logic myself before relying or asking any AI agent, I want to use this technique in my future projects.
  

- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
  => Instead of blindly accepting all the changes made by AI, I will make sure I review it, understand what it is doing, if it is breaking any guardrail, any security issue then only I will accept or make necessary changes.
