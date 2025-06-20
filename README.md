# TDS Virtual Teaching Assistant

This project develops a Virtual Teaching Assistant API tailored for the Tools in Data Science (TDS) course at IIT Madras. The API intelligently responds to student queries by leveraging course materials and historical discussions from the Discourse forum, enabling quick, accurate, and automated support for learners.

## Features

- ✅ **FastAPI REST endpoint** at `/query/` accepting POST requests
- ✅ **JSON request/response format** with question and optional base64 image
- ✅ **Structured response** with answer and relevant links
- ✅ **Course content integration** with TDS-specific knowledge
- ✅ **Discourse post simulation** with realistic Q&A data

## Setup

1. Install dependencies:
```bash
pip install -r requirements.txt
```

2. Set up environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

3. Scrape Discours data and Course Content (optional):
```bash
python scrape_course.py
python scrape_disourse.py
```

4. Run the application:
```bash
uvicorn app:app --reload
```

## API Usage

### Endpoint
POST `/query/`

### Request Format
```json
{
  "question": "Your question here",
  "image": "base64_encoded_image_data_optional"
}
```

### Response Format
```json
{
  "answer": "Detailed answer to the question",
  "links": [
    {
      "url": "https://discourse.onlinedegree.iitm.ac.in/t/...",
      "text": "Relevant link description"
    }
  ]
}
```

### Example Usage
```bash
curl "https://your-app-url.com/api/" \
  -H "Content-Type: application/json" \
  -d '{"question": "Should I use gpt-4o-mini which AI proxy supports, or gpt3.5 turbo?"}'
```

## Project Structure

```
├── app.py                 # Main FastAPI application
├── scrape_course.py  # Discourse data scraper
├── scrape_discourse.py # Course Content scraper
├── knowledge_base.db # file containing all the scraped content
├── procfile # used for deploying in render
├── promptfoo.yaml # for testing the endpoint with various test cases
├── requirements.txt       # Python dependencies
├── LICENSE               # MIT License
└── README.md            # Project documentation
```

## Evaluation

To test the application with the provided evaluation:

1. Update `project-tds-virtual-ta-promptfoo.yaml` with your API URL
2. Run: `npx -y promptfoo eval --config project-tds-virtual-ta-promptfoo.yaml`

## License

MIT License - see LICENSE file for details.
