# STA221_Project

# Data

- Source: https://www.kaggle.com/datasets/prathamsaraf1389/top-100-reddit-posts-daily-update/data

- Time range of data used: 2023-07-15 to 2024-11-13

- Ranking algorithm: https://github.com/reddit-archive/reddit/blob/master/r2/r2/lib/db/_sorts.pyx

- top 10 posts = top 10 posts ranked by descending score
- hot 10 posts = score * age
  - score = upvotes - downvotes
  - order = log10(max(abs(score), 1))
  - seconds = date - 1134028003
  - hot = round(sign(score) * order + seconds / 45000, 7)

- Score: the number of upvotes minus the number of downvotes of that particular reddit post
- Upvote Ratio: the number of upvotes / total number of votes
- Comment Score: the number of upvotes minus the number of downvotes of each comment

## Preprocessed Data

Posts dataframe

| # | Column             | Non-Null Count | Dtype          |
|---|--------------------|----------------|----------------|
| 0 | post_id            | 4275 non-null  | string         |
| 1 | subreddit          | 4275 non-null  | category       |
| 2 | title              | 4275 non-null  | string         |
| 3 | flair              | 2539 non-null  | string         |
| 4 | score              | 4275 non-null  | int64          |
| 5 | creation_time      | 4275 non-null  | datetime64[ns] |
| 6 | number_of_comments | 4275 non-null  | int64          |
| 7 | upvote_ratio       | 4275 non-null  | float64        |  


Comments dataframe

| # | Column              | Non-Null Count  | Dtype          |
|---|---------------------|-----------------|----------------|
| 0 | post_id             | 983115 non-null | string         |
| 1 | comment_id          | 983115 non-null | string         |
| 2 | comment_content     | 983115 non-null | string         |
| 3 | comment_score       | 983115 non-null | int64          |
| 4 | comment_created_utc | 983115 non-null | datetime64[ns] |

Relations: each post is indentified by the unique primary key post_id. For each post, there could be 0 or more comments under it. The comments are keyed by comment_id.