---
name: rodney
description: Browser automation via Rodney (Chrome DevTools Protocol). Use for navigating web pages, interacting with elements, taking screenshots, running assertions, and accessibility testing.
disable-model-invocation: true
allowed-tools: Bash(rodney:*)
---

# Browser Automation with Rodney

Rodney drives a persistent headless Chrome instance via the Chrome DevTools Protocol.
Each CLI invocation connects to the same running browser session.

## Quick Start

```bash
rodney start                          # Launch headless Chrome
rodney open http://localhost:4000     # Navigate to page
rodney ax-tree --depth 3             # Inspect page structure
rodney click "button"                # Click element
rodney screenshot /tmp/page.png      # Take screenshot
rodney stop                          # Shut down Chrome
```

## Session Lifecycle

```bash
rodney start                   # Launch Chrome (headless)
rodney start --show            # Launch with visible window
rodney start --local           # Directory-scoped session (./.rodney/)
rodney start --insecure        # Accept self-signed certs
rodney status                  # Show browser status
rodney stop                    # Shut down Chrome
```

Sessions persist across CLI invocations. Use `--local` for project-scoped sessions.

## Navigation

```bash
rodney open <url>              # Navigate to URL
rodney back                    # Go back
rodney forward                 # Go forward
rodney reload                  # Reload (--hard to bypass cache)
rodney clear-cache             # Clear browser cache
```

## Page Info

```bash
rodney url                     # Current URL
rodney title                   # Page title
rodney text "<selector>"       # Element text content
rodney html [selector]         # Page or element HTML
rodney attr "<selector>" <name>  # Attribute value
rodney pdf [file]              # Export page as PDF
```

## Interaction

```bash
rodney click "<selector>"      # Click element
rodney input "<selector>" "text"  # Type into input
rodney clear "<selector>"      # Clear input field
rodney file "<selector>" <path>   # Upload file to file input
rodney select "<selector>" <val>  # Select dropdown option
rodney submit "<selector>"     # Submit form
rodney hover "<selector>"      # Hover over element
rodney focus "<selector>"      # Focus element
```

## Waiting

```bash
rodney wait "<selector>"       # Wait for element to appear
rodney waitload                # Wait for page load
rodney waitstable              # Wait for DOM to stabilize
rodney waitidle                # Wait for network idle
rodney sleep <seconds>         # Sleep N seconds
```

## Screenshots

```bash
rodney screenshot [file.png]           # Page screenshot
rodney screenshot -w 1280 -h 720 f.png  # Custom viewport size
rodney screenshot-el "<selector>" f.png  # Element screenshot
```

## Assertions & Checks

Exit codes: 0 = pass, 1 = fail, 2 = error.

```bash
rodney exists "<selector>"     # Element exists in DOM?
rodney visible "<selector>"    # Element is visible?
rodney count "<selector>"      # Count matching elements
rodney assert '<js-expr>'      # Truthy check
rodney assert '<js-expr>' '<expected>'  # Equality check
rodney assert '<js-expr>' -m "message"  # Custom failure message
```

## JavaScript

```bash
rodney js 'document.title'                          # Evaluate expression
rodney js '[1,2,3].map(x => x*2)'                   # Returns JSON
rodney js 'document.querySelectorAll("li").length'   # Count elements
```

## Accessibility Tree

```bash
rodney ax-tree                        # Full accessibility tree
rodney ax-tree --depth 3              # Limit depth
rodney ax-tree --json                 # JSON output
rodney ax-find --role button          # Find by role
rodney ax-find --name "Submit"        # Find by accessible name
rodney ax-find --role link --name "Home"  # Combine filters
rodney ax-node "<selector>"           # Inspect element a11y info
```

## Tabs

```bash
rodney pages                   # List all tabs
rodney newpage [url]           # Open new tab
rodney page <index>            # Switch to tab
rodney closepage [index]       # Close tab
```

## Environment

- `ROD_CHROME_BIN` - Path to Chrome/Chromium binary (auto-detected if not set)
- `RODNEY_HOME` - Override data directory (default: ~/.rodney)

## Common Patterns

### Verify page content
```bash
rodney open http://localhost:4000
rodney waitload
rodney assert 'document.querySelector("h1").textContent.includes("Kaizen")'
rodney screenshot /tmp/homepage.png
```

### Check for JavaScript errors
```bash
# Use JS to check for errors (no built-in errors command)
rodney js 'window.__rodney_errors ? window.__rodney_errors.length : 0'
```
