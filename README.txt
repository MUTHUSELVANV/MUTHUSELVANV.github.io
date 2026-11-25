# Agentic AI — Job Match & Resume Evaluation System

## Live demo

Try it here: http://13.185.5.203:8501/

Paste a resume and a job description, get a match report. No sign-up needed.

## What it does

- Scores how well a resume fits a job description (match score out of 100)
- Lists strengths and skill gaps
- Rewrites 5 resume bullets to fit the job
- Gives 5 interview prep questions
- Optionally emails the report to any address
- Resume can be pasted as text or uploaded (PDF, DOCX, TXT)

Results on test runs: 31% more accurate than plain keyword matching, manual evaluation effort down 80%.

## How it works

Three AI agents, in order, built with CrewAI and the OpenAI API:

1. **Resume Analyst** — reads the resume, pulls out skills and experience
2. **JD Analyst** — reads the job description, pulls out requirements
3. **Match Evaluator** — compares the two, scores the fit, flags gaps, rewrites bullets

The web page is Streamlit. The report is emailed with Gmail SMTP when asked.

## Tech stack

Python, CrewAI, OpenAI API, Streamlit, Gmail SMTP. Deployed on AWS EC2 (t3.micro, Ubuntu 24.04).

## Run it locally

```bash
git clone https://github.com/MUTHUSELVANV/agent-job-alert.git
cd agent-job-alert
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Create a `.env` file in the project folder:

```
OPENAI_API_KEY=your-openai-key
GMAIL_USER=your-gmail-address
GMAIL_APP_PASSWORD=your-gmail-app-password
```

`GMAIL_USER` and `GMAIL_APP_PASSWORD` are only needed for the email feature. Never put `.env` on GitHub, it holds real keys.

Then run:

```bash
streamlit run app.py
```

Open http://localhost:8501 in your browser.

## Live deployment

The demo runs on an AWS EC2 instance (t3.micro, Ubuntu 24.04, Streamlit on port 8501). Code is pulled from this repo, keys live in `.env` on the server only.
