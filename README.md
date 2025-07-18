# Simple Commit Webhook Notifier

This automatically sends commit details to your webhook whenever you push changes to the repository.

## Setup

✅ **Already configured!** The webhook URL is set to:
`https://webhook.site/bebd9100-18be-4178-a303-46e2d059f43a`

No setup needed - just commit and it will automatically send data to your webhook.

## What it sends

When you commit, it automatically posts this JSON to your webhook:

```json
{
  "commit_sha": "abc123def456",
  "commit_message": "Updated subscriber action",
  "author": "Your Name",
  "author_email": "your@email.com",
  "repository": "username/MailerLite-Ruchi",
  "branch": "main",
  "timestamp": "2023-12-07T10:30:00Z",
  "modified_files": [
    "Actions/Addnewsinglesubscribertospecifiedgroup/config.json"
  ],
  "added_files": [],
  "removed_files": [],
  "commit_url": "https://github.com/username/repo/commit/abc123def456"
}
```

## How to receive the webhook

Your webhook endpoint should accept POST requests with JSON data. Example:

```javascript
// Express.js example
app.post("/webhook", (req, res) => {
  const commitData = req.body;
  console.log("New commit:", commitData.commit_message);
  console.log("Modified files:", commitData.modified_files);

  // Process the commit data here
  // Extract action IDs, call CompanyHub API, etc.

  res.status(200).send("OK");
});
```

That's it! Now every commit automatically notifies your webhook with all the details.
