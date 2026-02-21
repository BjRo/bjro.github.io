---
name: showboat
description: Create executable demo documents that capture verification steps, screenshots, and command outputs as persistent Markdown artifacts. Use for QA verification and demo generation.
disable-model-invocation: true
allowed-tools: Bash(showboat:*)
---

# Demo Documents with Showboat

Showboat builds Markdown documents that mix commentary, executable code blocks, and captured output.
These serve as both readable documentation and reproducible proof of work.

## Quick Start

```bash
showboat init demo.md "Feature Verification"    # Create document
showboat note demo.md "Testing the homepage"     # Add commentary
showboat exec demo.md bash "rodney title"        # Run command, capture output
showboat image demo.md screenshot.png            # Embed screenshot
showboat verify demo.md                          # Re-run and validate
```

## Commands

### init - Create a new demo document
```bash
showboat init <file> <title>
showboat init .demos/homepage.md "Homepage QA"
```

### note - Append commentary
```bash
showboat note <file> "Commentary text"
echo "Long text" | showboat note <file>     # From stdin
```

### exec - Run code and capture output
```bash
showboat exec <file> bash "echo hello"      # Run bash command
showboat exec <file> python "print('hi')"   # Run Python
cat script.sh | showboat exec <file> bash   # From stdin
```

Output is printed to stdout AND appended to the document. Exit code matches the executed command.

### image - Embed an image
```bash
showboat image <file> screenshot.png                    # Path only
showboat image <file> '![Description](screenshot.png)'  # With alt text
```

The image is copied into the document's directory with a generated filename.

### pop - Remove the most recent entry
```bash
showboat pop <file>   # Remove last note, exec, or image
```

Useful when a command produces an error that shouldn't remain in the document.

### verify - Re-run and validate
```bash
showboat verify <file>                    # Check all outputs match
showboat verify <file> --output new.md    # Write updated copy
```

Exit 0 if all outputs match, exit 1 if any changed.

### extract - Emit commands to recreate document
```bash
showboat extract <file>                           # Print CLI commands
showboat extract <file> --filename other.md       # Substitute filename
```

## Global Options

```bash
showboat --workdir <dir> exec ...    # Set working directory for execution
showboat --version                   # Print version
showboat --help                      # Show help
```

## QA Verification Pattern

```bash
# Initialize demo
showboat init .demos/homepage.md "Homepage QA Verification"

# Document what we're testing
showboat note .demos/homepage.md "## Check: Homepage renders correctly"

# Capture browser state
showboat exec .demos/homepage.md bash "rodney open http://localhost:4000"
showboat exec .demos/homepage.md bash "rodney title"

# Take and embed screenshot
rodney screenshot /tmp/qa-screenshot.png
showboat image .demos/homepage.md /tmp/qa-screenshot.png

# Run assertion
showboat exec .demos/homepage.md bash 'rodney assert "document.querySelector(\"h1\") !== null"'

# Verify the demo is reproducible
showboat verify .demos/homepage.md
```
