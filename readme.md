# Intelligent Financial Advisory System

An AI-powered intelligent financial advisory platform that provides personalized investment guidance and real-time market analysis for Indian retail investors using advanced AI models (Groq) with integrated financial data tools.



## Overview

The Intelligent Financial Advisory System is a comprehensive solution that combines artificial intelligence with real-time financial data to deliver personalized investment advice. The system analyzes market conditions, company fundamentals, and investor profiles to provide actionable recommendations tailored to individual financial goals and risk preferences.

## Key Features

- **AI-Powered Analysis**: Leverages state-of-the-art language models (Groq LLaMA) for intelligent financial analysis
- **Real-Time Data Integration**: Fetches live stock prices, analyst recommendations, and company fundamentals via YFinance
- **Web Search Capabilities**: Uses DuckDuckGo for latest market news, quarterly results, and industry trends
- **Personalized Recommendations**: Considers investor profile (age, income, risk appetite) for tailored advice
- **Comprehensive Financial Analysis**: Provides detailed 8-section analysis covering financial health, business segments, trends, and investment outlook
- **Investment Planning**: Calculates optimal allocation using modern portfolio theory and diversification principles

## Technology Stack

- **Backend**: FastAPI (Python)
- **AI Framework**: Phi Framework
- **AI Models**: Groq LLaMA 3.1 (8B/70B variants)
- **Data Sources**: YFinance, DuckDuckGo Search
- **Frontend**: HTML, CSS, JavaScript
- **Environment**: Python 3.12+

## Installation & Setup

### Prerequisites

- Python 3.12 or higher
- pip package manager
- Web browser (Chrome, Firefox, Edge, etc.)

### Step 1: Install Dependencies

Clone or download the project, then install required packages:

```bash
pip install -r requirements.txt
```

### Step 2: Configure API Keys

Create a `.env` file in the project root directory:

```
GROQ_API_KEY=your_groq_api_key_here
```

