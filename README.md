# ✉️ AI Cover Letter Generator

Upload your resume, paste a job description, and get a professional cover letter tailored to the job. Built with **Streamlit** and **Google Gemini Flash**.

## Features

- Upload a resume as **PDF, DOCX, or TXT**
- Paste any job description
- Choose tone (Professional, Enthusiastic, Confident, Friendly, Formal) and length
- Optional company name, job title, your name, and extra instructions
- Edit the generated letter in the browser
- Download as **.txt** or **.docx**
- The prompt instructs the model to use only facts from your resume, so it should not invent experience. Always review the letter before sending.

## Project structure

```
.
├── app.py
├── requirements.txt
└── README.md
```

## Run locally

1. Install Python 3.9 or newer.
2. Create and activate a virtual environment (recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Get a free Gemini API key at https://aistudio.google.com/app/apikey

5. Provide the key in one of these ways:

   - Paste it into the app's sidebar (easiest), or
   - Set an environment variable:

     ```bash
     export GEMINI_API_KEY="your-key"      # Windows PowerShell: $env:GEMINI_API_KEY="your-key"
     ```

   - Or create `.streamlit/secrets.toml`:

     ```toml
     GEMINI_API_KEY = "your-key"
     ```

6. Start the app:

   ```bash
   streamlit run app.py
   ```

## Configuration

| Setting | Where | Purpose |
|---|---|---|
| `GEMINI_API_KEY` | Sidebar, Streamlit secret, or env var | Your Gemini API key |
| `GEMINI_MODEL` | Streamlit secret or env var (optional) | Override the default Flash model |

The app uses `gemini-3.5-flash` by default and automatically falls back to `gemini-2.5-flash` if the first model is unavailable. Google retires model names over time, so if you see a "model not found" error, set `GEMINI_MODEL` to a current Flash model name from https://ai.google.dev/gemini-api/docs/models.

## Deploy on Streamlit Community Cloud

1. Push this project to a public GitHub repository (`.streamlit/secrets.toml` must **not** be committed).
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, pick your repository and branch, and set the main file path to `app.py`.
4. Open **Advanced settings → Secrets** and add:

   ```toml
   GEMINI_API_KEY = "your-key"
   ```

5. Click **Deploy**.

> If you add your key as a secret, everyone who uses your public app spends your API quota. To avoid that, leave the secret out and let users paste their own key in the sidebar.

## Privacy

Resume text and the job description are sent to Google's Gemini API to generate the letter. The app itself does not save uploaded files.

## Troubleshooting

- **"Couldn't read enough text from the resume"**: the PDF is probably a scanned image. Use a text-based PDF or a DOCX.
- **"model not found"**: set `GEMINI_MODEL` to a current Flash model.
- **API key errors**: confirm the key is valid and the Gemini API is available in your region.

## License

MIT# AI-cover-letter
