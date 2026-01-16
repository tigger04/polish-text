# polish-text

AI-powered text enhancement tool that improves clarity, professionalism, and impact of written content.

## Features

- Enhance text clarity and professionalism
- Preserve original meaning while improving language
- Support for multiple AI models (OpenAI, Claude, Ollama)
- Flexible input/output options
- Automatic context setting and summarization for lengthy messages

## Installation

### Standard Installation

```bash
# Clone the repository
git clone https://github.com/tigger04/polish-text.git
cd polish-text

# Test the installation
make test

# Install (auto-detects Homebrew prefix if available)
make install

# Or install to custom location
make install PREFIX=~/.local
```

### Development Installation

```bash
# Make executable
chmod +x polish-text

# Optional: Link to PATH
ln -s "$(pwd)/polish-text" /usr/local/bin/polish-text
```

## Configuration

The tool automatically detects available AI providers and uses the first available one. Configuration is loaded in this order:

1. **Environment variables** (highest priority)
2. **Config file**: `~/.config/polish-text/config`
3. **Built-in defaults**

### Quick Setup

```bash
# Create config directory
mkdir -p ~/.config/polish-text

# Copy example config
cp config.example ~/.config/polish-text/config

# Edit with your API keys
nano ~/.config/polish-text/config
```

### Configuration Options

```bash
# ~/.config/polish-text/config

# API Keys (set at least one)
export OPENAI_API_KEY="sk-..."
export CLAUDE_API_KEY="sk-ant-..."
# export OLLAMA_API_URL="http://localhost:11434"  # Optional: remote Ollama

# Default provider (optional - auto-detects if not set)
export DEFAULT_AI="openai"  # or "claude" or "ollama"

# Model configurations
openai_model="gpt-4o-mini"
claude_model="claude-3-5-sonnet-20241022"
ollama_model="mistral"

# Custom pre-prompt (optional)
# pre_prompt="Your custom text enhancement instructions..."
```

### Auto-Detection

- If only one API key is provided, that provider becomes the default
- If multiple keys are available, preference order: OpenAI → Claude → Ollama
- If no API keys but Ollama is running locally, uses Ollama

## Usage

```bash
# Polish text from a file
polish-text draft.txt

# Polish text from URL
polish-text https://example.com/draft

# Polish text from clipboard
polish-text --clipboard

# Use specific AI provider
polish-text draft.txt --claude
polish-text draft.txt --openai
polish-text draft.txt --ollama

# Output directly to clipboard for pasting
polish-text draft.txt --paste

# Show result as notification
polish-text draft.txt --notification
```

## Options

### AI Models
- `-l, --ollama[=model]`: Use Ollama API
- `-o, --openai[=model]`: Use OpenAI API
- `--claude`: Use Claude API
- `--preprompt=TEXT`: Custom prompt prefix

### Input
- `-c, --clipboard`: Read from clipboard
- `-s, --selection`: Read from selection (0.3s delay)

### Output
- `-n, --notification`: Show as system notification
- `-d, --dialog`: Show in dialog window
- `-t, --type`: Type out the result
- `-p, --paste`: Copy to clipboard

## What It Does

The tool:
- Sharpens language for clarity and impact
- Maintains respectful, professional tone
- Preserves key points and meaning
- Emphasizes important messages
- Adds context and summaries for lengthy content
- Never adds emojis

## License

MIT License - See LICENSE file for details