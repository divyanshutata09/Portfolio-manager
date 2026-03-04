# Portfolio-manager
Investment Goal Parser & Strategy Builder
​This module serves as the entry point for a financial planning pipeline. It bridges the gap between unstructured natural language and quantitative financial modeling.
Overview
​The module performs two primary functions:
​Natural Language Understanding (NLU): Uses the llama-3.3-70b model to extract financial parameters (amount, risk, horizon, geography) from user input.
​Execution Planning: Generates a step-by-step roadmap for the downstream portfolio optimization engine (Modern Portfolio Theory/Markowitz model).
parse_investment_goal
​This function acts as a "Structured Parser." It enforces a strict JSON schema on the LLM output to ensure the data is safe for mathematical operations.
​Model: llama-3.3-70b-versatile
​Input: A string (e.g., "I want to invest 10 lakhs in low-risk Indian stocks for 5 years.")
​Output: A dictionary containing:
​investment_amount (float)
​currency (ISO code)
​risk_level (Sanitized: low, moderate, high)
​duration_years (float)
​geography (Sanitized: india, us, global)
​ build_execution_plan
​This function maps the structured goal to a computational workflow. It defines the "recipe" that the rest of the application follows, including:
​Data fetching via yfinance.
​Monte Carlo simulations (5,000 iterations).
​Markowitz Mean-Variance Optimization.
​Efficient Frontier visualization.
