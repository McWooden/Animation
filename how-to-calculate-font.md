### 1. The Syntax Written
In the Tailwind classes, the syntax added was:
```css
text-[clamp(3rem,14vw,3.6rem)]
```

* **Tailwind Custom Utility `text-[...]`**: Uses Tailwind's arbitrary value notation to insert a raw CSS `clamp()` function.
* **`clamp(MIN, VAL, MAX)`**: A native CSS function that bounds a value between an upper and lower limit.

---

### 2. How the Responsiveness is Calculated

Here is how the browser calculates the font size dynamically as the screen size changes:

| Viewport Width | `14vw` Calculation (14% of width) | Clamped Font Size | Pixel Equivalent |
| :--- | :--- | :--- | :--- |
| **`320px`** (Mobile S) | `14% of 320px` = **`44.8px`** (`2.8rem`) | Clamped to **`3rem`** *(Minimum limit)* | **`48px`** |
| **`375px`** (Mobile M) | `14% of 375px` = **`52.5px`** (`3.28rem`) | Dynamic **`3.28rem`** *(Preferred)* | **`52.5px`** |
| **`425px`** (Mobile L) | `14% of 425px` = **`59.5px`** (`3.72rem`) | Clamped to **`3.6rem`** *(Maximum limit)* | **`57.6px`** |

---

### 3. Why `14vw` was selected
* **Characters per line**: The longest line on mobile is `"Coder Who"` (9 characters including spaces).
* **Target Fit**: To make the line fill the viewport width (minus the container's `40px` padding) on a `375px` screen, we want the text to be around `52px` to `54px`.
* **Formula**: $\text{Target Font Size} \div \text{Screen Width} = 52.5\text{px} \div 375\text{px} \approx 14\%$.
