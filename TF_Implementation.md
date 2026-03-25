## Summary:

The core concept students needed to understand in this Tinker was how a simple mood classification system works from start to finish, including preprocessing text, scoring it based on rules, and converting that score into a final label. Students also needed to understand that both the rule based and ML versions are heavily impacted by the data and labels they create. One of the biggest likely struggles is handling posts that are ambiguous, sarcastic, slang-based, or show mixed emotions, since those cases are not always easy even for humans to label consistently. AI was helpful for understanding the starter code, brainstorming dataset examples, and suggesting simple implementation ideas, but it could also be misleading when its suggestions were too repetitive, too generic, or more complicated than what the project actually needed. A good way to guide students without giving away the answer is to ask them to walk through what happens to one sample post from input to final label and explain where the model may be going wrong. Overall, this activity is useful because it shows students that even very small AI systems can become messy quickly, and that understanding failures is just as important as making the model work.

---

## Where AI Was Helpful vs Misleading:

### Helpful:

- AI was helpful for understanding the relationship between `SAMPLE_POSTS` and `TRUE_LABELS`.
- It was also helpful for explaining the overall flow of the project, especially how `preprocess()`, `score_text()`, and `predict_label()` work together.
- It helped brainstorm ideas for additional dataset examples, especially edge cases like sarcasm, slang, emojis, and mixed emotions.
- It was useful for suggesting simple implementation ideas for preprocessing, negation handling, and label mapping.
- It was also helpful when checking whether an implementation idea made sense before adding it to the code.

### Misleading:

- AI could be misleading when it gave suggestions that were too repetitive or unrealistic, especially when brainstorming posts.
- Sometimes it suggested more advanced or more complex solutions than the activity really needed.
- It could make something sound correct even when it still needed to be verified against the actual code and project goals.
- Some suggestions were technically valid, but not the best choice for a beginner-friendly implementation.
- It could also make students feel like they should solve everything right away, instead of first building a simple version and then improving it step by step.

---

## Parts that Can Be Confusing for Students:

- How to handle posts that are hard to label and can be confusing, such as sarcasm, mixed emotions, unclear messaging, slang, emojis, or cases where one person may label a post as positive while someone else may label it as neutral or negative.

- Understanding what happens at every step of the process and how everything flows together:
  `input text -> preprocess it -> score it -> turn score into a label`

- Understanding that `SAMPLE_POSTS` and `TRUE_LABELS` are parallel lists, and that every post must always have exactly one matching label.

- Figuring out why the model may predict something incorrectly even when the code is technically working.

- Understanding the difference between `neutral` and `mixed`.

- Realizing that the model does not understand meaning the way humans do. It only follows the rules and vocabulary that were given to it.

- Understanding why the ML model may behave differently from the rule based model, even when both use the same dataset.

---

## Ways to Guide Students Without Giving the Answer:

- Start by helping them understand the basics of the project. Encourage them to use Copilot as an assistant to better understand what they were given, instead of just using it to generate code.

- For example, ask them to prompt Copilot to explain in simple words:
  - how `SAMPLE_POSTS` and `TRUE_LABELS` relate to each other and why they must always have the same length
  - what the role of `preprocess()`, `score_text()`, and `predict_label()` is in `mood_analyzer.py`
  - how one sample post flows from start to finish through the model

- Ask guiding questions such as:
  - What words in this post affected the score?
  - Why do you think the model chose this label?
  - What happens if there is a negation like `not happy`?
  - Is this post really neutral, or is it mixed?
  - What word or phrase is the model missing here?

- Encourage them to brainstorm additional posts and labels with Copilot, but remind them to reject suggestions that sound repetitive, unrealistic, or unclear.

- Ask them whether they have thought about edge cases such as sarcasm, slang, emojis, and posts that contain both positive and negative moods.

- If they are stuck, guide them to print tokens, scores, or intermediate results instead of jumping straight to a full new solution.

---

## Things for Students to Understand/Realize:

- The implementation does not need to be perfect right away. A big part of the activity is understanding where and why the model fails.

