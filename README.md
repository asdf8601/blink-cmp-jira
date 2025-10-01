# blink-cmp-jira

A Neovim plugin that provides Jira ticket autocompletion for blink.cmp using jira-cli.

## Requirements

- Neovim 0.9+
- [blink.cmp](https://github.com/Saghen/blink.cmp)
- [jira-cli](https://github.com/ankitpokhrel/jira-cli)

## Installation

Install using your preferred package manager:

```lua
-- lazy.nvim
{
  'your-username/blink-cmp-jira',
  dependencies = {
    'Saghen/blink.cmp'
  }
}
```

## Setup

Add to your blink.cmp configuration:

```lua
require('blink.cmp').setup({
  sources = {
    default = { 'lsp', 'path', 'snippets', 'buffer', 'jira' },
    providers = {
      jira = {
        name = 'blink-cmp-jira',
        module = 'blink-jira'
      }
    }
  }
})
```

## Usage

Type `#` followed by your search term to trigger Jira ticket completion.

## Configuration

```lua
require('blink.cmp').setup({
  sources = {
    providers = {
      jira = {
        name = 'blink-cmp-jira',
        module = 'blink-jira',
        opts = {
          jira_project = 'PROJ',                    -- Filter by project key
          jira_status = {'In Progress', 'To Do'},   -- Filter by status (array)
          max_results = 50,                         -- Maximum tickets to fetch (default: 50)
          cache_duration = 300,                     -- Cache lifetime in seconds (default: 300)
          trigger_character = '#',                  -- Trigger character (default: '#')
          background_refresh = true,                -- Auto-refresh cache (default: true)
          cache_file = nil,                         -- Custom cache file path (default: stdpath("cache")/blink-jira-cache.json)
        }
      }
    }
  }
})
```

## Features

- Fast autocompletion with persistent disk caching
- Background cache refresh with automatic invalidation
- Configurable filters for project and status
- Rich completion items with status and assignee info
- Searchable by ticket key, title, and description
- Lazy-loaded documentation with markdown formatting
- Compatible with both new (vim.system) and legacy Neovim versions

## License

MIT