# Expert Solution Trace: The Log File Detective

## Solution Rationale
The problem requires efficient processing of a large log file to perform frequency analysis and filtering. The solution uses a pipeline of Unix commands, each performing a single, well-defined operation, which is both efficient and clear for verification.

## Step-by-Step Command Chain & Explanation

```bash
# 1. Extract the archive without verbose output
tar -xzf server_logs.tar.gz

# 2. Navigate into the logs directory
cd logs

# 3. Core Solution Pipeline
grep -o '\[[A-Z_]*\]' app.log |      # Extract just the error types in brackets
sort |                               # Sort error types to prepare for counting
uniq -c |                            # Count occurrences of each unique type
sort -nr |                           # Sort counts numerically, highest first
head -n 1 |                          # Take the top result (most frequent error)
awk '{print $2}' > top_error.tmp     # Save the error type (without count) to a file

# 4. Read the saved error type and find the last 3 matches
TOP_ERROR=$(cat top_error.tmp | tr -d '[]') # Store error, removing brackets
grep "\[$TOP_ERROR\]" app.log |             # Find all lines with this error
tail -n 3                                   # Output the last 3 occurrences
