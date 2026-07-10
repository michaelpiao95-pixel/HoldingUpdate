# Setup: Automated Earnings Memos via GitHub Actions

This makes the earnings memo agent run itself — no laptop, no manual
re-running. GitHub's servers check your holdings on a schedule and commit
new memos to the repo whenever a company reports.

## 1. Create a repo
- github.com -> New repository -> e.g. `portfolio-earnings-memos`
- Private is fine (recommended, since this is personal holdings data).

## 2. Add the files
Put these at the **root** of the repo:
- `holdings.csv`
- `EARNINGS_MEMO_AGENT.md`
- `.github/workflows/earnings-memo-agent.yml` (note the exact path —
  GitHub only picks up workflows inside `.github/workflows/`)

Easiest way: on github.com, use "Add file -> Upload files" and drag all
three in (recreate the `.github/workflows/` folder structure when you
upload the yml, or use `git` locally:
```
git clone https://github.com/<you>/portfolio-earnings-memos.git
cd portfolio-earnings-memos
mkdir -p .github/workflows
# copy the three files in, then:
git add .
git commit -m "Initial setup"
git push
```

## 3. Add your API key as a secret
- Get an API key from console.anthropic.com (Settings -> API Keys) if you
  don't have one. This is a separate thing from your claude.ai login —
  it's pay-as-you-go and is what lets the automation run without you.
- In the repo: Settings -> Secrets and variables -> Actions -> New
  repository secret
- Name: `ANTHROPIC_API_KEY`
- Value: paste your key

## 3b. Add email notification secrets
This uses Gmail SMTP to send you an email whenever a new memo gets
written (silent when nothing new happened, so no daily noise).

- **Turn on 2-Step Verification** on the Gmail account you want to send
  from, if it isn't already (Google Account -> Security).
- **Create an App Password**: myaccount.google.com/apppasswords -> name
  it something like "earnings-memo-bot" -> copy the 16-character password
  it generates. (This is a Gmail-generated password just for this
  automation — not your real Gmail password, and you can revoke it
  anytime without affecting your login.)
- In the repo, add three secrets (Settings -> Secrets and variables ->
  Actions -> New repository secret):
  - `GMAIL_USERNAME` — the full Gmail address you're sending from
  - `GMAIL_APP_PASSWORD` — the 16-character app password
  - `NOTIFY_EMAIL` — the address you want notified (can be the same
    Gmail address, or a different inbox entirely)

## 4. Install the Claude GitHub App (one-time, lets the action run)
- Locally, run `claude` then type `/install-github-app` and follow the
  prompts, OR
- Just go to github.com/apps/claude and install it on this repo directly.

## 5. Test it
- Go to the repo's "Actions" tab -> "Earnings Memo Agent" -> "Run workflow"
  (this is the manual trigger, works anytime, doesn't wait for the
  schedule)
- Watch it run. First run will be slow (39 companies, building the IR URL
  cache) — expect it to take a while and use a decent chunk of API credits
  once. After that, each run is fast and cheap since it skips anything
  without new earnings.
- Check the `memos/` folder for output once it finishes, and check your
  inbox (including spam, for the first email) for the notification.

## After that
It just runs — twice a day on weekdays, forever, checking all 39 holdings
and only doing real work when one of them actually reports. New memos show
up as commits in the repo. You can watch progress anytime under the
Actions tab, or check your email if you have GitHub notifications on for
failed workflow runs.

## Cost note
- GitHub Actions minutes: free tier easily covers this (a few minutes per
  run, twice a day).
- Anthropic API usage: billed per token via your API key. Cost scales with
  how many companies have new earnings that run — most runs will process
  0-2 companies, occasional "earnings season" runs will process more.
  Worth checking usage at console.anthropic.com periodically, especially
  after the first full run.
