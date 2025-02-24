
# Ice Breaker App

## Overview

"The Glacier App" is a conversational helper tool that allows users to generate personalized conversation starters, summaries, and interesting facts about a person based on publicly available data from LinkedIn and Twitter. It leverages AI-based natural language processing with `LangChain` and APIs to gather data and present it in a user-friendly and engaging format.

This app can be particularly useful for networking professionals, recruiters, or anyone looking to make impactful initial impressions while engaging with someone new.

---

## Features

- **Smart Data Aggregation**: Scrapes relevant information from LinkedIn and Twitter using intelligent agents.
- **AI-Powered Insights**: Generates an appealing summary of the person, unique facts, conversation starters, and topics of interest using AI.
- **User-Friendly Web Interface**: A simple, responsive front-end interface to enter names and view results quickly.
- **Dynamic Spinner**: Loading spinner to enhance the user experience while processing requests.
- **Profile Picture Integration**: Automatically fetches and displays the LinkedIn profile picture, if available.

---

## How It Works

1. **Input**: Enter the name of the person whose insights you want to generate on the form.
2. **Data Fetching**:
   - Fetch LinkedIn and Twitter profile details using `SerpAPIWrapper` and connected APIs.
   - Scrape key information such as work history, tweets, topics of interest, and profile images.
3. **AI-Powered Processing**: Use the power of the `LangChain` library to:
   - Analyze the fetched data.
   - Generate conversational icebreakers and facts.
4. **Output**: View a summary, facts, ice-breakers, and suggested topics of interest alongside the profile image, all displayed clearly in the web interface.

---

## Setup & Installation

### Prerequisites
- Python 3.13.2 or higher
- `pip` for dependency management
- API keys for:
  - LinkedIn scraping
  - Twitter API
  - SerpAPI for Google Custom Search

### Installation

1. Clone the repository:
```shell script
git clone <repo_url>
   cd ice-breaker
```

2. Install dependencies:
```shell script
pipenv install
   pipenv shell
```

3. Set up your `.env` file with the required API keys:
```shell script
SCRAPIN_API_KEY=<Your_LinkedIn_API_Key>
   OPENAI_API_KEY=<Your_OpenAI_API_Key>
   SCRAPIN_API_KEY=<Your_Scripin_API_Key>
   TAVILY_API_KEY=<Your_Tavily_API_Key>
   LANGSMITH_API_KEY=<Your_Langsmith_API_Key>
```

4. Run the Flask application:
```shell script
python app.py
```

5. Open your browser and navigate to:
```
http://127.0.0.1:5000/
```

---

## Project Structure

- **app.py**: Main application file to run the Flask server and route API calls.
- **templates**:
  - `index.html`: The web interface used to input names and render the results.
- **static/css**:
  - `style.css`: Contains styles for the front-end interface.
- **third_parties**:
  - `linkedin.py` and `twitter.py` for data scraping from LinkedIn and Twitter respectively.
- **agents**: Lookup agents for fetching profile URLs based on name.
- **glacier.py**: Core business logic for creating conversational summaries and facts using `LangChain`.
- **output_parsers.py**: Defines output schemas for AI-generated data.
- **tools.py**: Custom SerpAPI wrapper for profile URL searches.

---

## API Usage

### `/process [POST]`
- **Description**: Processes the name submitted via the web form and returns the generated data.
- **Request**: `{ "name": "Harrison Chase" }`
- **Response**:
```json
{
    "summary": "Software Engineer focused on AI development.",
    "interests": ["Python", "Natural Language Processing"],
    "facts": ["Runs LangChain", "Has a passion for AI research"],
    "ice_breakers": ["What inspired your interest in AI?", "Do you teach others about LangChain?"],
    "picture_url": "https://linkedin.com/path/to/profile-pic.jpg"
  }
```

---

## Technologies Used

**Backend**:
- Python 3.13.2
- Flask
- LangChain (for AI task orchestration)
- Tweepy (Twitter scraping)

**Frontend**:
- HTML/CSS
- FontAwesome (icons)

**External APIs**:
- ScrapIn (for linkedin profile lookups)
- Tavily API for scraping accessible data.

