# CLI Challenge: The Log File Detective

## Objective
Your task is to find the most frequent error type in a server log file and extract the last 3 occurrences of that error, along with their timestamps.

## Scenario
You are given a compressed archive (`server_logs.tar.gz`). Inside, there is a directory `logs/` containing a file `app.log`. The log file lines follow this format:
`[YYYY-MM-DD HH:MM:SS] [ERROR_TYPE] - Message text here...`

## Specific Tasks
1.  Extract the archive.
2.  Identify which `[ERROR_TYPE]` appears the most number of times in `app.log`.
3.  Output only the last 3 log lines (full lines) that contain this most frequent error type.
4.  The final output should be just those three lines, nothing else.

## Constraints
- You must complete this using a sequence of command-line commands (Bash, Zsh, etc.).
- Do not use graphical tools or text editors in a non-CLI mode.
- Assume the file is large (1GB+), so your solution should be efficient.

## Success Criteria
A solution is correct if it:
- Correctly identifies the most frequent error type.
- Outputs exactly the last three occurrences of that error.
- Uses a chain of standard CLI tools (e.g., `tar`, `grep`, `awk`, `sort`, `uniq`, `tail`).
