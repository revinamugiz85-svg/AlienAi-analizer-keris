# AlienAI Keris Analyzer - Frontend Export

This document contains the complete frontend export for the AlienAI Keris Analyzer application, including both a unified HTML/CSS implementation and a modular React architecture.

---

## 1. Project Overview
- **Brand**: AlienAI Keris Analyzer
- **Design System**: Celestial Heritage (Light Mode, Premium Mystical Aesthetic)
- **Primary Colors**: Surface (#fefccf), Primary/Gold (#0a192f used as base for accent tokens), Cyan/High-tech accents.
- **Typography**: Playfair Display (Serif) & Inter (Sans-serif)

---

## 2. Global CSS Variables (Tailwind Extension)
```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        surface: '#fefccf',
        'surface-dim': '#dedcb1',
        'primary-container': '#0a192f',
        'on-primary-container': '#fefccf',
        accent: '#00dce5', // Cyan glow
        gold: '#d4af37',
      },
      fontFamily: {
        display: ['Playfair Display', 'serif'],
        sans: ['Inter', 'sans-serif'],
      },
    },
  },
}
```

---

## 3. React Implementation (Modular)

### App.js (Navigation Flow)
```jsx
import React, { useState } from 'react';
import Home from './screens/Home';
import Upload from './screens/Upload';
import ScanAnimation from './screens/ScanAnimation';
import AnalysisResult from './screens/AnalysisResult';
import Payment from './screens/Payment';
import Success from './screens/Success';
import Certificate from './screens/Certificate';
import Profile from './screens/Profile';
import Admin from './screens/Admin';

const App = () => {
  const [currentScreen, setCurrentScreen] = useState('HOME');

  const renderScreen = () => {
    switch (currentScreen) {
      case 'HOME': return <Home onStart={() => setCurrentScreen('UPLOAD')} />;
      case 'UPLOAD': return <Upload onScan={() => setCurrentScreen('SCANNING')} />;
      case 'SCANNING': return <ScanAnimation onComplete={() => setCurrentScreen('RESULT')} />;
      case 'RESULT': return <AnalysisResult onPay={() => setCurrentScreen('PAYMENT')} />;
      case 'PAYMENT': return <Payment onSuccess={() => setCurrentScreen('SUCCESS')} />;
      case 'SUCCESS': return <Success onDone={() => setCurrentScreen('CERTIFICATE')} />;
      case 'CERTIFICATE': return <Certificate />;
      case 'PROFILE': return <Profile />;
      case 'ADMIN': return <Admin />;
      default: return <Home />;
    }
  };

  return (
    <div className="min-h-screen bg-surface font-sans text-primary-container">
      {renderScreen()}
      <BottomNavBar active={currentScreen} onChange={setCurrentScreen} />
    </div>
  );
};
```

### Component: TopAppBar.jsx
```jsx
const TopAppBar = ({ title, showNotification = true }) => (
  <header className="flex justify-between items-center w-full px-6 py-4 border-b border-black/10 backdrop-blur-xl bg-surface/80 sticky top-0 z-50">
    <div className="flex items-center gap-3">
      <img src="{{DATA:IMAGE:IMAGE_10}}" alt="Logo" className="w-10 h-10 rounded-full" />
      <h1 className="font-display text-xl font-bold tracking-tight text-primary-container">AlienAI</h1>
    </div>
    {showNotification && <button className="p-2"><i className="material-icons">notifications</i></button>}
  </header>
);
```

---

## 4. Key Screens (HTML Snippets)

### Screen: AI Analysis Result (SCREEN_30)
```html
<!-- Main Content Area -->
<main class="p-6 space-y-8 animate-fade-in">
  <section class="text-center">
    <span class="px-4 py-1 rounded-full border border-accent/30 text-accent text-xs uppercase tracking-widest font-bold">AI Confidence Analysis</span>
    <h2 class="text-4xl font-display mt-4">98.4%</h2>
    <div class="w-full bg-black/10 h-1 rounded-full mt-2 overflow-hidden">
      <div class="h-full bg-accent w-[98.4%] shadow-[0_0_8px_rgba(0,220,229,0.5)]"></div>
    </div>
  </section>

  <!-- Dapur Section -->
  <div class="bg-white/40 p-6 rounded-2xl border border-black/5">
    <div class="flex justify-between items-start">
      <div>
        <p class="text-xs text-primary-container/60 uppercase font-bold tracking-widest">Dapur Keris</p>
        <h3 class="text-2xl font-display mt-1">Naga Siluman</h3>
      </div>
      <i class="material-icons text-primary-container/20">auto_awesome</i>
    </div>
    <p class="mt-4 text-sm leading-relaxed opacity-80">Struktur bilah memiliki karakteristik *luk* yang elegan dengan stilasi kepala naga pada bagian *gandhik*.</p>
  </div>
</main>
```

### Screen: Digital Certificate (SCREEN_12)
```html
<div class="m-6 p-8 bg-white shadow-2xl border-[12px] border-double border-[#d4af37] relative overflow-hidden">
  <div class="absolute inset-0 opacity-5 pointer-events-none" style="background-image: url('{{DATA:IMAGE:IMAGE_23}}'); background-size: cover;"></div>
  <div class="text-center">
    <img src="{{DATA:IMAGE:IMAGE_10}}" class="w-24 mx-auto mb-6" />
    <h2 class="font-display text-3xl uppercase tracking-[0.2em] mb-2">Sertifikat Otentikasi</h2>
    <hr class="border-[#d4af37]/30 my-4" />
    <p class="text-[10px] tracking-widest opacity-60">PROTOCOL ALIEN-SCAN V.4.2</p>
  </div>
  <!-- Keris Art Frame -->
  <div class="mt-8 rounded-xl overflow-hidden relative border border-[#d4af37]/20">
    <img src="{{DATA:IMAGE:IMAGE_23}}" class="w-full h-64 object-cover" />
    <div class="absolute top-4 left-4 px-3 py-1 bg-black/60 backdrop-blur-md rounded-full text-[10px] text-accent">
      • STRUCTURAL INTEGRITY: 98.4%
    </div>
  </div>
  <!-- Digital Signature -->
  <div class="mt-12 flex justify-end">
    <img src="{{DATA:IMAGE:IMAGE_5}}" class="w-32 opacity-80" />
  </div>
</div>
```

---

## 5. Deployment Instructions
1. **Assets**: Ensure all image placeholders (`{{DATA:IMAGE:...}}`) are replaced with the provided PNG/SVG assets in your static directory.
2. **Framework**: The UI is built using Tailwind CSS utility classes. Ensure the Tailwind CDN or PostCSS plugin is configured.
3. **Fonts**: Import 'Playfair Display' and 'Inter' from Google Fonts.
