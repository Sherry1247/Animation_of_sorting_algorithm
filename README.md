# ⇅ SortViz

> **Interactive, step-by-step sorting algorithm visualizer** — built for exam prep, classroom learning, and the occasional existential dread of watching Thanos snap half your array.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Algorithms](https://img.shields.io/badge/algorithms-13-green.svg)](#algorithms)
[![Languages](https://img.shields.io/badge/code-Java%20%7C%20Python%20%7C%20C%20%7C%20C%2B%2B-orange.svg)](#code-panel)
[![Single File](https://img.shields.io/badge/deploy-single%20HTML-purple.svg)](#usage)

---

## 📸 Preview

Load any array, pick an algorithm, and step through every comparison, swap, and partition — one frame at a time. Designed for the exact kind of "what does the array look like after the first recursion?" questions that show up on midterms.

---

## ✨ Features

| Feature | Details |
|---|---|
| **Step-by-step trace** | Every comparison, swap, shift, and merge shown individually |
| **Bar visualization** | Color-coded bars with value + index labels |
| **Pointer labels** | L / H / P markers float above bars (Quick Sort) |
| **Heap tree diagram** | Live SVG tree updates during Heap Sort |
| **Trace table** | Click any row to jump directly to that step |
| **Multi-language code** | Java, Python, C, C++ for every algorithm |
| **Complexity table** | Best / Average / Worst / Space / Stable rating per algorithm |
| **Keyboard controls** | `←` `→` to step, `Space` to play/pause |
| **Speed control** | Adjustable animation delay (60ms – 950ms) |
| **Custom input** | Enter your own array or generate a random one |
| **Zero dependencies** | Single self-contained HTML file, no build step |

---

## 🚀 Usage

### Option 1 — Open directly
Download `sorting_visualizer.html` and open it in any modern browser. No server needed.

### Option 2 — GitHub Pages
1. Fork this repository
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Visit `https://<your-username>.github.io/<repo-name>/sorting_visualizer.html`

### Option 3 — Serve locally
```bash
# Python
python -m http.server 8080

# Node.js
npx serve .
```
Then open `http://localhost:8080/sorting_visualizer.html`

---

## 📚 Algorithms

### 🔷 Classic Sorts

| Algorithm | Best | Average | Worst | Space | Stable |
|---|---|---|---|---|---|
| **Bubble Sort** | O(n) | O(n²) | O(n²) | O(1) | ✅ |
| **Insertion Sort** | O(n) | O(n²) | O(n²) | O(1) | ✅ |
| **Selection Sort** | O(n²) | O(n²) | O(n²) | O(1) | ❌ |
| **Merge Sort** | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ |
| **Quick Sort** | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ |
| **Heap Sort** | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ |

### 🔶 Advanced Sorts

| Algorithm | Best | Average | Worst | Space | Stable |
|---|---|---|---|---|---|
| **Shell Sort** | O(n log n) | O(n log² n) | O(n²) | O(1) | ❌ |
| **Counting Sort** | O(n+k) | O(n+k) | O(n+k) | O(k) | ✅ |
| **Radix Sort (LSD)** | O(nk) | O(nk) | O(nk) | O(n+k) | ✅ |

### 🎭 For Fun

| Algorithm | Description |
|---|---|
| **慈禧 Sort 👑** | Imperial tribute sort. Position 0 becomes 1; every subsequent element is exactly 1 more than the previous. Your original values are irrelevant. Pay your reparations. |
| **Thanos Sort ✪** | Checks if sorted. If not, randomly eliminates exactly half the elements. Repeats. Perfectly balanced, as all things should be. |
| **Führersort ☠** | Does not sort. Simply declares the array sorted. O(1) time, O(1) space, 0% correctness. History will vindicate it. |
| **Stalin Sort 🔴** | Scans left to right. Any element smaller than the previous one is permanently eliminated. One pass. No mercy. Guaranteed sorted output (by removal). |

> ⚠️ Fun sorts are satire. The historical figures referenced are not endorsed; the jokes mock authoritarianism and delusion, not their victims.

---

## 🎯 Exam Prep Tips

This tool was built specifically to answer the kinds of questions that appear on CS midterms:

**"What does the array look like after the first partition?"**
→ Select Quick Sort → press Next until you see the "Partition done" step

**"Show the array after building the max-heap"**
→ Select Heap Sort → step through until the heap tree is complete

**"Trace 2 passes of bubble sort"**
→ Select Bubble Sort → the trace table labels every pass clearly

**"What is the state after the first merge?"**
→ Select Merge Sort → the split and merge steps are shown separately

**For any algorithm:** The trace table on the right shows every intermediate array state with color coding. Click any row to jump to that exact moment.

---

## 🧩 Quick Sort Details

This visualizer uses the **middle-element pivot** with **Hoare-style L/H pointers**, which is the variant most commonly taught in university courses:

```
pivot = arr[(l + r) / 2]
L starts at left boundary, H starts at right boundary
L advances while arr[L] < pivot
H retreats while arr[H] > pivot
Swap when L ≤ H, then L++, H--
Recurse on [l..H] and [L..r]
```

The bars display floating labels: **P** (pivot), **L** (left pointer), **H** (right pointer).

---

## 💻 Code Panel

Every algorithm includes implementations in **Java**, **Python**, **C**, and **C++**, accessible via the tabs below the trace table. The code prioritizes **clarity over cleverness** — written to match what you'd see in a textbook or write on an exam.

---

## 🗂 File Structure

```
sortviz/
├── sorting_visualizer.html   # Entire app — single file, zero dependencies
└── README.md
```

The app is intentionally a **single HTML file** for maximum portability. No npm, no webpack, no framework. Open it anywhere.

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|---|---|
| `→` | Next step |
| `←` | Previous step |
| `Space` | Play / Pause |

---

## 🛠 Browser Support

Works in all modern browsers. Requires ES6+ support (Chrome 60+, Firefox 55+, Safari 12+, Edge 79+).

---

## 🤝 Contributing

Contributions welcome! Ideas:

- Add more algorithms (Tim Sort, Cocktail Sort, Bogo Sort...)
- Add more fun sorts (propose in Issues)
- Dark/light theme toggle
- Export trace as PDF / image
- Add a "quiz mode" that hides the next state

**To add a new algorithm:**
1. Add an entry to the `ALGOS` array with `id`, `name`, `group`, complexity fields, `desc`, and `code` (all 4 languages)
2. Write a `genXxx(a)` step generator function following the existing pattern
3. Add it to the `genSteps` dispatch map
4. Add a legend entry to `LEGENDS`

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

Free to use for personal projects, coursework, and teaching. If this helped you pass your midterm, a ⭐ on GitHub is appreciated.

---

## 🙏 Acknowledgments

- Algorithm complexity references: [Big-O Cheat Sheet](https://bigocheatsheet.com)
- Inspired by [VisuAlgo](https://visualgo.net) and [Sorting.at](https://sorting.at)
- Fun sort concepts: internet folklore / CS humor community
- Built with vanilla HTML/CSS/JS — no libraries harmed

---

*"The purpose of a sorting algorithm is to bring order to chaos — unless you are Thanos, in which case the purpose is to bring chaos to order."*
