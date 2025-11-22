# GenBI

An AI-powered data analysis tool built with FastAPI and LangChain. Upload any dataset (CSV, Excel, JSON) and ask questions in plain English. GenBI classifies your query and responds with interactive charts, tables, or text answers.

## How It Works

1. Upload a dataset through the API
2. Ask a question like "show me a bar chart of sales by region" or "what is the average revenue?"
3. GenBI classifies the query (plot, table, or text answer) and returns the result
4. Visualizations are generated with Plotly, tables with Pandas, and answers with GPT-4o

## Tech Stack

- **FastAPI** for the backend API
- **LangChain + OpenAI GPT-4o** for query classification and response generation
- **Plotly** for interactive visualizations
- **Pandas** for data processing
- **Firebase** for authentication and session management
- **Vercel** for deployment

## Project Structure

```
GenBI/
├── main.py                   # FastAPI app with upload, query, and session endpoints
├── config.py                 # Environment config (API keys, model settings)
├── auth.py                   # Firebase token verification
├── file_processor.py         # CSV/Excel/JSON file loader
├── session_manager.py        # Firestore session storage
├── agents/
│   ├── classifier.py         # Classifies queries into plot/table/answer
│   ├── prompt_generator.py   # Generates data manipulation prompts
│   ├── visualization.py      # Creates Plotly charts from processed data
│   ├── table_generator.py    # Generates dataframes from queries
│   └── responce_generator.py # Text response generation with LangChain agent
├── utils/
│   ├── openai_helpers.py     # OpenAI API wrapper and key validation
│   └── data_processor.py     # DataFrame cleaning and manipulation
├── models/
│   └── token_models.py       # Pydantic models for Firebase tokens
├── api/
│   └── index.py              # Vercel serverless entry point
├── vercel.json               # Vercel deployment config
└── requirements.txt
```

## Setup

1. **Clone the repo**
   ```bash
   git clone https://github.com/harihkk/GenBI.git
   cd GenBI
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Create a `.env` file** in the project root with your keys
   ```
   OPENAI_API_KEY=your_openai_key
   FIREBASE_CREDENTIALS=your_firebase_credentials_json
   ```

4. **Run the server**
   ```bash
   uvicorn main:app --reload
   ```

## API Endpoints

- `GET /` Health check
- `POST /upload` Upload a dataset file (requires auth token)
- `POST /query` Ask a question about the uploaded data (requires auth token)
- `GET /session` Get session history for the authenticated user

## License

MIT
