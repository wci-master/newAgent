
# newagent

## Overview

**newagent** is an AI-powered code review agent that leverages Google Gemini models and the Vercel AI SDK to provide automated, high-quality code reviews. It analyzes code changes in a given directory, reviews them file by file, and outputs actionable feedback based on best practices in software engineering.

## Features

- Automated code review using Google Gemini (Generative AI)
- File-by-file analysis of code changes (via Git)
- Customizable review focus areas (correctness, clarity, maintainability, etc.)
- Extensible tool system (add your own tools)
- Written in TypeScript, runs on Bun

## How It Works

1. The agent uses the [Vercel AI SDK](https://sdk.vercel.ai/docs) and [@ai-sdk/google](https://www.npmjs.com/package/@ai-sdk/google) to access Gemini models.
2. It loads a system prompt (see `prompt.ts`) that defines review style and focus.
3. It uses a custom tool (`getFileChangesInDirectoryTool`) to gather Git diffs for a target directory.
4. The agent streams review feedback to the console, file by file.

## Project Structure

- `index.ts` – Main entry point; runs the code review agent
- `tools.ts` – Tool definitions (e.g., for getting file changes)
- `prompt.ts` – System prompt for the AI reviewer
- `.env` – Environment variables (API keys)
- `package.json`/`bun.lock` – Dependencies
- `tsconfig.json` – TypeScript configuration

## Setup

1. **Install dependencies:**
	```bash
	bun install
	```

2. **Configure your API key:**
	- Create a `.env` file in the project root:
	  ```env
	  GOOGLE_GENERATIVE_AI_API_KEY=your-google-api-key-here
	  ```

3. **Run the agent:**
	```bash
	bun run index.ts
	```

## Usage

By default, the agent reviews code changes in the `../my-agent` directory. You can modify the prompt or tool input in `index.ts` to target a different directory or customize the review instructions.

## Customization

- **Change the review prompt:** Edit `prompt.ts` to adjust the review style, focus, or tone.
- **Add tools:** Extend `tools.ts` to add new capabilities (e.g., static analysis, test coverage checks).
- **Change the model:** Update the model in `index.ts` to use a different Gemini version or provider.

## Dependencies

- [Bun](https://bun.com) (runtime)
- [ai](https://www.npmjs.com/package/ai) (Vercel AI SDK)
- [@ai-sdk/google](https://www.npmjs.com/package/@ai-sdk/google)
- [simple-git](https://www.npmjs.com/package/simple-git)
- [zod](https://www.npmjs.com/package/zod)

## License

This project is licensed under the Apache-2.0 License.

---
Created with `bun init` and powered by Vercel AI SDK and Google Gemini.
