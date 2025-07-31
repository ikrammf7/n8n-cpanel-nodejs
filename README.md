## N8N Setup on cPanel with Node.js Selector

### ✅ Initial Setup

1. **Enable Shell Access** for the cPanel account (Terminal access).
2. Let **AutoSSL** run on the domain.

### ⚙️ Create NodeJS App in cPanel

3. Go to **"Setup Node.js App"** in cPanel.
4. Enter:
   - **Node.js version** (e.g., 20.x)
   - **Application mode**: `development`
5. Click **Create**.
   - ❗ Do **not** set custom application paths or add other settings.
   - The default startup file (`app.js`) will be changed later.
6. After creation, **copy the virtual environment activation command** from the top of the app page.

### 💻 Install N8N via Terminal

7. Open **cPanel Terminal**.
8. **Paste** the previously copied virtual environment command.
9. Inside the environment, run:

```bash
npm init -y
```
```bash
npm install n8n
```

### 🔧 Configure Node Application
10. Go back to the Node.js App page in cPanel.
11. Change the Startup File to: `node_modules/n8n/bin/n8n`

12. Set the following Environment Variables:

| Variable                  | Value                                  |
| ------------------------- | -------------------------------------- |
| `N8N_BASIC_AUTH_ACTIVE`   | `true`                                 |
| `N8N_BASIC_AUTH_USER`     | `[username]`                           |
| `N8N_BASIC_AUTH_PASSWORD` | `[password]`                           |
| `N8N_HOST`                | `set to 0.0.0.0`                       |
| `WEBHOOK_URL`             | `https://your-installation-domain.com` |

13. Change the Application Mode to `production`.

🔐 Final Steps

14. Open your domain in a browser.
15. Create an owner account – this will be used for login.
16. Register a community license (optional) to unlock premium features.

🔄 Optional: Auto-Update Workflow
To keep n8n up to date automatically:
1. Create a workflow using the Execute Command module.
2. Write a shell script to update n8n.
    (You can use ChatGPT to help write this script.)
3. Schedule the workflow to run every 24 hours.
    🔁 Also remember to update the NodeJS version in cPanel annually to stay within supported versions.

**Source:** [MattH](https://community.n8n.io/u/MattH)
