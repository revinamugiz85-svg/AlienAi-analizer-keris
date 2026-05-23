# AlienAI Keris Analyzer - GitHub Deployment Repository

This repository contains the complete source code for the **AlienAI Keris Analyzer** mobile application. Optimized for React and Tailwind CSS, this project is ready for one-click deployment to Netlify or Vercel.

## 🚀 Live Preview
Once deployed, your app will be accessible at: `https://[your-project-name].netlify.app`

---

## 📦 Project Structure
```text
alienai-keris-analyzer/
├── public/
│   ├── index.html        # Entry point with mobile-first meta tags
│   └── assets/           # Brand assets, logos, and illustrations
├── src/
│   ├── components/       # Shared UI (TopBar, BottomNav, etc.)
│   ├── screens/          # Core screens (Home, Scan, Analysis, Payment, Cert)
│   ├── App.js            # Main routing and state management
│   └── index.css         # Global styles & Tailwind directives
├── tailwind.config.js    # Celestial Heritage design tokens
├── package.json          # Dependency manifest
└── README.md             # This guide
```

---

## 🛠️ Step-by-Step Deployment (to Netlify)

1. **Create a GitHub Repo**: Go to [GitHub](https://github.com/new) and create a repository named `alienai-keris-analyzer`.
2. **Push Code**: Upload the files from this document to your new repository.
3. **Connect to Netlify**:
   - Login to [Netlify](https://app.netlify.com).
   - Click **"Add new site"** > **"Import an existing project"**.
   - Select **GitHub** and authorize.
   - Choose the `alienai-keris-analyzer` repository.
4. **Build Settings**:
   - **Build Command**: `npm run build`
   - **Publish Directory**: `dist` (or `build`)
5. **Deploy**: Click **"Deploy site"**. Your app will be live in seconds!

---

## 🎨 Design System: Celestial Heritage
- **Typography**: Playfair Display (Headers), Inter (Body)
- **Colors**: Surface (#fefccf), Primary Container (#0a192f), Accent Cyan (#00dce5)
- **Assets**: Integrated with high-fidelity AI-generated visuals for Keris authentication.

---

## 📜 License
Internal project for AlienAI Keris Analyzer. All rights reserved.
