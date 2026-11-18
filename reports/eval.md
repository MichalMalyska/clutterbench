# Grader eval

Ground truth: Adam's reviews of 24 runs. dev = 3 articles used to write prompts; test = 3 held-out articles.

- labelAcc: % of elements given the same colour as Adam (pooled). runAcc: same, averaged per run so busy graphics do not dominate.
- cutAcc: % agreement on red vs not-red. scoreMAE / scoreRho: error and rank correlation of the 0-10 clutter score.
- shareMAE: error in clutter share, in points. missing: runs where Adam noted missing or unreadable information that the grader also flagged, and false alarms.
- seconds / tokens / usd: mean per graded run (usd is the CLI's API-equivalent figure; runs are on subscription).

## test (12 runs, 12 with element labels)

| grader | runs | labelAcc | runAcc | cutAcc | scoreMAE | scoreRho | shareMAE | missing | seconds | tokens | usd |
|---|---|---|---|---|---|---|---|---|---|---|---|
| luna-low-v4 | 12 | 77.7 | 83.6 | 81.8 | 1.67 | 0.97 | 11.1 | 1/2 caught, 0 false | 9 | 9762 | – |
| consensus-v4 | 12 | 80.9 | 82.8 | 84.9 | 1.33 | 0.91 | 5.4 | 1/2 caught, 1 false | – | – | – |
| haiku-low-v4-b | 12 | 80.9 | 82.7 | 85.1 | 1.33 | 0.92 | 5.5 | 1/2 caught, 1 false | 13.7 | 29275 | 0.004 |
| haiku-low-v4 | 12 | 77.3 | 79.6 | 79.3 | 1.33 | 0.91 | 7.6 | 1/2 caught, 1 false | 13 | 29332 | 0.004 |
| sonnet-low-v4 | 12 | 76.3 | 76.4 | 81.6 | 1.42 | 0.84 | 12.6 | 0/2 caught, 1 false | 8.7 | 26185 | 0.057 |
| haiku-low-v5 | 12 | 58.2 | 73.7 | 80.1 | 1.08 | 0.88 | 13.7 | 2/2 caught, 2 false | 14.1 | 30637 | 0.004 |
| consensus-v5 | 12 | 57.7 | 73 | 59.9 | 1.33 | 0.86 | 18.1 | 0/2 caught, 1 false | – | – | – |
| haiku-low-v5-b | 12 | 57.4 | 72.3 | 60.2 | 1.33 | 0.88 | 17.7 | 0/2 caught, 2 false | 13.3 | 30498 | 0.002 |
| sonnet-low-v5 | 10 | 57.8 | 68.9 | 62.9 | 1.7 | 0.73 | 22.4 | 0/2 caught, 1 false | 9.2 | 28541 | 0.066 |

## dev (12 runs, 10 with element labels)

| grader | runs | labelAcc | runAcc | cutAcc | scoreMAE | scoreRho | shareMAE | missing | seconds | tokens | usd |
|---|---|---|---|---|---|---|---|---|---|---|---|
| consensus-v4 | 12 | 89.6 | 93.6 | 90 | 0.75 | 0.92 | 6.5 | 1/1 caught, 0 false | – | – | – |
| haiku-low-v4-b | 12 | 89.6 | 93.6 | 90 | 0.75 | 0.92 | 6.5 | 1/1 caught, 0 false | 10.8 | 27891 | 0.004 |
| consensus-v5 | 12 | 89.6 | 93.6 | 90.5 | 0.75 | 0.92 | 6.2 | 1/1 caught, 0 false | – | – | – |
| luna-low-v4 | 12 | 89.1 | 93.5 | 91 | 0.5 | 0.95 | 6.7 | 0/1 caught, 0 false | 10 | 8201 | – |
| haiku-low-v5 | 12 | 89.1 | 93.3 | 90 | 0.83 | 0.89 | 5.9 | 1/1 caught, 1 false | 13 | 29622 | 0.004 |
| haiku-low-v5-b | 12 | 88.6 | 93 | 89.6 | 0.92 | 0.92 | 6.3 | 1/1 caught, 0 false | 12.3 | 29440 | 0.002 |
| haiku-low-v4 | 12 | 89.1 | 92.8 | 89.6 | 1 | 0.89 | 7.7 | 1/1 caught, 0 false | 11.2 | 28032 | 0.003 |
| sonnet-low-v4 | 12 | 87.2 | 92.1 | 90 | 0.58 | 0.94 | 6.4 | 1/1 caught, 0 false | 8 | 25201 | 0.055 |
| sonnet-low-v5 | 7 | 85 | 88.7 | 88.2 | 0.71 | 0.91 | 9.5 | 1/1 caught, 0 false | 9.4 | 26831 | 0.062 |
