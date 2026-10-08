# Reddit Public Sentiment & Text Processing Pipeline

This repository contains a personal, non-commercial research script designed to process public Reddit posts for text classification and sentiment analysis.

## Overview
The application fetches public post headers and text from specific subreddits via Reddit's official API (OAuth2) using a read-only script. The collected text is processed locally and passed to a classification engine to analyze community pain points and feedback trends.

## Responsible Builder & Privacy Compliance
- **Non-Commercial Use**: This project is strictly for personal educational research and text classification testing.
- **Read-Only Access**: The application only uses `GET` endpoints (`/r/{subreddit}/new`). It does not post, comment, upvote, or perform any write actions.
- **Rate Limit Compliance**: Implements exponential backoff and respects the `User-Agent` header requirements (1 request per 2 seconds max).
- **Data Retention & Privacy**: No user data, usernames, or PII (Personally Identifiable Information) are stored long-term. In accordance with Reddit's Responsible Builder Policy, cached data is periodically cleared, and deleted posts/comments are purged from local caches upon request.

## Architecture
1. Auth: OAuth2 Client Credentials / Script App (`https://oauth.reddit.com`).
2. Ingestion: Python/Node.js script polling public subreddits.
3. Processing: Text sanitization and sentiment categorization.
4. Output: Structured CSV/Spreadsheet export for personal analysis.
