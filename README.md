# Non-Recursive-Predictive-Parsing

A Flask-based Python project that builds a non-recursive predictive parser for a given grammar, computes `FIRST` and `FOLLOW` sets, generates the parsing table, and checks whether an input string is accepted by the grammar.

## Features

- Computes `FIRST` and `FOLLOW` sets for each non-terminal.
- Builds the predictive parsing table from the grammar.
- Validates whether the grammar is suitable for top-down parsing.
- Checks an input string step by step using the generated table.
- Shows the intermediate results in a web UI.

## Project Structure

- `app.py` - Flask application and parser implementation.
- `stack.py` - Simple stack helper used by the parser.
- `templates/index.html` - Input form for grammar and string.
- `templates/parse.html` - Results page for sets, table, and parsing steps.
- `requirements.txt` - Python dependencies.

## Requirements

- Python 3.10+ recommended.
- Flask
- pandas

## How It Works

1. Enter the grammar as comma-separated productions.
2. Provide terminal symbols, non-terminal symbols, the start symbol, and the string to check.
3. The app parses the grammar into an internal CFG representation.
4. It computes `FIRST` sets, then `FOLLOW` sets.
5. It builds the parsing table.
6. It checks the input string using a predictive parsing stack and displays each step.

## Running Locally

From the project folder, create a virtual environment, install dependencies, and run the app:

```powershell
python -m venv venv
venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```

Open `http://127.0.0.1:5000/` in your browser.

## Sample Input

Use this grammar for a quick test:

```text
cfg: E -> T E' , E' -> + T E' | ε , T -> F T' , T' -> * F T' | ε , F -> ( E ) | id
terminals: +,*,(,),id,ε
non-terminals: E,E',T,T',F
start symbol: E
string: id,+,id,*,id
```

This sample should be accepted.

## Notes

- Productions should be left-factored and free of left recursion for predictive parsing.
- Grammar items are entered comma-separated in the current UI.
- The input string should also be comma-separated, for example `id,+,id`.

## Push To GitHub

After reviewing the changes, you can push with:

```powershell
git add README.md requirements.txt .gitignore
git commit -m "Add documentation and project setup"
git push origin main
```
