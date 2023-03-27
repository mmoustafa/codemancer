# codemancer: coding superpowers with GPT-4 in your command line 🧙‍♂️

`codemancer` is a command line tool that uses the OpenAI API to generate code based on a given prompt and input file. You can use it to change code in-place or create new files.

You can use it as a versatile and efficient AI-powered programming assistant that simplifies code generation, streamlines development tasks, and boosts productivity.

https://user-images.githubusercontent.com/1714782/227892213-8cfdcbdb-3dae-4043-b155-9164e1104bc1.mp4

<br />

## Installation

```bash
npm install -g codemancer
```

## Usage

To use codemancer, you need to set the `OPENAI_API_KEY` environment variable with [your OpenAI API key](https://platform.openai.com/account/api-keys).

```bash
export OPENAI_API_KEY=your_api_key_here
```

> ⚠️ `codemancer` works best using GPT-4, and will use it by default. If you do not have access and receive a 404, you can use the GPT-3.5 model instead via `-m "gpt-3.5-turbo"`, but code generations will be much less reliable.

<br />

### Reading and writing to the same file

Modify a file in-place based on a prompt, useful for iterating on functionality, addressing review comments, resolving conflicts, or refactoring.

```bash
codemancer -i input_file_path -p "break the /recipe/<id> route into /recipe/<id>/info and /recipe/<id>/image"
```

### Reading and writing to a different file

Useful for generating a new file with similar functionality, readmes, or interface definitions (e.g. rpc).

```bash
codemancer -i input_file_path -o output_file_path -p "extract inlined types into interfaces in a separate file"
```

### Writing from prompt to file

For generating blank slate code for new projects, one-offs, or scripts.

```bash
codemancer -o output_file_path -p "I need an AppleScript to wipe Safari history on restart"
```

### Simple prompting

Ask questions, get answers and suggestions.

```bash
codemancer -p "what's a bulletproof regex for validating emails"
```

### Customizing model and temperature

```bash
codemancer -i input_file_path -m gpt-3.5-turbo -t 0.5 -p "change all variable names to obscure animals"
```

## Limitations:

- If there are multiple code blocks returned in the completion, codemancer will present a confirmation message for each and write only the accepted one. If the verbosity argument is set to 0, it will auto-confirm and write the first code block it encounters to the output file.
- The file content + prompt are currently limited to 8K tokens for GPT-4. If your file is too large/dense and you exceed this limit you will get a 400 error.

<br />

## License

GPL License - This code was largely written by AI with some human guidance.

<br />

<br />

<a href="https://www.buymeacoffee.com/0xmmo" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>
