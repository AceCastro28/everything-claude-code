# ⚡ Quick Setup - Replace Only the (?) Placeholders

## 🎯 Your Mission: Find and Replace 5 Placeholders

---

## File 1: `mcp-configs/mcp-servers-ready-to-use.json`

### 4 Required Replacements:

```json
✅ REPLACEMENT #1 - GitHub Token
"GITHUB_PERSONAL_ACCESS_TOKEN": "(?)",
                                  ↑↑↑
                    Replace with: ghp_YourActualTokenHere
                    Get from: https://github.com/settings/tokens

✅ REPLACEMENT #2 - Firecrawl Key
"FIRECRAWL_API_KEY": "(?)",
                      ↑↑↑
        Replace with: fc_YourActualKeyHere
        Get from: https://firecrawl.dev

✅ REPLACEMENT #3 - Supabase Project ID
"--project-ref=(?)"
               ↑↑↑
Replace with: --project-ref=abcdefghijklmnop
Get from: https://supabase.com/dashboard → Settings → General

✅ REPLACEMENT #4 - Filesystem Path
"args": ["-y", "@modelcontextprotocol/server-filesystem", "(?)"],
                                                           ↑↑↑
                                    Replace with: /Users/yourname/projects
                                    (or C:\\Users\\yourname\\projects on Windows)
```

---

## File 2: `hooks/hooks-ready-to-use.json`

### 1 Optional Replacement:

```json
✅ REPLACEMENT #5 - Editor Command (OPTIONAL)
(?)\necho '[Hook] Press Enter to continue...'
↑↑↑
Replace with: code . (for VS Code)
          or: zed . (for Zed)
          or: cursor . (for Cursor)
          or: DELETE THIS LINE entirely (to skip opening editor)
```

---

## 📋 Checklist

Copy this and mark as you go:

```
[ ] 1. Replace (?) with GitHub token
[ ] 2. Replace (?) with Firecrawl key (or delete this MCP server)
[ ] 3. Replace (?) with Supabase project ID (or delete this MCP server)
[ ] 4. Replace (?) with your projects directory path
[ ] 5. Replace or delete (?) in git push hook
[ ] 6. Copy mcpServers object to ~/.claude/settings.json
[ ] 7. Copy hooks object to ~/.claude/settings.json
[ ] 8. Save ~/.claude/settings.json
[ ] 9. Restart Claude Code
[ ] 10. Test: Ask Claude "Can you check my GitHub repos?"
```

---

## 🚀 3-Minute Setup (Seriously!)

### Step 1: Get Your Credentials (2 minutes)

Open these in browser tabs:
1. GitHub Token: https://github.com/settings/tokens
2. Firecrawl Key: https://firecrawl.dev (if you use it)
3. Supabase Dashboard: https://supabase.com/dashboard (if you use it)

### Step 2: Find & Replace (30 seconds)

Use your editor's Find & Replace:
- Find: `(?)`
- Replace with your actual values (one at a time)

### Step 3: Copy to Settings (30 seconds)

```bash
# Open your Claude settings
code ~/.claude/settings.json

# Or create it if it doesn't exist
echo '{}' > ~/.claude/settings.json
code ~/.claude/settings.json
```

Copy the `mcpServers` and `hooks` objects into the file.

### Step 4: Restart Claude Code

Done! 🎉

---

## 💡 Pro Tips

### Skip MCPs You Don't Need

Don't use Supabase? **Delete that entire block:**
```json
"supabase": {
  // DELETE THIS WHOLE OBJECT
},
```

Don't use Firecrawl? **Delete it:**
```json
"firecrawl": {
  // DELETE THIS WHOLE OBJECT
},
```

### Minimal Setup (Just GitHub + Essentials)

Keep only:
- ✅ `github` (requires token)
- ✅ `memory` (no config needed)
- ✅ `sequential-thinking` (no config needed)
- ✅ `filesystem` (requires path)

Delete everything else!

---

## 🔍 Exactly Where Are the (?) Placeholders?

### In `mcp-servers-ready-to-use.json`:

**Line ~6:** GitHub token
```json
"GITHUB_PERSONAL_ACCESS_TOKEN": "(?)",
```

**Line ~14:** Firecrawl key
```json
"FIRECRAWL_API_KEY": "(?)",
```

**Line ~21:** Supabase project ID
```json
"args": ["-y", "@supabase/mcp-server-supabase@latest", "--project-ref=(?)"],
```

**Line ~81:** Filesystem path
```json
"args": ["-y", "@modelcontextprotocol/server-filesystem", "(?)"],
```

### In `hooks-ready-to-use.json`:

**Line ~29:** Editor command (inside the git push hook)
```json
(?)
```

---

## 🎨 Example: Complete Setup

### Before (with placeholders):
```json
{
  "mcpServers": {
    "github": {
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "(?)"
      }
    },
    "filesystem": {
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "(?)"]
    }
  }
}
```

### After (with your info):
```json
{
  "mcpServers": {
    "github": {
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_abc123XYZ789def456"
      }
    },
    "filesystem": {
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/john/projects"]
    }
  }
}
```

---

## ⚠️ Common Mistakes

### ❌ Don't Leave the (?):
```json
"GITHUB_PERSONAL_ACCESS_TOKEN": "(?)",  // WRONG!
```

### ✅ Replace it completely:
```json
"GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_abc123",  // CORRECT!
```

### ❌ Don't forget quotes:
```json
"args": ["--project-ref=myproject"]  // Missing quotes on path
```

### ✅ Keep the quotes:
```json
"args": ["-y", "@supabase/mcp-server-supabase@latest", "--project-ref=myproject"]  // Correct!
```

### ❌ Don't escape Windows paths wrong:
```json
"args": ["-y", "@modelcontextprotocol/server-filesystem", "C:\Users\John"]  // WRONG!
```

### ✅ Use double backslashes OR forward slashes:
```json
"args": ["-y", "@modelcontextprotocol/server-filesystem", "C:\\Users\\John"]  // Correct!
// OR
"args": ["-y", "@modelcontextprotocol/server-filesystem", "C:/Users/John"]  // Also correct!
```

---

## 🆘 Still Confused?

### Just Search for `(?)`

In your editor:
1. Open `mcp-servers-ready-to-use.json`
2. Press `Cmd+F` (Mac) or `Ctrl+F` (Windows/Linux)
3. Search for: `(?)`
4. Replace each one as you find it

You'll find exactly 5 total:
- 4 in `mcp-servers-ready-to-use.json`
- 1 in `hooks-ready-to-use.json`

---

## 🎯 Final Destination

Your completed `~/.claude/settings.json` should look like:

```json
{
  "mcpServers": {
    // ... all your configured MCP servers
  },
  "hooks": {
    "PreToolUse": [
      // ... your hooks
    ],
    "PostToolUse": [
      // ... your hooks
    ],
    "Stop": [
      // ... your hooks
    ]
  }
}
```

**That's it! You're done! 🎉**

---

## 📞 Quick Links

- Full Guide: See `INSTALLATION-GUIDE.md`
- Security Info: See the security review report
- Original Repo: https://github.com/AffanMustafa/everything-claude-code

**Now go build something amazing with Claude Code! 🚀**
