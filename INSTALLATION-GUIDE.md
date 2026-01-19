# 🚀 Installation Guide - Ready to Use Configurations

This guide will help you set up your Claude Code configurations with minimal effort. Just replace the `(?)` placeholders with your information!

## 📋 Quick Start Checklist

- [ ] Replace all `(?)` placeholders in `mcp-configs/mcp-servers-ready-to-use.json`
- [ ] Replace the `(?)` placeholder in `hooks/hooks-ready-to-use.json` (optional)
- [ ] Copy configurations to `~/.claude/settings.json`
- [ ] Restart Claude Code
- [ ] Test your configuration

---

## 🔧 Step 1: Configure MCP Servers

### File: `mcp-configs/mcp-servers-ready-to-use.json`

This file has **4 placeholders** marked with `(?)` that you need to replace:

### Required Replacements:

#### 1️⃣ GitHub Personal Access Token
**Find:** `"GITHUB_PERSONAL_ACCESS_TOKEN": "(?)",`

**Replace with:** Your GitHub token

**How to get it:**
1. Go to https://github.com/settings/tokens
2. Click "Generate new token (classic)"
3. Select scopes: `repo`, `read:org`, `read:user`
4. Copy the generated token
5. Replace `(?)` with your token

**Example:**
```json
"GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_abc123XYZ456def789"
```

---

#### 2️⃣ Firecrawl API Key
**Find:** `"FIRECRAWL_API_KEY": "(?)",`

**Replace with:** Your Firecrawl API key

**How to get it:**
1. Go to https://firecrawl.dev
2. Sign up for an account
3. Generate an API key from your dashboard
4. Replace `(?)` with your API key

**Example:**
```json
"FIRECRAWL_API_KEY": "fc_abc123XYZ456"
```

**Note:** If you don't use Firecrawl, you can delete this entire server block.

---

#### 3️⃣ Supabase Project Reference
**Find:** `"--project-ref=(?)"`

**Replace with:** Your Supabase project reference ID

**How to get it:**
1. Go to https://supabase.com/dashboard
2. Open your project
3. Go to Settings → General
4. Copy the "Reference ID"
5. Replace `(?)` with your reference ID

**Example:**
```json
"args": ["-y", "@supabase/mcp-server-supabase@latest", "--project-ref=abcdefghijklmnop"]
```

**Note:** If you don't use Supabase, you can delete this entire server block.

---

#### 4️⃣ Filesystem Path
**Find:** `"args": ["-y", "@modelcontextprotocol/server-filesystem", "(?)"],`

**Replace with:** Absolute path to your projects directory

**Examples:**
- **macOS/Linux:** `/Users/yourname/projects` or `/home/yourname/projects`
- **Windows:** `C:\\Users\\yourname\\projects`

**Example:**
```json
"args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/john/projects"]
```

---

### Servers That Don't Need Configuration:

These are **ready to use** without any changes:
- ✅ `memory` - Persistent memory across sessions
- ✅ `sequential-thinking` - Chain-of-thought reasoning
- ✅ `vercel` - Vercel deployments
- ✅ `railway` - Railway deployments
- ✅ `cloudflare-*` - Cloudflare services
- ✅ `clickhouse` - ClickHouse analytics
- ✅ `context7` - Live documentation
- ✅ `magic` - Magic UI components

**Tip:** Delete any servers you don't need to keep your context window clean!

---

## 🪝 Step 2: Configure Hooks (Optional)

### File: `hooks/hooks-ready-to-use.json`

This file has **only 1 placeholder** marked with `(?)`:

### Optional Replacement:

#### Editor for Git Push Review
**Find:** The `(?)` line in the git push hook

**Replace with:** Your preferred editor command (or delete this line)

**Options:**
```bash
zed .           # For Zed editor
code .          # For VS Code
cursor .        # For Cursor editor
vim .           # For Vim
nano .          # For Nano
```

**Example:**
```json
"command": "#!/bin/bash\n# Open editor for review before pushing\necho '[Hook] Review changes before push...' >&2\ncode .\necho '[Hook] Press Enter to continue with push or Ctrl+C to abort...' >&2\nread -r"
```

**OR simply delete the `(?)` line** if you don't want auto-opening an editor.

---

### Most Hooks Are Ready to Use!

The following hooks work without any changes:
- ✅ Block dev servers outside tmux
- ✅ Tmux reminder for long commands
- ✅ Block unnecessary .md file creation
- ✅ Auto-log PR creation
- ✅ Auto-format with Prettier
- ✅ TypeScript check after edits
- ✅ Warn about console.log statements
- ✅ Final console.log audit

---

## 📁 Step 3: Install to Claude Code

### Find Your Claude Settings File:

**macOS/Linux:**
```bash
~/.claude/settings.json
```

**Windows:**
```
C:\Users\YourName\.claude\settings.json
```

### Copy the Configurations:

