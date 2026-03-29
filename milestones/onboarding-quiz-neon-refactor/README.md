# Case Study: Onboarding Quiz & Dynamic Select2 Refactor 🦩

## 📋 Overview
In this milestone for **Label MBA**, I led the visual transformation of a lead-capture tool. The goal was to convert a standard, generic third-party form into a high-end "Cinematic Neon" experience, ensuring 100% brand alignment with the music industry aesthetic.

## 🛠️ The Technical Challenge
The third-party library used for the quiz injected elements into the DOM with **Dynamic IDs** (e.g., `select2-forminator-69c536...`). This rendered traditional static CSS selectors useless.

### Key Problems:
1. **Selector Volatility:** IDs changed on every page refresh, breaking custom styles.
2. **Style Bleeding:** Default plugin styles (blue outlines, white backgrounds) clashed with the Dark Mode requirements.
3. **Asset Masking:** Integrating a non-transparent brand GIF (The Flamingo) without creating a "boxy" visual artifact.

---

## 💡 The Engineering Solution

### 1. Dynamic Attribute Targeting
Instead of targeting volatile IDs, I implemented **CSS Attribute Selectors** with wildcards to hook into the persistent parts of the dynamic strings:

```css
/* Target any span whose ID contains the Forminator container string */
span[id*="select2-forminator"] {
    color: #ffffff !important;
    background-color: transparent !important;
}

2. Visual Layering (Glassmorphism)
To create depth without compromising performance, I implemented a layering system using rgba transparencies and backdrop-filter: blur(). This ensured text legibility on dark backgrounds while maintaining the "Neon" glow effect.

3. State-Based UI Orchestration
I used CSS advanced combinators to detect the "active" state of the quiz steps. This allowed me to toggle the visibility of global headers and focus the user's attention solely on the questions:

/* Hide global title only when the specific quiz module is active */
#quiz-module:not([style*="display: none"]) ~ .global-header {
    display: none;
}

## 📸 Visual Comparison

| Before (Generic Library UI) | After (Custom Neon UI) |
| :---: | :---: |
| ![Before 1](../../assets/quiz-before-1.png) | ![After 1](../../assets/quiz-after-1.png) |
| ![Before 2](../../assets/quiz-before-2.png) | ![After 2](../../assets/quiz-after-2.png) |