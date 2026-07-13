# Learning Notes – Software

## Python

### Files and Paths
- `Path(__file__).parent` means the folder where the current Python file is located.
- This allows the program to load files like `personality.md`, `memory.json`, and `journal.md` from the same folder.

### JSON
- `memory.json` stores structured long-term memory.
- JSON is good for stable facts and small memory entries.
- A missing comma can break the file.

## Huggy AI

### Memory Layers
- `history` = short-term memory during the current run
- `memory.json` = stable long-term memory
- `journal.md` = emotional and project journal
- `conversations/` = full saved conversations

### Personality
- `personality.md` controls Huggy's response style.
- The real file stays private.
- A public example can be shared on GitHub.

## Git

### .gitignore
- prevents private files from being uploaded
- should ignore:
  - `personality.md`
  - `memory.json`
  - `journal.md`
  - `conversations/`
  - `.env`

## APIs

### OpenAI API
- the API key should be stored in an environment variable
- never write the key directly into the code