1. Open `~/.claude/settings.json` in your editor
2. If it doesn't exist, create it with `{}`
3. Add the MCP servers:

```json
{
  "mcpServers": {
    // PASTE THE CONTENTS FROM mcp-servers-ready-to-use.json HERE
    // (everything inside the "mcpServers" object)
  }
}
```

4. Add the hooks (optional but recommended):

```json
{
  "mcpServers": {
    // ... your MCP servers
  },
  "hooks": {
    // PASTE THE CONTENTS FROM hooks-ready-to-use.json HERE
    // (everything inside the "hooks" object)
  }
}
```

### Example Final `settings.json`:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_YOUR_ACTUAL_TOKEN"
      }
    },
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
    // ... more servers
  },
  "hooks": {
    "PreToolUse": [
      // ... your hooks
    ],
    "PostToolUse": [
      // ... your hooks
    ]
  }
}
```

---

## 🔄 Step 4: Restart Claude Code

After saving your `settings.json`:

```bash
# Exit Claude Code completely and restart
# MCP servers will be loaded on startup
```

---

## ✅ Step 5: Test Your Configuration

### Test MCP Servers:

Ask Claude Code:
```
Can you check my GitHub repositories?
```

If GitHub MCP is working, Claude will be able to access your repos!

### Test Hooks:

Try editing a TypeScript file:
```
Edit any .ts file
```

You should see `[Hook]` messages about TypeScript checking and Prettier formatting.

---

## 📚 Using Your New Configuration

### Copy Other Files to Claude Config:

You can now copy any other files from this repo to your `~/.claude/` directory:

```bash
# Copy all agents
cp -r agents/ ~/.claude/

# Copy all skills
cp -r skills/ ~/.claude/

# Copy all commands
cp -r commands/ ~/.claude/

# Copy all rules
cp -r rules/ ~/.claude/

# Copy examples
cp -r examples/ ~/.claude/
```

---

## 🎯 What You Get:

### ✨ MCP Servers:
- 🔗 **GitHub** - Manage repos, PRs, issues
- 🔥 **Firecrawl** - Web scraping
- 🗄️ **Supabase** - Database operations
- 🧠 **Memory** - Persistent context
- 🤔 **Sequential Thinking** - Enhanced reasoning
- ☁️ **Cloud Services** - Vercel, Railway, Cloudflare
- 📂 **Filesystem** - Direct file access

### 🪝 Hooks:
- 🛡️ **Safety** - Prevent dev servers without tmux
- ✅ **Quality** - Auto-format and type check
- 🔍 **Audit** - Catch console.log before commit
- 📝 **Documentation** - Prevent random .md files
- 🚀 **Workflow** - Auto-log PR creation

### 🤖 Agents:
- 🔍 Code reviewer
- 🔒 Security scanner
- 📋 Implementation planner
- 🧪 TDD guide
- 📚 Documentation updater
- 🏗️ System architect
- 🔧 Build error resolver
- And more!

---

## 🆘 Troubleshooting

### MCP Server Not Working?

1. **Check your API key** - Make sure you replaced `(?)`
2. **Verify internet connection** - Some MCPs require network access
3. **Check Claude logs** - Look for error messages
4. **Restart Claude Code** - MCPs load on startup

### Hook Not Triggering?

1. **Check the matcher** - Ensure it matches your use case
2. **Verify bash syntax** - Test the command separately
3. **Check hook output** - Look for `[Hook]` messages in stderr
4. **Dependencies installed?** - Some hooks need Prettier, TypeScript, etc.

### Still Having Issues?

1. **Check Claude Code logs:** `~/.claude/logs/`
2. **Validate JSON syntax:** Use a JSON validator
3. **Test one at a time:** Enable MCPs/hooks individually
4. **Open an issue:** https://github.com/anthropics/claude-code/issues

---

## 🔐 Security Reminders

### ⚠️ NEVER commit your actual API keys to git!

**Bad:**
```json
{
  "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_abc123XYZ"  // DON'T COMMIT THIS!
}
```

**Good:**
```json
{
  "GITHUB_PERSONAL_ACCESS_TOKEN": "(?)"  // Safe to commit
}
```

### Keep your `~/.claude/settings.json` private!

Add to your global `.gitignore`:
```bash
echo "**/.claude/settings.json" >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

---

## 🎉 You're All Set!

You now have a fully configured Claude Code setup with:
- ✅ MCP servers for enhanced capabilities
- ✅ Hooks for workflow automation
- ✅ Agents for specialized tasks
- ✅ Skills for domain knowledge
- ✅ Commands for quick workflows
- ✅ Rules for consistent code

**Happy coding with Claude! 🚀**

---

## 📞 Need Help?

- **Documentation:** Read the guide at https://github.com/YOUR_REPO
- **Issues:** Open an issue on GitHub
- **Questions:** Check existing issues first

---

**Created with ❤️ for the Claude Code community**
