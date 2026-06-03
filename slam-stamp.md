The stamp animation is built using a combination of four synchronized animations. Here are the animation names and their properties:

### 1. Stamp Slam & Squash-and-Stretch (`stampSlam`)
This animates the physical stamp seal dropping down, squashing on impact, and spring-bounding back to its final shape:
* **CSS Selector**: `.hero-stamp-seal`
* **Animation Property**: `stampSlam 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.2) 0.9s forwards`
* **Keyframes**:
  ```css
  @keyframes stampSlam {
    0% {
      opacity: 0;
      transform: scale(3.5) rotate(25deg);
      filter: blur(4px);
    }
    60% {
      opacity: 1;
      transform: scale(0.85, 0.7) rotate(-5deg); /* Squashed vertically */
      filter: blur(0);
    }
    80% {
      transform: scale(1.1, 1.15) rotate(2deg); /* Stretched vertically */
    }
    100% {
      opacity: 1;
      transform: scale(1) rotate(0deg); /* Settle */
    }
  }
  ```

---

### 2. Document Shake (`docImpactShake`)
This shakes the entire document slightly when the stamp hits (at `1.2s` delay) to simulate physical force:
* **CSS Selector**: `.hero-signing-shake`
* **Animation Property**: `docImpactShake 0.45s ease 1.25s`
* **Keyframes**:
  ```css
  @keyframes docImpactShake {
    0%, 100% { transform: translate(0, 0) rotate(0deg); }
    15% { transform: translate(-3px, 2px) rotate(-0.5deg); }
    30% { transform: translate(3px, -2px) rotate(0.8deg); }
    45% { transform: translate(-2px, 1px) rotate(-0.3deg); }
    60% { transform: translate(1px, 2px) rotate(0.2deg); }
    75% { transform: translate(-1px, -1px) rotate(-0.1deg); }
  }
  ```

---

### 3. Impact Ripple Wave (`stampRipple`)
An expanding circle representing the ink ripple/shockwave radiating from the stamp center:
* **CSS Selector**: `.hero-stamp-ripple`
* **Animation Property**: `stampRipple 0.8s cubic-bezier(0.16, 1, 0.3, 1) 1.2s forwards`
* **Keyframes**:
  ```css
  @keyframes stampRipple {
    0% {
      transform: scale(0.8);
      opacity: 0.8;
      stroke-width: 4;
    }
    100% {
      transform: scale(2.8);
      opacity: 0;
      stroke-width: 0.5;
    }
  }
  ```

---

### 4. Checkmark Drawing (`drawCheck`)
Draws the purple checkmark inside the stamp seal from the center outwards on impact:
* **CSS Selector**: `.hero-stamp-check`
* **Animation Property**: `drawCheck 0.4s ease 1.2s forwards`
* **Keyframes**:
  ```css
  @keyframes drawCheck {
    to { stroke-dashoffset: 0; }
  }
  ```