**Getting Your Groq API Key:**
1. Visit [Groq Console](https://console.groq.com/)
2. Sign up for a free account
3. Navigate to API Keys section
4. Generate a new API key
5. Copy and paste it into your `.env` file

> **Note**: Groq offers free API access with generous rate limits, making it ideal for development and personal use.

### Step 3: Launch the Application

#### Option A: Using the Launcher Script (Recommended)

```bash
python app.py
```

This will automatically:
- Start the backend API server
- Open the frontend in your default browser

#### Option B: Manual Launch

**Start the Backend API:**

```bash
python backend_api.py
```

The API server will run on `http://localhost:8000`

**Open the Frontend:**

Navigate to the `frontend` directory and start a local server:

```bash
cd frontend
python -m http.server 8080
```

Then open your browser and visit: `http://localhost:8080`

## Usage Guide

### Basic Query

Ask any financial question in natural language:

```
What is the current price of Reliance stock?
```

### Personalized Investment Advice

Provide your investor profile for customized recommendations:

**Example Query:**
```
Should I invest in TCS?
```

**Profile Information:**
- Age: 30
- Monthly Salary: ₹300,000
- Risk Appetite: Moderate

The system will:
1. Analyze TCS fundamentals and market position
2. Consider your age, income, and risk tolerance
3. Calculate optimal allocation using financial planning frameworks
4. Provide specific SIP recommendations and portfolio allocation

### Advanced Analysis Request

Request comprehensive financial analysis:

```
Do a complete financial analysis of Reliance Industries
```

The system will provide an 8-section detailed analysis covering:
1. Financial Performance (Revenue, Profit, Cash Flow, Debt)
2. Business Segment Analysis
3. Industry Trends & Opportunities
4. Management & Strategy
5. Macroeconomic Factors
6. Future Outlook (3-5 years)
7. Investment Recommendation
8. Personalized Investment Plan (if profile provided)

## Configuration Options

### Changing the AI Model

Edit `financial_agent.py` to switch between different AI models:

**Current Configuration (Groq - Fast & Free):**
```python
model=Groq(id="llama-3.1-8b-instant")
```

**For More Powerful Analysis (Groq - Larger Model):**
```python
model=Groq(id="llama-3.1-70b-versatile")
```

**Using OpenAI (Requires OpenAI API Key):**
```python
from phi.model.openai import OpenAIChat
model=OpenAIChat(id="gpt-4")
```

Don't forget to add `OPENAI_API_KEY` to your `.env` file if using OpenAI.

### Agent Configuration

**With Tools (Default - Recommended):**
- Uses YFinanceTools for real-time stock data
- Uses DuckDuckGo for web search and market context
- Provides comprehensive analysis with live data

**Pure LLM Mode (No Tools):**
- Use `financial_advisor_pure` from `financial_agent.py`
- AI responses only, no real-time data fetching
- Useful for testing or when API limits are reached

## Project Structure

```
Intelligent-Financial-Advisory-System/
│
├── financial_agent.py      # Core AI agent with financial analysis logic
├── backend_api.py          # FastAPI backend server
├── app.py                  # Application launcher script
├── requirements.txt        # Python dependencies
├── .env                    # Environment variables (API keys)
│
├── frontend/
│   ├── index.html         # Main frontend interface
│   ├── script.js          # Frontend JavaScript logic
│   └── styles.css         # Frontend styling
│
└── README.md              # Project documentation
```

## Example Queries

Try these example questions to explore the system's capabilities:

**Stock Price Queries:**
- "What is the current price of TCS stock?"
- "Show me the stock price of HDFC Bank"
- "What's the current market price of Reliance?"

**Investment Advice:**
- "Should I invest in Reliance?"
- "I'm 30 years old, earn ₹3,00,000/month, have moderate risk. Should I invest in HDFC Bank?"
- "Is Wipro a good investment for a 25-year-old with high risk appetite?"

**Analyst Information:**
- "What are the analyst recommendations for TCS?"
- "Show me analyst ratings for Infosys"

**Comparative Analysis:**
- "Compare TCS and Infosys for investment"
- "Which is better: Reliance or TCS?"

**Comprehensive Analysis:**
- "Do a complete financial analysis of Reliance Industries"
- "Provide detailed analysis of TCS with investment recommendation"

## Financial Planning Framework

The system uses professional financial planning principles:

### Investment Capacity Calculation
- **Age 20-30**: 25-30% of monthly salary (longer investment horizon)
- **Age 31-50**: 20-25% of monthly salary (mid-career, family expenses)
- **Age 51+**: 15-20% of monthly salary (approaching retirement)

### Risk-Based Asset Allocation
- **Low Risk**: 70% Debt, 30% Equity
- **Moderate Risk**: 50% Debt, 50% Equity
- **High-Moderate Risk**: 30% Debt, 70% Equity
- **High Risk**: 10% Debt, 90% Equity

### Single Stock Allocation Limits
- **Low Risk**: Max 5-10% of equity portfolio
- **Moderate Risk**: Max 10-15% of equity portfolio
- **High-Moderate Risk**: Max 15-20% of equity portfolio
- **High Risk**: Max 20-25% of equity portfolio

## API Endpoints

The backend API provides the following endpoints:

- `POST /api/chat` - Send financial queries and receive AI-powered responses
  - Request body: `{"question": "your question", "age": 30, "salary": 300000, "risk": "Moderate"}`
  - Response: JSON with analysis and recommendations

## Troubleshooting

### Backend Not Starting
- Ensure port 8000 is not in use
- Check that all dependencies are installed: `pip install -r requirements.txt`
- Verify `.env` file exists with valid `GROQ_API_KEY`

### Frontend Not Loading
- Ensure backend is running on `http://localhost:8000`
- Check browser console for errors
- Verify `frontend/index.html` exists

### API Errors
- Verify your Groq API key is valid and active
- Check API rate limits on Groq Console
- Ensure internet connection for data fetching

### No Data Returned
- Check internet connection (required for YFinance and DuckDuckGo)
- Verify stock symbols are correct (use NSE format: `RELIANCE.NS`, `TCS.NS`)
- Some data may be unavailable during market hours

## Limitations & Disclaimers

- **Not Financial Advice**: This system provides informational analysis only. Always consult with certified financial advisors before making investment decisions.
- **Data Accuracy**: While the system uses real-time data sources, always verify critical information independently.
- **Market Volatility**: Stock prices and market conditions change rapidly. Analysis is based on data available at query time.
- **API Dependencies**: System requires active internet connection and valid API keys for full functionality.

## Future Enhancements

Potential improvements for future versions:
- Portfolio tracking and management
- Historical performance analysis
- Multi-stock portfolio optimization
- Risk assessment scoring
- Integration with trading platforms
- Mobile application
- Advanced charting and visualization

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

## License

This project is provided as-is for educational and personal use.

## Support

For issues, questions, or suggestions:
1. Check the troubleshooting section above
2. Review the code comments in `financial_agent.py`
3. Open an issue on the project repository

## Acknowledgments

- **Groq** for providing fast and free AI inference
- **YFinance** for real-time financial data
- **Phi Framework** for the agent infrastructure
- **FastAPI** for the robust backend framework

---

**Built with ❤️ for Indian Retail Investors**

*Empowering informed investment decisions through AI-powered financial intelligence*


