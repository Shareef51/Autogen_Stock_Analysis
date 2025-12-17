# Autogen_Stock_Analysis with Multi-Agent

This repository contains the architecture and tool definitions for a multi-agent system designed for financial analysis. The system leverages specialized agents that utilize modular tools to fetch data, perform technical analysis, and generate investment recommendations. 

---

## System Architecture

The system is organized into two primary layers: the **Agent Layer** and the **Toolbox Layer**. 

### Agent Layer

**UserProxyAgent**: Acts as the orchestrator/supervisor, receiving input from the user and delivering the final recommendation. 

**Finance Reporting Analyst**: Initiates the process by running reports and fetching core insights. 

**Technical Analyst**: Focuses specifically on technical indicators to detect market trends and momentum. 

**Strategy Agent**: Synthesizes reports, technical insights, and risk data to provide final "Buy/Sell/Hold" recommendations. 

### Toolbox Layer (The "Hands" of the Agent)

Tools are callable Python functions or APIs that allow agents to interact with the real world or perform complex calculations that an LLM cannot do alone. 

---

## Tool Documentation

### 1. Finance Data Fetch (`finance_data_fetch`)

**Purpose**: Fetches basic financial and historical stock data. 

**Inputs**: Stock ticker, period (default: 1mo). 

**Key Metrics**: Company info (market cap, P/E ratio), historical closing prices. 

**Primary User**: Finance Reporting Analyst. 

### 2. Technical Analysis Tool (`technical_analysis_tool`)

**Purpose**: Performs technical indicator calculations. 

**Key Metrics**: SMA (20-day), EMA (20-day), RSI (14-day), and last close price. 

**Primary User**: Technical Analyst. 

### 3. Risk Assessment Tool (`risk_assessment_tool`)

**Purpose**: Analyzes the stock’s risk profile. 


**Key Metrics**: Beta, Market Cap, Dividend Yield, and Volatility. 

**Output**: Risk Rating (High/Moderate/Low). 

**Primary User**: Strategy Agent. 

### 4. Strategy Signal Tool (`strategy_signal_tool`)


**Purpose**: Supports decision-making via momentum signals. 


**Key Metrics**: MACD, MACD Signal Line, RSI, and last close price. 


**Primary User**: Strategy Agent. 


---

## Design Principles

**Modularity & Accuracy**: By separating logic from execution, the system ensures reliable operations and minimizes hallucinations. 


**Reusability**: Tools are designed to be used across different agents and extended for complex workflows. 


**Error Handling**: All tools implement a graceful fallback mechanism, returning error messages in JSON format to ensure system stability. 
<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/126bbb6c-200e-486f-b124-614f5aa1deff" />



