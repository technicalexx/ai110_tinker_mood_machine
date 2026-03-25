# The Mood Machine

---

## _The Implementation and Reflection is in TF_Implementation.md_

---

## _Summary:_

The main concept students needed to understand in this Tinker was how a simple mood classification system works from start to finish, including preprocessing text, scoring it based on rules, and converting that score into a final label. Students also needed to understand that both the rule based and ML versions are heavily impacted by the data and labels they create. One of the biggest likely struggles is handling posts that are ambiguous, sarcastic, slang-based, emoji-based, or show mixed emotions, since those cases are not always easy even for us to label consistently. AI was helpful for understanding the starter code, brainstorming dataset examples, and suggesting simple implementation ideas, but it could also be misleading when its suggestions were too repetitive, too generic, missing simple edge cases, or more complicated than what the project actually needed. A good way to guide students without giving away the answer is to ask them to walk through what happens to one sample post from input to final label and explain where the model may be going wrong. The ML comparison also helps show that higher accuracy does not always mean the model is truly better, especially when it is being tested on the same small dataset it trained on.

---

The Mood Machine is a simple text classifier that begins with a rule based approach and can optionally be extended with a small machine learning model. It tries to guess whether a short piece of text sounds **positive**, **negative**, **neutral**, or even **mixed** based on patterns in your data.

This lab gives you hands on experience with how basic systems work, where they break, and how different modeling choices affect fairness and accuracy. You will edit code, add data, run experiments, and write a short model card reflection.

---

## Repo Structure

```plaintext
├── dataset.py         # Starter word lists and example posts (you will expand these)
├── mood_analyzer.py   # Rule based classifier with TODOs to improve
├── main.py            # Runs the rule based model and interactive demo
├── ml_experiments.py  # (New) A tiny ML classifier using scikit-learn
├── model_card.md      # Template to fill out after experimenting
└── requirements.txt   # Dependencies for optional ML exploration
```

---

## Getting Started

1. Open this folder in VS Code.
2. Make sure your Python environment is active.
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the rule-based starter:

   ```bash
   python main.py
   ```

If pieces of the analyzer are not implemented yet, you will see helpful errors that guide you to the TODOs.

To try the ML model later, run:

```bash
python ml_experiments.py
```

---

## What You Will Do

During this lab you will:

- Implement the missing parts of the rule based `MoodAnalyzer`.
- Add new positive and negative words.
- Expand the dataset with more posts, including slang, emojis, sarcasm, or mixed emotions.
- Observe unusual or incorrect predictions and think about why they happen.
- Train a tiny machine learning model and compare its behavior to your rule based system.
- Complete the model card with your findings about data, behavior, limitations, and improvements.
- The goal is to help you reason about how models behave, how data shapes them, and why even small design choices matter.

---

## Tips

- Start with preprocessing before updating scoring rules.
- When debugging, print tokens, scores, or intermediate choices.
- Ask an AI assistant to help create edge case posts or unusual wording.
- Try examples that mislead or confuse your model. Failure cases teach you the most.
