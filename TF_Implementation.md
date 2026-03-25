---
## Parts that Can Be Confusing for Students:

- How to handle posts that are hard to label and can be confusing (sarcasm, mixed emotions, etc., unclear messasing, subjective meaning when one person can label it as positive, while someone else can label it as neutral/negative, etc.)

- What happens at every step (preprocessing, scoring, labeling) and how it flows throughout the process (input text -> preprocess it -> score it -> turn scores into labels)

-
---

## Ways to Guide Students Without Giving the Answer:

- You can start with understanding the basics of the project. Use Copilot as your assistant or instructor to better understand what you were provided. For example, prompt it to help you understand in simple words:
  - how sample_post and true_labels relate to each other (and why they must have the same length)
    OR
  - what is the role of preprocess(), score_text(), predict_label() in analyzer_mood.py in the overall flow of the system?
  - how any sample post flows from start to finish through the model? What are the main steps?
- Try to rainstorm the ideas using Copilot of additional posts and corresponding labels you can add to train and test you model
- Did you think about all possible edge cases, like sarcasm, emojis, posts that have both positive and negative words?
- What about negations?
- Can you use Copilot to get more ideas and check whether you cover all possible edge cases?

---

## Things for Students to Understand/Realize:

## What They Have in the Starter Code and What's Missing:

- Initial dataset (starter moods, sample posts, matching labels) -> needs to be expanded
- Every post has 1 label -> Must keep it that way when adding new posts
- In mood_analyzer.py:
  - preprocess() exists, but it is basic -> can be improved
  - score_text() needs to be implemented
  - predict_label() needs to be implemented
  - explain is partially implemented (it is optional) -> can be improved

---

## _Implementation:_

### PROMPT 1 (something that could help students to better understand what they were provided):

Look at dataset.py. Can you explain in simple words how SAMPLE_POSTS and TRUE_LABELS relate to each other, and why they must always have the same length?

![Dataset Explanation](screenshots\im1.png)

### PROMPT 2:

Look at mood_analyzer.py. Can you explain the role of preprocess, score_text, and predict_label in the overall flow of this project?

![Dataset Explanation](screenshots\im2.png)

### PROMPT 3 (brainstorming ideas for new posts and labels):

Can you suggest 10 - 15 short realistic social-media-style posts for a mood classification dataset, including slang, emojis, sarcasm, and mixed feelings?

![Dataset Explanation](screenshots\im3.png)

=> Copilot included imojis and slang in every single one of them => the prompt needed to be adjusted to get more diverse posts.

Final posts that were added to dataset.py:

![Dataset Explanation](screenshots\im4.png)

![Dataset Explanation](screenshots\im5.png)

### PROMPT 4 (Improving preprocess() method):

Initial improvement of preprocess() method:

![Dataset Explanation](screenshots\im6.png)

=> Good implementation, but can still be improved a little more

Look at preprocess() in mood_analyzer.py. I want a simple beginner friendly improvement that lowercases, removes common punctuation, keeps emojis if possible, and returns tokens. Does this implementation make sense?

![Dataset Explanation](screenshots\im7.png)

=> Better implementation (in my opinion) in this version because it removes all the unnecessary punctuation without specificaly listing it and keeps emojis.

![Dataset Explanation](screenshots\im8.png)
