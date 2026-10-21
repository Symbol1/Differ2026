# 給 AI 助理

- 使用者用注音輸入法，有時忘記切換，訊息會變成按鍵本身的「火星文」，例如 `su3cl3`（ㄋㄧˇ ㄏㄠˇ，你好）、`ji394su3`（ㄨㄛˇ ㄞˋ ㄋㄧˇ，我愛你）、`hk4g4`（ㄘㄜˋ ㄕˋ，測試）。看到英文字母夾著 `3`、`4`、`6`、`7` 或 `,`、`.`、`/`、`;` 的怪字串時，不要當成亂碼或英文縮寫：先依下面的大千式鍵位轉回注音（`3`、`4`、`6`、`7` 與空白是聲調，也是字與字的分界），再大致轉成漢語拼音，用讀音猜意思。猜不準時，在 chat 中說出猜測並向使用者確認。

  ```text
  1ㄅ 2ㄉ 3ˇ 4ˋ 5ㄓ 6ˊ 7˙ 8ㄚ 9ㄞ 0ㄢ -ㄦ
  qㄆ wㄊ eㄍ rㄐ tㄔ yㄗ uㄧ iㄛ oㄟ pㄣ
  aㄇ sㄋ dㄎ fㄑ gㄕ hㄘ jㄨ kㄜ lㄠ ;ㄤ
  zㄈ xㄌ cㄏ vㄒ bㄖ nㄙ mㄩ ,ㄝ .ㄡ /ㄥ
  ```

# Notebook 格式

