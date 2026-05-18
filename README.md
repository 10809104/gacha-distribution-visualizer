# Gacha Distribution Visualizer
> 一個基於網頁的抽卡機率與分布模擬器，支援無保底、硬保底及軟保底模型。

![](https://img.shields.io/badge/Language-HTML%20%2F%20CSS%20%2F%20JavaScript-orange)
![](https://img.shields.io/badge/Library-Chart.js-blue)
![](https://img.shields.io/badge/License-MIT-green)

這個專案是一個單網頁應用程式（SPA），旨在幫助玩家與開發者直觀地理解不同抽卡機制（機制包含無保底、硬保底、軟保底）下的機率質量函數 (PMF) 與累積分布函數 (CDF)。

## 🌟 線上體驗 (Live Demo)
👉 **[點此進入網頁版模擬器](https://10809104.github.io/gacha-distribution-visualizer/)**

---

## 📊 核心功能

*   **三種主流模型切換**：
    *   **無保底模型 (No Guaranteed)**：標準的幾何分布，可自訂繪圖的抽數上限。
    *   **硬保底模型 (Fixed Cap)**：在第 $N$ 抽前機率固定，第 $N$ 抽強制出貨（極端值的非酋救贖）。
    *   **軟保底模型 (Soft Cap)**：模擬現代主流手遊（如原神、崩鐵），從第 $x$ 抽開始，每抽機率線性遞增 $y\%$。
*   **關鍵指標即時計算**：
    *   **期望抽數 ($E$)**：群體玩家拿到角色的平均成本。
    *   **綜合勝率 ($P_{\text{total}}$)**：引入保底機制後，倒數算出的真實綜合出貨率。
    *   **區間機率查詢**：輸入特定抽數 $n$，即時計算「n 抽內至少中一次」與「n 抽內完全沒中」的非歐機率。
*   **雙圖表動態可視化**：
    *   **PMF 曲線圖**：清晰展現「特定某一抽」的出貨機率，直觀觀察軟保底的「機率小山丘」與硬保底的「保底通天柱」。
    *   **CDF 曲線圖**：展現累積出貨率，斜率的劇烈轉折代表保底機制的介入。

---

## 📐 數學公式說明

### 1. 綜合勝率
綜合出貨率 $P_{\text{total}}$ 剛好等於期望抽數的倒數：
$$P_{\text{total}} = \frac{1}{E}$$

### 2. 硬保底期望值
在第 $N$ 抽前機率皆為固定值 $p$，其期望值 $E$ 的閉合形式為：
$$E = \frac{1-(1-p)^N}{p}$$

### 3. 軟保底期望值
當基礎機率 $p_n$ 隨抽數 $n$ 分段動態變化時，系統採用數值法窮舉求和：
$$E = \sum_{n=1}^{N} n \cdot P(X=n) \quad \text{其中 } P(X=n) = p_n \prod_{i=1}^{n-1}(1-p_i)$$

---

## 🛠️ 技術棧

*   **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
*   **Chart Library**: [Chart.js](https://www.chartjs.org/) (透過 CDN 引入，輕量且無外部依賴)

## 🚀 如何在本地運行

1. 複製本儲存庫：
   ```bash
   git clone [https://github.com/10809104/gacha-distribution-visualizer.git](https://github.com/10809104/gacha-distribution-visualizer.git)
