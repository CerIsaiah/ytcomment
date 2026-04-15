# CommentMarketer

A bot to automatically comment, like, or dislike YouTube videos based on a search query.

> **Note:** If a video has already been liked or disliked, the script will skip it and will not add a comment.

---

## YouTube API Quota

YouTube limits the number of comments, likes, dislikes, and queries you can send. A `403` error will be raised when this limit is reached. See the [YouTube API quota documentation](https://developers.google.com/youtube/v3/getting-started#quota) for more details.

---

## Setup

1. Create a [Google Cloud Console](https://console.cloud.google.com/) project (free)
2. Create an **OAuth 2.0 credential** in the project
3. Download the OAuth credentials file into the project folder and rename it `secret.json`
4. Install [Python](https://www.python.org/downloads/)
5. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

```bash
python main.py --query "my query" [--comments "My comment" "My other comment" --rating like --size 50 --sleep 20]
```

### Arguments

| Argument | Required | Default | Description |
|---|---|---|---|
| `--query` | ✅ Yes | — | The search query used to find videos |
| `--comments` | No | — | One or more comments to randomly post on each video |
| `--rating` | No | `like` | Rate the video: `like` or `dislike` |
| `--size` | No | `50` | Number of videos to process (min: 0, no max) |
| `--sleep` | No | `30` | Pause in seconds between each action (helps avoid quota limits) |
| `--region` | No | — | Restrict results to a specific country (two-letter code, e.g. `US`) |

### Example

```bash
python main.py --query "lo-fi music" --comments "Great video!" "Love this" --rating like --size 20 --sleep 15 --region US
```

---

## Authentication

When you run the script, it will prompt you to:

1. Open a URL in your browser
2. Grant Google account access
3. Copy the token Google returns
4. Paste it into the console

---

## Notes

- Comments are selected **randomly** from the list you provide via `--comments`
- The `--sleep` flag is useful for long-running sessions to avoid hitting the API quota
- Please be kind in your comments 🙂

---

## Documentation

- [YouTube Data API v3](https://developers.google.com/youtube/v3/docs)
