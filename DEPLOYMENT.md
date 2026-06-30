# Deployment Guide: Hostel Wi-Fi Auto-Login Web App

You can share this web app with your friends so they can generate their own automated login installers. Here are three super easy ways to publish this website online for free:

---

## Method 1: Netlify (Easiest - Drag & Drop)
This takes less than 30 seconds and requires no account creation or coding:

1. Open your browser and go to **[app.netlify.com/drop](https://app.netlify.com/drop)**.
2. Drag and drop the entire `hostel-wifi-autologin-web` folder into the dotted upload box on that webpage.
3. Your site will be deployed instantly! Netlify will provide a public link (e.g., `https://random-name.netlify.app`) that you can copy and share with your friends.
4. *(Optional)* You can sign up for a free Netlify account to customize the name of the link (e.g., `https://my-hostel-wifi.netlify.app`).

---

## Method 2: Vercel (Super Fast - Drag & Drop)
Another great drag-and-drop option that is extremely fast and reliable:

1. Go to **[vercel.com](https://vercel.com)** and sign up for a free account.
2. Go to your dashboard and click **Add New Project**.
3. Under the upload options, select **Vercel CLI or Drag & Drop** (or go to **[vercel.com/new](https://vercel.com/new)**).
4. Drag your `hostel-wifi-autologin-web` folder onto the page.
5. Vercel will deploy the site and give you a shareable link (e.g., `https://hostel-wifi.vercel.app`).

---

## Method 3: GitHub Pages (For Git users)
If you want to keep the source code on GitHub and have it auto-deploy:

1. Create a new repository on GitHub named `hostel-wifi` (or any name you like).
2. Push the files (`index.html`, `style.css`, and `app.js`) to the repository:
   ```bash
   git init
   git add .
   git commit -m "initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/hostel-wifi.git
   git branch -M main
   git push -u origin main
   ```
3. On GitHub, go to your repository **Settings** -> **Pages** (on the left side menu).
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
5. Select the **`main`** branch and click **Save**.
6. Wait 1-2 minutes, and your site will be live at `https://YOUR_USERNAME.github.io/hostel-wifi/`.

---

## Local Testing
To test the website locally on your own computer before uploading:
1. Double-click **`index.html`** in your project folder to open it in your browser.
2. Fill in the form and click **Generate & Download ZIP**.
3. It will download a customized `hostel-wifi-autologin.zip` file containing your credentials. You can unzip and inspect it to make sure the credentials in `config.json` match!
