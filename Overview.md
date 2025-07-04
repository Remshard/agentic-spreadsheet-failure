# Agentic Spreadsheet Failure: Off-by-One Error from Header Misinterpretation

← [Back to Summary](./README.md)

## Objective

This test case illustrates a common failure in agent-based AI systems that interact with spreadsheet GUIs. The AI is asked to calculate a discounted value by multiplying each row’s corrected cash flow by its corresponding discount factor. The expected output appears in a “Final Answer” column.

## Prompt to the Agent

> “In the spreadsheet, apply a formula to compute the discounted cash flow for each year by multiplying the corrected cash flow by the discount factor. Enter the result in the 'Final answer' column.”

## Expected Behavior

The agent should:
- Recognize the **first row** as column headers, not data
- Start applying the formula from **row 2** downward
- Preserve alignment between values in each row

The correct formula in cell `E2` should be:

=D2*C2

Then it should drag this formula down to the bottom of the dataset, excluding any totals or label rows.

## Observed Behavior

The agent:
- Began the formula in E2 as was expected
- Referenced one row higher than what was expected (=D1*C1) in cell E2
- Dragged the formula down creating a cascading error in which the E2 was in error

### Screenshot of Incorrect Agent Output

![Formula Error](./error%201.png)

### Formula Breakdown Visualization

![Formula Breakdown](./error%202.png)
