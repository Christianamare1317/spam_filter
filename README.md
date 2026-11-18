# Break the Spam Filter - Adversarial ML Task

## Results Table

| My message | Model said | Should be | Why it failed |
| :--- | :--- | :--- | :--- |
| `"Cl@im your fr33 g1ft card now"` | `ham` | `spam` | Leetspeak and symbol substitutions (`@`, `3`, `1`) hid keywords from the vectorizer vocabulary. |
| `"C h a t   w i t h   s i n g l e s   n o w"` | `ham` | `spam` | Spacing out letters broke the word tokenization, making the model treat them as random characters. |
| `"Urgent notice regarding your bank account passw0rd"` | `ham` | `spam` | Substituting a number for a letter (`0`) bypassed the keyword match for "password". |
| `"Not free, just confirming lunch at 1pm"` | `spam` | `not spam` | The model reacted aggressively to the trigger word "free" and completely ignored the negation ("not"). |

## Dataset Link
- Dataset Source: [Kaggle SMS Spam Collection Dataset](https://raw.githubusercontent.com/mohitgupta-1O1/Kaggle-SMS-Spam-Collection-Dataset-/master/spam.csv)

## What I Learned
I learned that bag-of-words and TF-IDF classifiers rely heavily on exact keyword matching. Because of this, simple adversarial tricks like leetspeak, spacing, or character substitution can easily bypass baseline spam filters.
