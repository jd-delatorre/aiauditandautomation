# DigitalOcean Demo Setup Guide

Instructions for setting up an OpenClaw demo instance on DigitalOcean.

---

## Step 1: Create the Droplet

1. **Log into DigitalOcean** → [cloud.digitalocean.com](https://cloud.digitalocean.com)

2. **Create Droplet:**
   - **Region:** New York (NYC1 or NYC3) — lowest latency for NJ clients
   - **Image:** Ubuntu 24.04 LTS
   - **Size:** Basic → Regular → **$6/month** (1 GB RAM, 1 vCPU, 25 GB SSD)
     - This is plenty for demo/light production
   - **Authentication:** SSH key (recommended) or password
   - **Hostname:** `njaiautomation-demo` or similar

3. **Create** → Wait ~60 seconds for it to spin up

4. **Copy the IP address** once it's ready

---

## Step 2: SSH In & Initial Setup

```bash
# SSH into your new droplet
ssh root@YOUR_DROPLET_IP

# Update packages
apt update && apt upgrade -y

# Install Node.js 22+ (via NodeSource)
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt install -y nodejs

# Verify
node -v   # Should show v22.x.x
npm -v
```

---

## Step 3: Create a Non-Root User (Best Practice)

```bash
# Create user
adduser clawdbot
usermod -aG sudo clawdbot

# Switch to that user
su - clawdbot
```

---

## Step 4: Install OpenClaw

```bash
# Install globally
npm install -g clawdbot@latest

# Verify it's installed
clawdbot --version
```

---

## Step 5: Run the Onboarding Wizard

```bash
clawdbot onboard --install-daemon
```

The wizard will walk you through:

1. **Local vs Remote gateway** → Choose **Local** (it's running on this VPS)

2. **Auth/Model provider:**
   - **Claude (Anthropic)** — Recommended. You'll need an API key from [console.anthropic.com](https://console.anthropic.com)
   - Or OpenAI if you prefer

3. **Channels to connect:**
   - **Telegram** — Easiest for demo (just need a bot token from @BotFather)
   - **WhatsApp** — QR code login (good for showing clients)
   - **Slack/Discord** — If relevant to your demos

4. **Install daemon** → Yes (runs as systemd service, starts on boot)

5. **Gateway token** → Let it generate one (save this!)

---

## Step 6: Connect Demo Channels

### Telegram (Easiest for Demo)
1. Message [@BotFather](https://t.me/botfather) on Telegram
2. `/newbot` → Give it a name like "NJ AI Demo"
3. Copy the bot token
4. Add it via: `clawdbot configure --section telegram`

### WhatsApp (Impressive for Clients)
```bash
clawdbot channels login
```
Scan the QR code with WhatsApp → Settings → Linked Devices

---

## Step 7: Verify It's Running

```bash
# Check status
clawdbot status

# Health check
clawdbot health

# View logs
clawdbot gateway logs
```

---

## Step 8: Set Up Remote Access (Optional but Useful)

To access the Control UI from your laptop:

### Option A: SSH Tunnel (Quick)
```bash
# From your Mac, not the VPS
ssh -L 18789:localhost:18789 clawdbot@YOUR_DROPLET_IP
```
Then open `http://localhost:18789` in your browser.

### Option B: Tailscale (Better for Ongoing Use)
```bash
# On the VPS
curl -fsSL https://tailscale.com/install.sh | sh
tailscale up
```
Then access via Tailscale IP.

---

## Step 9: Create Demo Workspace

```bash
cd ~
mkdir -p clawd
cd clawd

# Create basic files
cat > SOUL.md << 'EOF'
# Demo AI Assistant

I'm a demo AI assistant for NJ AI Automation. I help businesses automate their workflows.

I'm helpful, professional, and demonstrate what's possible with AI automation.
EOF

cat > USER.md << 'EOF'
# Demo Mode

This is a demo instance. Be helpful and showcase capabilities.
EOF
```

---

## Monthly Costs Summary

| Item | Cost |
|------|------|
| DigitalOcean Droplet | $6/mo |
| Claude API (demo usage) | ~$5-20/mo |
| **Total** | **~$11-26/mo** |

---

## Quick Reference Commands

```bash
# Start/stop/restart gateway
clawdbot gateway start
clawdbot gateway stop
clawdbot gateway restart

# Check status
clawdbot status --all

# View config
clawdbot configure --show

# Add a channel
clawdbot configure --section telegram

# Approve pairing (when someone DMs the bot)
clawdbot pairing list telegram
clawdbot pairing approve telegram <code>
```

---

## Troubleshooting

### "clawdbot: command not found"
```bash
# Check npm global bin path
npm prefix -g

# Add to PATH if needed
export PATH="$(npm prefix -g)/bin:$PATH"
```

### Gateway won't start
```bash
# Check logs
journalctl -u clawdbot -n 50

# Or run manually to see errors
clawdbot gateway --verbose
```

### Can't connect channels
```bash
# Re-run channel setup
clawdbot configure --section <channel>

# Check channel status
clawdbot status --all
```

---

*Created: February 2026*
