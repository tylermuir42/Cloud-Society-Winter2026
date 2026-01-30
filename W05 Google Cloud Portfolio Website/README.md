# Week 05

This README is designed for your 1-hour workshop. It’s written with a "peer-to-peer" vibe—professional enough for a university setting, but with enough wit to keep a room full of CS students from falling asleep.

---

# 🚀 Workshop: Launch Your Portfolio in 60 Minutes

**Cloud Solutions Society** _Hosting a static site using Google Cloud Firebase_

Welcome! Today, we’re moving your portfolio from "it works on my machine" to "it’s live on the global CDN." We’re using **Firebase Hosting**, a production-grade tool that handles SSL, custom domains, and lightning-fast delivery for you.

---

## 🛠️ Step 1: The Foundations (Node.js)

Firebase’s command-line tools run on **Node.js**. If you don’t have it, your terminal will have no idea what we’re trying to do.

1. Go to [nodejs.org](https://nodejs.org/).
2. Download the **LTS (Long Term Support)** version.
3. Run the installer. (Keep the defaults; they’re smart).
4. **Verify it:** Open your terminal (Command Prompt, PowerShell, or Zsh) and type:

```bash
node -v
npm -v

```

_If you see version numbers, you’re golden._

---

## ☁️ Step 2: The Command Center (Firebase Console)

Before we code, we need a "home" in the cloud.

1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Sign in with your Google account.
3. Click **"Add project"**.
4. **⚠️ The Golden Rule of DNS:** Your Project ID becomes your URL (e.g., `your-name.web.app`).

- **Pro-Tip:** Keep the name **short, lowercase, and unique**. Avoid things like `my-portfolio-v3-final-really-final`.

5. (Optional) Disable Google Analytics for this workshop to save 30 seconds of clicking.
6. Click **Create Project**. Once the cloud finishes spinning, click **Continue**.

---

## 🧰 Step 3: The Toolkit (Firebase CLI)

Now we tell your computer how to talk to Google Cloud. In your terminal, run:

```bash
npm install -g firebase-tools

```

> **Note:** On Mac/Linux, if you get a "Permission Denied" error, you might need to run `sudo npm install -g firebase-tools`.

---

## 🏗️ Step 4: The Local Setup

Let’s create a place for your files to live.

1. **Create a folder:** `mkdir portfolio`
2. **Move into it:** `cd portfolio`
3. **Log in:** ```bash
   firebase login

```
*This will pop open a browser. Log in with the same Google account you used in the console.*


```

---

## 🪄 Step 5: The Terminal Wizard (The "Init")

This is where the magic happens. Run:

```bash
firebase init

```

The wizard will ask you some questions. Use your **arrow keys** and **spacebar** to answer:

1. **Which features?** Select `Hosting: Set up deployments for static web apps`
2. **Project Setup?** Choose `Use an existing project`.
3. **Select your project:** Find the short/unique name you created in Step 2.
4. **Public directory?** Press Enter to keep the default `public`.
5. **Single-page app?** Type `N` (for a standard portfolio).
6. **GitHub Deploys?** Type `N` (we’ll stick to manual for now).

---

## 🎡 Step 6: Test Locally

Firebase lets you run a local "mock" of their servers so you don’t have to deploy every time you change a comma.

1. Open the `public/index.html` file that Firebase just created. Change the `<h1>` to say "Hello World, This is [Your Name]".
2. In your terminal, run:

```bash
firebase serve

```

3. Open `http://localhost:5000` in your browser. If you see your change, you’re ready for the big leagues.

---

## 🚀 Step 7: The Grand Finale (Deploy)

Ready to go live? One command:

```bash
firebase deploy

```

Wait for the progress bars to finish. At the bottom, you’ll see a **Hosting URL**. Click it. Congrats—you are officially a Cloud Engineer.

---

### 💡 Troubleshooting for Pros

- **Command not found:** Restart your terminal after installing Node.js.
- **Wrong project:** Run `firebase use --add` to switch to a different project ID.
- **Stuck?** Ask a lead. We don't bite; we just debug.

---

This template is designed to be a "single-file wonder." By keeping the CSS inside the HTML file, we minimize the chance of students getting lost in file paths during a timed workshop.

It’s modern, dark-themed (because we're CS students, after all), and fully responsive.

### 📄 The Portfolio Template

Open `public/index.html` in their code editor (like VS Code), delete everything inside, and paste in the contents from `portfolio.html` in this folder:

### 🎨 Make Changes:

1. **Personalize it:** Change the "Your Name" and "About Me" sections immediately.
2. **Save the file.**
3. **Run `firebase serve`:** This lets them see their beautiful new site on `localhost:5000`.
4. **Final Deploy:** Run `firebase deploy` to push the "real" version live.

---

### 🚀 Bonus Challenge - Adding an Image

1. Put an image file (like `profile.jpg`) inside the `public/` folder.
2. Add `<img src="profile.jpg" style="width: 150px; border-radius: 50%;">` inside the `<header>`.
3. Re-deploy!

This is a fantastic addition. Transitioning from manual deployments to **CI/CD (Continuous Integration/Continuous Deployment)** is exactly the "aha!" moment students need to move from hobbyist to professional.

The best part? Firebase has a built-in command that automates about 90% of the GitHub Actions setup, including the generation of service account keys.

---

# ♾️ Level 2: Automating with DevOps (GitHub Actions)

Now that your site is live, let's make it so you never have to run `firebase deploy` manually again. We want the cloud to detect your code changes and deploy them for you.

---

Adding a "Step 0" for Git is a smart move. In a room full of students, you'll always have that one person who just got a new laptop or usually only uses the web interface.

Here is the Git installation section to slot in right at the beginning of your README.

---

## 🕒 Step 8: The "Time Machine" (Installing Git)

Before we can use GitHub Actions, your computer needs to know how to track code changes. Git is the industry standard for version control.

### **1. Install for your OS**

- **Windows:** Download and run the **[Git for Windows](https://git-scm.com/download/win)** installer.
- _Pro-tip:_ Just keep clicking "Next" on the defaults. They are optimized for developers.

- **macOS:** You might already have it! Open your terminal and type `git --version`. If it asks you to install "command line developer tools," say **Yes**.
- Alternatively, use Homebrew: `brew install git`.

- **Linux:** Use your package manager: `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora).

### **2. Introduce Yourself to Git**

Git needs to know who you are so your name shows up on your commits. Run these two commands in your terminal (using your own info, obviously):

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

```

### **3. Verify the Installation**

Run this command:

```bash
git --version

```

If you see `git version 2.x.x`, you are officially ready to start building.

---

## 🐙 Step 9: Initialize Git & GitHub

Before we can automate, we need our code in the cloud.

1. **Initialize Git:** In your `portfolio` folder, run:

```bash
git init
git add .
git commit -m "feat: initial portfolio setup"

```

2. **Create a Repo:** Go to [GitHub](https://github.com/new) and create a new repository named `my-cloud-portfolio`. Keep it **Public**.
3. **Link and Push:** Copy the commands from GitHub to link your local folder and push:

```bash
git remote add origin https://github.com/YOUR_USERNAME/my-cloud-portfolio.git
git branch -M main
git push -u origin main

```

---

## 🤖 Step 10: The DevOps Shortcut

Firebase has a specialized "wizard" for GitHub Actions. Run this in your terminal:

```bash
firebase init hosting:github

```

**The Wizard will ask:**

1. **For which GitHub repository?** Type `YOUR_USERNAME/my-cloud-portfolio`.
2. **Set up a service account?** Type `Y` (This allows GitHub to talk to Google Cloud safely).
3. **Set up a workflow to run a build script before every deploy?** Type `N` (Since we are using plain HTML, we don't need a build step).
4. **Set up automatic deploy when a PR is merged?** Type `Y`.
5. **What is the name of the main branch?** It should default to `main`. Press Enter.

---

## 🔎 Step 11: Understanding the YAML

Open the newly created file at `.github/workflows/firebase-hosting-merge.yml`. This is your "Pipeline-as-Code."

- **`on: push`**: This tells GitHub to wake up whenever code is pushed to the `main` branch.
- **`jobs`**: This defines a virtual machine (Ubuntu) that GitHub spins up to run your commands.
- **`secrets.FIREBASE_SERVICE_ACCOUNT_...`**: This is a secure key the CLI automatically generated and stored in your GitHub Repository settings.

---

## 🚀 Step 12: The "Look Ma, No Hands" Test

Let's see the automation in action.

1. Open your `public/index.html`.
2. Change a line of text (e.g., change your subtitle or add a new project).
3. **Commit and Push:**

```bash
git add .
git commit -m "test: checking github actions pipeline"
git push origin main

```

4. **Watch the Magic:** Go to your GitHub repository and click the **"Actions"** tab. You’ll see a yellow circle (meaning it’s working). Once it turns into a green checkmark, your website has been updated automatically!

---

### 🎨 Bonus: The "I'm a Professional" Status Badge

Once your GitHub Action runs successfully, you can add this snippet to the **very top** of your `README.md` file to show off:

```markdown
![Deploy Status](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME/actions/workflows/firebase-hosting-merge.yml/badge.svg)
```

_(Replace the placeholders with your actual GitHub username and repo name.)_

---

### 🛡️ Pro-Tips for the Lab Leads

- **Permissions:** If students get a 403 error during the `firebase init hosting:github` step, ensure they are logged into the GitHub CLI or have authorized the Firebase browser popup correctly.
- **The `.gitignore`:** Remind students that Firebase automatically ignores `node_modules`. This is a good time to explain why we never push `node_modules` to GitHub.

---
