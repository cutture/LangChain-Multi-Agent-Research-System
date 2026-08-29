# LangChain Multi-Agent Research System

A lightweight multi-agent research workflow built with LangChain, OpenAI models, Tavily search, and web scraping utilities. The project demonstrates how a research pipeline can move from web discovery to content extraction, structured report generation, and quality review using specialized agents.

## Overview

This system is designed to:

- Search the web for recent and relevant information
- Select promising source URLs
- Scrape and clean article content
- Draft a structured research report
- Critique the generated report for quality and weaknesses

It is a practical example of using multiple LLM-powered agents in a single research workflow, with a simple Streamlit front-end for interaction.

## Features

- Multi-agent research architecture
- Search and extraction using Tavily + scraping libraries
- Structured report generation with LangChain prompt chains
- Built-in critic/reviewer step for evaluation
- Streamlit UI for easy experimentation
- Environment-based configuration for API keys

## Architecture

The project follows a simple pipeline:

1. Search Agent
   - Uses Tavily to find relevant web results for a topic.
2. Reader Agent
   - Selects a strong URL and extracts readable article content.
3. Writer Chain
   - Combines findings into a detailed, structured research report.
4. Critic Chain
   - Reviews the report and returns a scored assessment with strengths and areas to improve.

High-level flow:

```text
User Query
   ↓
Search Agent ──> Web search results
   ↓
Reader Agent ──> Scraped article content
   ↓
Writer Chain ──> Research report
   ↓
Critic Chain ──> Feedback and score
```

## Technologies Used

- Python 3.11+
- LangChain and LangChain Core
- LangChain OpenAI integration
- OpenAI GPT models
- Tavily Search API
- Streamlit for the user interface
- BeautifulSoup for HTML parsing
- Readability + Trafilatura for article extraction
- python-dotenv for environment management
- Requests for HTTP fetches

## Project Structure

```text
.
├── app.py                     # Streamlit app UI
├── main.py                    # Example pipeline entry point
├── requirements.txt           # Python dependencies
├── README.md                  # Documentation
├── src/
│   ├── agents/
│   │   └── agents.py          # Agent and chain definitions
│   ├── pipelines/
│   │   └── pipeline.py        # End-to-end research workflow
│   ├── tools/
│   │   └── tools.py           # Search and scraping tools
│   └── __init__.py
└── lcma/                      # Local virtual environment
```

## Prerequisites

Before running the project, make sure you have:

- Python 3.11 or newer
- An OpenAI API key
- A Tavily API key
- Internet access for research and scraping

## Installation

1. Clone the repository

```bash
git clone https://github.com/cutture/LangChain-Multi-Agent-Research-System.git
cd LangChain-Multi-Agent-Research-System
```

2. Create and activate a virtual environment

```bash
python -m venv .venv

# Windows
.venv\Scripts\activate

# macOS/Linux
source .venv/bin/activate
```

3. Install dependencies

```bash
pip install -r requirements.txt
```

4. Configure environment variables

Create a `.env` file in the project root with:

```env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

You can also set additional model configuration if needed.

## Usage

### Run the research pipeline

```bash
python main.py
```

This executes the default research topic defined in `main.py`.

### Launch the Streamlit app

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal in your browser.

## Example Workflow

The default example searches for:

> The impact of AI on the job market in 2026

The workflow will:

- search for relevant sources,
- scrape the most promising source,
- generate a report,
- provide feedback on the quality of the report.

## Notes

- This project is intended as a research and demonstration system rather than a production-grade autonomous crawler.
- Web scraping can be affected by website restrictions, rate limiting, and anti-bot protections.
- API usage will incur OpenAI and Tavily charges depending on your usage.

## Contributing

Contributions are welcome. If you would like to improve this project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request with a clear description

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgements

- LangChain
- OpenAI
- Tavily
- Streamlit
- The broader open-source AI and web research ecosystem