- There is no need to immediately support every possible label or edge case. For example, students can first implement `positive`, `negative`, and `neutral` and make sure those work properly before trying to handle `mixed`.

- A model can be working correctly according to its own rules and still produce a wrong or weak prediction.

- Labels are not always objective. Some posts are naturally ambiguous, and disagreement between humans is normal.

- The dataset matters a lot. The words and labels students add directly shape how both the rule based and ML versions behave.

- High accuracy does not automatically mean the model is actually good. With a very small dataset, a model may still fail badly on realistic examples.

- AI suggestions should always be treated as ideas to inspect and verify, not as the final answer.

---

## What They Have in the Starter Code and What’s Missing:

- An initial dataset with starter mood words, sample posts, and matching labels  
  -> this needs to be expanded

- A one-to-one relationship between posts and labels  
  -> students must keep it that way when adding new posts

- In `mood_analyzer.py`:
  - `preprocess()` already exists, but it is basic  
    -> it can be improved
  - `score_text()` needs to be implemented
  - `predict_label()` needs to be implemented
  - `explain()` is partially implemented and optional  
    -> it can also be improved

- In `main.py`:
  - the evaluation logic is already there
  - the batch demo is already there
  - the interactive loop is already there

- In `ml_experiments.py`:
  - the ML workflow is already provided
  - students mainly need to run it, compare its behavior, and reflect on how it differs from the rule based approach

---

## _Implementation:_

### PROMPT 1 (something that could help students better understand what they were provided):

Look at `dataset.py`. Can you explain in simple words how `SAMPLE_POSTS` and `TRUE_LABELS` relate to each other, and why they must always have the same length?

![Dataset Explanation](screenshots/im1.png)

---

### PROMPT 2:

Look at `mood_analyzer.py`. Can you explain the role of `preprocess`, `score_text`, and `predict_label` in the overall flow of this project?

![Mood Analyzer Flow Explanation](screenshots/im2.png)

---

### PROMPT 3 (brainstorming ideas for new posts and labels):

Can you suggest 10 to 15 short realistic social-media-style posts for a mood classification dataset, including slang, emojis, sarcasm, and mixed feelings?

![Brainstorming New Posts](screenshots/im3.png)

=> Copilot included emojis and slang in almost every single example, so the prompt needed to be adjusted to get more diverse posts.

Final posts that were added to `dataset.py`:

![Updated Sample Posts](screenshots/im4.png)

![Updated True Labels](screenshots/im5.png)

---

### PROMPT 4 (improving `preprocess()` method):

Initial improvement of `preprocess()` method:

![Initial Preprocess Suggestion](screenshots/im6.png)

=> Good implementation, but it could still be improved a little more.

Look at `preprocess()` in `mood_analyzer.py`. I want a simple beginner-friendly improvement that lowercases, removes common punctuation, keeps emojis if possible, and returns tokens. Does this implementation make sense?

![Improved Preprocess Prompt](screenshots/im7.png)

=> Better implementation in my opinion, because it removes unnecessary punctuation without having to list each symbol manually and still keeps emojis.

![Final Preprocess Implementation](screenshots/im8.png)

---

### PROMPT 5 (implementing `score_text()` method):

Look at `score_text()` in `mood_analyzer.py`. I want a simple beginner-friendly implementation that scores positive and negative words and handles simple negation like `not happy` and `not bad`. Does this approach make sense?

![Score Text Suggestion](screenshots/im9.png)

=> This looks like a pretty good implementation and it is simple enough for now.

=> One small improvement could be adding `"no"` as another negation word, since it could also potentially change the mood:

![Negation Improvement](screenshots/im10.png)

---

### PROMPT 6 (`predict_label()` method implementation):

Look at `predict_label()` in `mood_analyzer.py`. I want a simple beginner-friendly version that maps positive score to positive, negative score to negative, and zero to neutral. Does this fit the current `score_text()` logic?

![Predict Label Suggestion](screenshots/im11.png)

=> This looks like a good initial implementation of the `predict_label()` method.

=> After adding it to `mood_analyzer.py`, I ran `python main.py` to test the implementation:

![Rule Based Output](screenshots/im12.png)