- 講義直接呈現整理後的知識，而不需要糾正 prompt 因為 prompt 寫太快本來就很容易錯。任何需要釐清 prompter 的用詞或觀念時，在 chat 中說明，不寫進講義。例如直接介紹螢光讀取，不加上「不宜直接稱為『化學放光』」之類的話。
- 中文排版請依照 [中文文案排版指北（GitHub README）](https://github.com/sparanoid/chinese-copywriting-guidelines/blob/master/README.md)。
- 中文的並列項目，要用頓號就全部用頓號（`BEC、BSC、AWGN`），要用連接詞就全部用連接詞（`BEC 或 BSC 或 AWGN`），不要混用。用逗號或分號隔開的並列項目也一樣，不要只在最後一項之前加連接詞（如 `，以及`、`；或`）。英文列舉「前面用逗號、最後一項前加 and 或 or」的文法不適用於中文，不論有沒有 Oxford comma 都不要套用：不寫 `BEC、BSC 或 AWGN`，也不寫 `BEC、BSC、或 AWGN`。
- 矩陣方向一律使用英文 `row` 與 `column`，不使用中文對應詞，以避免地域用法歧義。
- 數學符號與公式在中英文混排時也視為英文，適用相同的空格與標點規則：與中文字之間加空格，與全形標點之間不加空格。例如 `當 $p$ 很小時`、`若 $d = 4$，則能更正 1 個錯誤`、`距離（$d$）`。
- 建立或修改 `.ipynb` 講義時，每個 section title（包含各級 Markdown 標題 `#` 至 `######`）必須獨立放在一個 Markdown cell；內文、公式、表格、圖片、其他標題應放在其他 cells。
- 每個 cell 的內容不得有 leading empty line 或 trailing empty line；分段所需的空白行只保留在 cell 內容中間。
- cell 大概十行，這是為了 jk 翻 cell 的時候不要一次捲動太多
- 講義用到的照片與圖檔（板書照片、截圖等）放在以講義日期命名的資料夾（例如 `1012/`），檔名用簡短的英文名稱（小寫、以 `-` 連接），描述圖中畫了什麼，或補充、說明了什麼，例如 `0923/ball-leaves-hilltop-anytime.png`、`0930/two-paths-around-small-rectangle.png`。不要用 `image-1.png`、`IMG_1924.jpeg` 這類流水號，也不要加 `-board`、`-annotated` 這類只說明圖片形式的字尾。檔名會出現在講義原始碼、`git log`、`ls` 中，alt text 只有渲染後才看得到。改名時一併更新講義中的連結。照片保留拍攝時的完整解析度，不要另存縮小的複本。格式要能在 VS Code 與 GitHub 上直接顯示（JPEG、PNG、WebP）；iPhone 的 HEIC 先轉成同解析度的 JPEG 再放進資料夾。同一張照片在 repo 中只留一份。
- Markdown 內文按句子分行，讓每個句子在呈現時也另起一行；同一段落內使用行尾兩個空格加換行，不只在原始碼中換行。長句可依語意在子句之間分行，參照使用者既有排版。空行只用於真正換段，公式前後仍遵循下述 TeX 段落規則。
- Sage 程式碼的 cell 語言標記使用 `python`，以顯示語法配色；每個 code cell 的 `metadata.vscode.languageId` 與 notebook 的 `metadata.language_info.name` 都設為 `python`，不可設為 `sage`。執行核心仍使用 SageMath，保留 `metadata.kernelspec` 的 SageMath 設定。儲存後檢查所有 code cells，避免編輯器留下 `languageId: sage`。
  - **不要再把語法配色改成 sage。** 缺少 `metadata.vscode.languageId` 同樣算違規：VS Code 會退回 kernelspec 的 `"language": "sage"`，結果語法配色消失。因此每個 code cell（包含新增的 cell）都必須明確寫上 `"metadata": {"vscode": {"languageId": "python"}}`。
  - 不要修改 `metadata.kernelspec`（保留 `"language": "sage"`、`"name": "sagemath"`），也不要把 `language_info.name` 改成 `sage`。
  - 每次編輯 `.ipynb` 後都要跑一次檢查，確認所有 code cells 的 `languageId` 都是 `python`，缺漏或為 `sage` 就立即補正。
- LaTeX 原始碼要加上適當空格，讓公式容易閱讀：二元運算子與關係符號（如 `+`、`-`、`=`、`\in`、`\le`）兩側留空格，逗號後留空格。例如 `s_b(t) = A\cos(2\pi f_ct + \pi b),\qquad b \in \{0, 1\}`。上下標內例外，見下一條。
- 上標與下標（`_{...}`、`^{...}`）內的原始碼不加空格：TeX 排版上下標時本來就省略運算子、關係符號、逗號周圍的間距，原始碼也比照呈現效果。例如寫 `a_{n+1}`、`(z - a)^{n+1}`、`\sum_{n=0}^\infty`、`\oint_{|z-a|=r}`、`\sum_{n\ge1}`、`\lim_{z\to a}`，不寫 `a_{n + 1}`、`\sum_{n = 0}`、`\oint_{|z - a| = r}`、`\sum_{n \ge 1}`。`\ge`、`\to` 等控制序列前面不加空格；後面只在接字母時保留一個空格，因為 TeX 需要它來結束控制序列名稱（如 `\to a`、`\ge N`）；接數字或其他符號時不加（如 `\ge1`、`\to0`、`\to\infty`）。`\text{...}` 內的文字照常空格。上下標內也不加 `\,` 等間距指令，例如寫 `q^{\max(u-d+1,0)}`；但積分的微分符號前的 `\,` 照常保留，例如 `e^{-\int P\,dx}`；但上下標裡並列兩組條件時，用 `\ ` 隔開比較好讀，例如 `_{1\le i\le n,\ 0\le j\le n-k-1}`。上下標以外的部分仍依上一條加空格。
- 行內公式與前後文字的間距依上述混排規則處理；`$` 與公式內容之間不加空格。
- 函數的冪次寫在引數之後，此時引數加括號：`\sin(\pi t)^3`、`\cos(\theta)^2`，不寫成 `\sin^3(\pi t)`、`\cos^2\theta`。指數是對函數值取冪，不是函數名的一部分。
- 除此之外，函數引數**只在會被誤讀時**才加括號，不要一律加。後面緊接另一個因式或上標時加：`\cos(a) I`、`\sin(\pi t)^3`、`\ln(3/2)`、`\sin(x)\cos(x)`。後面是關係符、運算子、逗號、`\frac` 之類的群組邊界或行尾時不加，因為那些本來就分隔得很清楚：`\ln2 \approx 6.93`、`\frac{\ln2}{0.005}`、`$\sin x$`、`\sin y = 0`、`\ln|y|`。
- 算子與其作用對象之間、以及帶有上下標的因式之間，在原始碼留一個空格：`T_a y`、`D y`、`D T_a y`、`P(D) y`、`e^{-ia} z`、`\frac{a^2 D^2}{2!}`。純量並列不加空格，例如 `cy`、`iy'`、`Ce^{rt}`。函數值與其後因式之間同樣留空格：`\cos(a) I + \sin(a) D`，不寫成 `\cos a\,I + \sin a\,D`。
- 展示公式 `$$ ... $$` 前後的空行依 TeX 的段落語意處理：空行代表換段，不是單純增加視覺留白。公式延續前文時，前文與公式之間不加空行；後文延續同一段時，公式與後文之間也不加空行。上下都有空行會讓公式獨立成段，通常不合講述脈絡，因此不要慣例性地在兩側都加空行；只在語意確實換段時留空行。
- 對 LaTeX 空格的詳細用法有疑問時，參照既有 `.ipynb` 講義與使用者已調整的公式格式。但既有原始碼可能有使用者沒注意到的不一致，不能當作規範的依據，也不要從既有寫法反推出新慣例。新寫的內容依 AGENTS.md 的規則；發現既有寫法與規則衝突，或遇到規則沒涵蓋的情況時，在 chat 中向使用者提出（指出位置與兩種寫法），由使用者決定。
- 同時存在三門課的講義 ~/Correct2026, ~/Complex2026, ~/Differ2026，請互相參考，尤其是互相參考對方的 AGENTS.md
- 英文標題大小寫依層級統一：`# GOOD JOB`（全大寫）、`## Good Job`（Title Case）、`### Good job`（Sentence case，以下層級亦同）。Title Case 的冠詞、連接詞、介系詞通常小寫，標題開頭、結尾、冒號後開頭除外；Sentence case 保留專有名詞與縮寫的慣用大小寫。數學公式、程式碼、連結網址保持原樣。
- LaTeX 數字的千分位分隔符號使用 `{,}`，括號內不加空格，例如 `201{,}000`；一般列舉項目或參數之間的逗號仍依原規則在逗號後留空格。
- 定義 LaTeX 巨集時使用 `\def`，不使用 `\newcommand` 或 `\renewcommand`，例如 `\def\FF{\mathbb F}`。
- 新建 `.ipynb` 講義時，先加入兩個佔位的作業 section，依序為 `## Homework Due <Today+4>` 與 `## Homework Due <Today+7>`（這門課星期三上課，即 `## Homework Due Sunday` 與 `## Homework Due Wednesday`），之後再補上實際題目內容。

# Kahoot 題型

- 使用者的 Kahoot 帳號為付費版，可用題型為：Quiz（含複選，可標記多個正確答案）、True or false、Type answer（自由輸入文字）、Slider（數值範圍作答）、Pin answer（在圖片上標記位置）、Puzzle（排序）。
- 草擬 Kahoot 題目時依內容挑選合適題型，而不要預設只有傳統四選一：分類題（order／linear 或 nonlinear／homogeneous 等獨立屬性）適合用 Quiz 複選，每個屬性各自標記對錯；數值題（例如「約 6.93 小時」「約 138.63 個月」）適合用 Slider；步驟排序類適合用 Puzzle。
