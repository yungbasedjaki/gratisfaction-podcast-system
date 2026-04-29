# 🚀 Push this repo to GitHub — 60 second checklist

Run these commands from a Git Bash window (or PowerShell with git installed) in this folder:
**`C:\Users\jakie\CoworkOps\Gratisfaction\repo\`**

---

## Step 1 — Clean up failed git init attempt (if any) and re-init

Open Git Bash, cd into the repo folder:

```bash
cd /c/Users/jakie/CoworkOps/Gratisfaction/repo
```

If a broken `.git` folder exists from earlier:

```bash
rm -rf .git
```

Then init fresh:

```bash
git init -b main
git config user.email "jakie.blunt@gmail.com"
git config user.name "Jakie Blunt"
git add -A
git commit -m "Initial commit: Gratisfaction Tuesday Topic Lab v1"
```

If that worked, `git log` will show your initial commit. Done with step 1.

---

## Step 2 — Create the GitHub repo (web)

1. Go to **[github.com/new](https://github.com/new)**
2. Repository name: `gratisfaction-podcast-system`
3. Description: `Tuesday topic prep + auto-ordered timeline for the Gratisfaction podcast`
4. **Public** or **Private** — your call (Cloudflare Pages works with either)
5. **DO NOT** check "Add a README" or "Add .gitignore" or "Choose a license"
   - We already have those locally; if GitHub adds them too you'll have to merge
6. Click **Create repository**

GitHub will show you a page with commands. Look for the section "**…or push an existing repository from the command line**". It'll show the exact remote URL to use in step 3.

---

## Step 3 — Connect local repo to GitHub and push

Replace `YOUR_USERNAME` with your GitHub username (it's whatever GitHub shows in the remote URL):

```bash
git remote add origin https://github.com/YOUR_USERNAME/gratisfaction-podcast-system.git
git branch -M main
git push -u origin main
```

It'll prompt for your GitHub credentials (use a personal access token if asked — see GitHub's docs if you don't have one configured).

After this, refresh your GitHub repo page in the browser — you should see all 4 files: `index.html`, `README.md`, `TUESDAY_WORKFLOW.md`, `.gitignore`.

---

## Step 4 — Connect Cloudflare Pages to the repo

1. Go to **[dash.cloudflare.com](https://dash.cloudflare.com)** → **Workers & Pages** → **Create application** → **Pages** tab
2. Click **Connect to Git** → authorize GitHub
3. Select `gratisfaction-podcast-system` from the list
4. Build settings:
   - Framework preset: **None**
   - Build command: leave **blank**
   - Build output directory: **/** (just a single forward slash, the root)
5. Click **Save and Deploy**
6. ~30 seconds later, visit the auto-generated `https://gratisfaction-podcast-system.pages.dev` URL — your dashboard should load

If the dashboard loads at the `.pages.dev` URL, the build is working. Move to step 5.

---

## Step 5 — Add the custom subdomain `gratisfaction.inkwellandiron.com`

In your Cloudflare Pages project:

1. Go to **Custom domains** tab
2. Click **Set up a custom domain**
3. Type: `gratisfaction.inkwellandiron.com`
4. Cloudflare will show you the DNS record to add. It will likely be a **CNAME** with:
   - Name: `gratisfaction`
   - Target: `gratisfaction-podcast-system.pages.dev` (or similar)

---

## Step 6 — Add the CNAME at GoDaddy

1. Go to **[godaddy.com](https://godaddy.com)** → **My Products** → click **`inkwellandiron.com`** → **DNS**
2. Click **Add New Record**
3. Type: **CNAME**
4. Name/Host: `gratisfaction`
5. Value/Points to: paste whatever Cloudflare gave you (e.g. `gratisfaction-podcast-system.pages.dev`)
6. TTL: 1 hour (or default)
7. Save

---

## Step 7 — Wait for DNS + SSL (5-30 min, passive)

Refresh the Cloudflare Pages **Custom domains** page until it shows **Active** with a green check.

Then visit: **https://gratisfaction.inkwellandiron.com**

It should load the dashboard with auto-provisioned SSL. Done.

---

## Step 8 — iPhone home screen + share with the guys

1. Open `https://gratisfaction.inkwellandiron.com` in iPhone Safari
2. Tap the share button (square with arrow up)
3. **Add to Home Screen** → name it "Gratisfaction"
4. Drop the URL in the group chat — Justin and Bobbye do the same

---

## After this is live

Every push to `main` from now on auto-deploys to the live subdomain in ~30 seconds. So when I (or you) update the dashboard:

```bash
cd /c/Users/jakie/CoworkOps/Gratisfaction/repo
# (make changes — or I'll output a diff for you to apply)
git add -A
git commit -m "describe what changed"
git push
```

That's it. Live in 30 sec.

---

## If something breaks

- **`git push` rejected**: GitHub repo had auto-init files. Either delete the GitHub repo and start over (recommended) or `git pull --rebase origin main` then push.
- **Cloudflare Pages build fails**: check build settings (Framework: None, Build command: blank, Output: `/`)
- **Custom domain stuck on "verifying"**: wait 30 min for DNS, refresh
- **`https://gratisfaction.inkwellandiron.com` loads but shows GoDaddy parking page**: CNAME at GoDaddy not propagated yet — wait
- **SSL warning**: cert provisioning still in progress, wait 10-15 min

Tell me which step you got stuck on and I'll debug.
