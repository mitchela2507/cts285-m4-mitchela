# NOTES: Three Layers

Your name: TODO

Fill each TODO. Write plain, short sentences. Do not delete the headings.

## Part 1. Predict, then find [S1]

Write your prediction before you open any code. Then search. In the last column, write each file the search finds and what that file does.

| Action | Search word | My prediction (file) | Files found and what each does |
|---|---|---|---|
| Prints "Not yet. Try again." | `Not yet` | app.py | No files were found because I changed the message in app.py from "Not yet. Try again." to "EEE -- Try again." |
| Decides that the second miss shows the answer | `reveal` | dataman/logic.py | dataman/logic.py decides when to reveal the answer. app.py displays the revealed answer. tests/test_logic.py checks that the second miss reveals the answer. |
| Saves one attempt | `save_attempt` | dataman/store.py | dataman/store.py saves attempts in memory or in a JSON file. dataman/logic.py calls save_attempt when an answer is submitted. |
| Refuses the 11th problem | `SetFull` | dataman/logic.py | dataman/logic.py defines SetFull and enforces the 10-problem limit. app.py catches SetFull and displays a refusal message. tests/test_logic.py tests the rule. exercise/bank.py defines SetFull for the practice exercise. exercise/test_bank.py tests the exercise rule. |

Search command: `grep -rn "SEARCH WORD" --include=*.py .`

## Part 2. What the program remembered [S1]

After the restart, what did the program remember? The program remembered my previous incorrect answer, 55, and continued with Try 2.

Which file made that possible? The dataman_store.json file saved the attempt so the program could load it after restarting.

## Part 3. The interface change [S1]

What did you change in `app.py`? I changed the retry message from "Not yet. Try again." to "EEE -- Try again."

Why did no test need to change? The tests check the program's logic and results, not the wording of the retry message.

## Part 4. The rule in the real library [S2]

The same 10-problem rule exists in the real library. Write the file and the function name. The file is dataman/logic.py, and the function is MemoryBank.add_problem().

## Part 5. The red test [S2]

With the rule removed from the library, what did the screen show? The screen showed "Added. Set holds 11." because the program allowed the 11th problem.

With the rule removed, which test failed? The test_eleventh_problem_is_refused test in tests/test_logic.py failed.

## Part 6. The data swap [S2]

A real database would replace which file? A real database would replace dataman/store.py.

Which file holds the rules and does not change when the database changes? The dataman/logic.py file holds the rules and does not need to change.

## Reflection [S2]

Write 3 to 5 sentences. Pick one layer. Say what you changed in it. Say what stayed the same in the other two layers. I changed the interface layer by changing the retry message in app.py to "EEE -- Try again." I also changed the default storage option in app.py from memory to json. The business logic in dataman/logic.py stayed the same, and the data layer in dataman/store.py stayed the same. The program still follows the same rules, but the saved attempts remain available after restarting.

## Beta feedback (optional)

This bonus is a beta test. Which step took longer than its time? What confused you? Write it here. Your answer helps the next class. The search and testing steps took longer than expected because I had to check different files to understand which layer handled each task. It was also a little confusing to understand the difference between the interface, business logic, and data layers.
