# Manufacturing Operations Copilot Agent — Deployment Guide

## Package Contents

```
appPackage/
├── manifest.json              # Teams app manifest (devPreview schema)
├── declarativeAgent.json      # Agent definition with 7 conversation starters
├── color.png                  # 192×192 app icon
├── outline.png                # 32×32 outline icon
└── instructions/
    └── system-prompt.md       # Full system prompt with all 7 capabilities
```

## The 7 Manufacturing-Ops Features

| Skill | Manufacturing Use Case |
|-------|----------------------|
| `/status-report` | Daily production review, plant leadership report, shift summary |
| `/capacity-plan` | Capacity constraints, line/load analysis, labor/machine bottleneck review |
| `/process-doc` | SOPs, standard work, work instructions, escalation paths |
| `/runbook` | Shift handoff runbook, line-down response, quality hold process |
| `/change-request` | Engineering change, tooling change, process change, line changeover approval |
| `/risk-assessment` | Safety, quality, supplier, production, and delivery risk triage |
| `/compliance-tracking` | OSHA, ISO 9001, IATF 16949, FDA, GMP, customer audit prep |

## Deployment Steps

### 1. Generate a unique App ID
Replace `{{APP_ID}}` in `manifest.json` with a new GUID.  
PowerShell: `[guid]::NewGuid().ToString()`

### 2. Update SharePoint URL (optional)
In `declarativeAgent.json`, update the `items_by_url` URL to point to your actual SharePoint site containing manufacturing documents.

### 3. Upload to M365 Admin Center
1. Go to **Microsoft 365 Admin Center** → **Settings** → **Integrated apps**
2. Click **Upload custom apps**
3. Upload `ManufacturingOpsAgent.zip`
4. Assign to target users/groups

### 4. Test in M365 Copilot
1. Open M365 Copilot (copilot.microsoft.com or Teams)
2. Click the agent picker → select **Manufacturing Ops**
3. Use any of the 7 conversation starters to test

## Customization

- **System prompt**: Edit `instructions/system-prompt.md` to add plant-specific terminology, KPIs, or standards
- **SharePoint grounding**: Add your manufacturing document library URLs in `declarativeAgent.json` capabilities
- **Conversation starters**: Modify the starter prompts in `declarativeAgent.json` to match your plant's workflows
- **After edits**: Re-zip the `appPackage/` folder contents and re-upload
