# TDS Virtual Teaching Assistant

This project develops a Virtual Teaching Assistant API tailored for the Tools in Data Science (TDS) course at IIT Madras. The API intelligently responds to student queries by leveraging course materials and historical discussions from the Discourse forum, enabling quick, accurate, and automated support for learners.

## Features

- ✅ **FastAPI REST endpoint** at `/api/` accepting POST requests
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

3. Scrape Discourse data (optional):
```bash
python scraper/scraper.py
```

4. Run the application:
```bash
python app.py
```

## API Usage

### Endpoint
POST `/api/`

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
├── scraper/
│   ├── scraper.py  # Discourse and Course Content data scraper
├── data/
│   ├── discourse_posts.json # Scraped Discourse data
│   └── course_content.json  # Course content data
├── models/
│   ├── request_models.py     # Pydantic request models
│   └── response_models.py    # Pydantic response models
├── services/
│   ├── question_processor.py # Question processing logic
│   └── answer_generator.py   # Answer generation service
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
