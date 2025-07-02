# agentic-spreadsheet-failure

## Overview
This test case explores a common failure mode in agent-based AI systems performing spreadsheet tasks. Specifically, it demonstrates how models frequently mistake the header (label) row for actual data, leading to off-by-one errors in formulas and incorrect outputs.

## Scenario
An AI agent is given a spreadsheet containing time-series financial data with labeled columns:
- Year
- Date
- Discount Factor
- Corrected Cash Flow
- Final Answer (Expected: Discounted Cash Flow)

The task is to compute the present value of each cash flow using the formula:

Final Answer = Corrected Cash Flow × Discount Factor

## Failure Mode
Instead of starting from row 2 (the first data row), the AI includes the header row (row 1) in the computation. This shifts all formula references upward by one, misaligning Discount Factors with incorrect Cash Flow entries. This leads to:
- Incorrect results
- Mismatched totals
- Logical inconsistencies

## Insight
This error stems from the AI’s failure to apply implicit human priors about layout semantics (e.g., headers vs data). It lacks the abstract contextual understanding needed to differentiate structural elements in GUI environments.

## Takeaway
While LLMs may succeed at formula generation or simple GUI simulation, they often lack the perceptual scaffolding required to navigate structured interfaces with the implicit logic humans rely on (e.g., "skip the label row"). This presents a critical bottleneck for agentic automation in spreadsheet-driven workflows.
