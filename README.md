# STA221_Project

# Data

Source: https://www.kaggle.com/datasets/prathamsaraf1389/top-100-reddit-posts-daily-update/data

Time range of data used: 2023-07-15 to 2024-11-13

Ranking algorithm: https://github.com/reddit-archive/reddit/blob/master/r2/r2/lib/db/_sorts.pyx

top 10 posts = top 10 posts ranked by descending score
hot 10 posts = score * age
    score = upvotes - downvotes
    order = log10(max(abs(score), 1))
    seconds = date - 1134028003
    hot = round(sign(score) * order + seconds / 45000, 7)

- Score: the number of upvotes minus the number of downvotes of that particular reddit post
- Upvote Ratio: the number of upvotes / total number of votes
- Comment Score: the number of upvotes minus the number of downvotes of each comment