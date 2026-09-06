# LLM-Testing
在本地端串接LLM模型與ChromaDB、Vtube Studio等工具完成模型驅動之Vtuber。
本專案是經由AI協助完成。

---

系統流程圖為：

<img src="img/LLM流程.png" width="40%" />

---

# 各功能說明

---

<table>
  <tr>
    <td align="center">
      <b>功能</b>
    </td>
    <td align="center">
      <b>說明</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>STT (Speech-to-Text)</b>
    </td>
    <td align="center">
      <b>使用 Google Speech API 以及文字輸入介面</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>短期記憶</b>
    </td>
    <td align="center">
      <b>保留最新的幾輪的對話上下文，確保對話連貫性</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>長期記憶</b>
    </td>
    <td align="center">
      <b>採用 ChromaDB 作為資料庫，將過去對話存入</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>LLM</b>
    </td>
    <td align="center">
      <b>透過本地端的 LM Studio 部署 Llama 3.2 語言模型，並透過自訂之 Tokenizer 達到特定對話風格之功能</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>動作與反應</b>
    </td>
    <td align="center">
      <b>從 LLM 生成的文本中即時提取動作標籤，透過 WebSocket API與 VTubeStudio 進行通訊，觸發對應的 Live2D 模型熱鍵，實現語音與肢體動作的同步 </b>
    </td>
  </tr>
</table>

---

# 風格對話功能實現方法

對話資料來源：田中芳樹《銀河英雄傳說》

對話資料處理平台：Google Colab

對話資料處理方法：

1. 進行資料清洗並對話擷取，建立動作標籤與角色性格標籤，整理成對話文本，並將其轉成包含 instruction 與 output 的 JSONL 檔案

2. 訓練繁體中文之 Tokenizer

3. 對 Llama 3.2 模型進行微調

---

# 目前仍待解決問題

<table>
  <tr>
    <td align="center">
      <b>LLM</b>
    </td>
    <td align="center">
      <b>風格化的對話表現不佳，溝通時語意不通順。</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <b>Vtube Studio</b>
    </td>
    <td align="center">
      <b>因動作標籤產生錯誤導致VTS的動作錯誤。</b>
    </td>
  </tr>
</table>
