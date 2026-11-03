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
- 講義中的英文散文請依照 AMS Style Guide（AMSSG）的規範書寫，不只限於引號規則。例如採用邏輯引號（logical quotation）：句尾標點（句號、逗號等）若不屬於被引用的文字本身，應放在右引號之外，如 `the term "bounded"` 而非 `"bounded."`；只有標點本身就是引文的一部分時才放在引號內。
- 建立或修改 `.ipynb` 講義時，每個 section title（包含各級 Markdown 標題 `#` 至 `######`）必須獨立放在一個 Markdown cell；內文、公式、表格、圖片、其他標題應放在其他 cells。
- 每個 cell 的內容不得有 leading empty line 或 trailing empty line；分段所需的空白行只保留在 cell 內容中間。編輯後跑 `python3 strip_blank_lines.py` 清掉（參數與 `fix_languageid.py` 相同，`--check` 只檢查）；VS Code 拆 cell 時常留下這種空行。
- Markdown cell 大概五行，這是為了 jk 翻 cell 的時候不要一次捲動太多。Code cell 不在課堂上講解，長度不限：依功能與語意切分（例如一組資料、一個函式與它的用法、一張圖、一組檢查各一格），不要為了行數切開。
- 講義用到的照片與圖檔（板書照片、截圖等）放在以講義日期命名的資料夾（例如 `1012/`），檔名用簡短的英文名稱（小寫、以 `-` 連接），描述圖中畫了什麼，或補充、說明了什麼，例如 `0923/ball-leaves-hilltop-anytime.png`、`0930/two-paths-around-small-rectangle.png`。不要用 `image-1.png`、`IMG_1924.jpeg` 這類流水號，也不要加 `-board`、`-annotated` 這類只說明圖片形式的字尾。檔名會出現在講義原始碼、`git log`、`ls` 中，alt text 只有渲染後才看得到。改名時一併更新講義中的連結。照片保留拍攝時的完整解析度，不要另存縮小的複本。格式要能在 VS Code 與 GitHub 上直接顯示（JPEG、PNG、WebP）；iPhone 的 HEIC 先轉成同解析度的 JPEG 再放進資料夾。同一張照片在 repo 中只留一份。
- Markdown 內文按句子分行，讓每個句子在呈現時也另起一行；同一段落內使用行尾兩個空格加換行，不只在原始碼中換行。長句可依語意在子句之間分行，參照使用者既有排版。空行只用於真正換段，公式前後仍遵循下述 TeX 段落規則。
- Sage 程式碼的 cell 語言標記使用 `python`，以顯示語法配色；每個 code cell 的 `metadata.vscode.languageId` 與 notebook 的 `metadata.language_info.name` 都設為 `python`，不可設為 `sage`。執行核心仍使用 SageMath，保留 `metadata.kernelspec` 的 SageMath 設定。儲存後檢查所有 code cells，避免編輯器留下 `languageId: sage`。
  - **不要再把語法配色改成 sage。** 缺少 `metadata.vscode.languageId` 同樣算違規：VS Code 會退回 kernelspec 的 `"language": "sage"`，結果語法配色消失。因此每個 code cell（包含新增的 cell）都必須明確寫上 `"metadata": {"vscode": {"languageId": "python"}}`。
  - 不要修改 `metadata.kernelspec`（保留 `"language": "sage"`、`"name": "sagemath"`），也不要把 `language_info.name` 改成 `sage`。
  - 每次編輯 `.ipynb` 後都要跑 `python3 fix_languageid.py`（不加參數時處理資料夾內所有講義，也可以只指定檔名），它會把缺漏或為 `sage` 的 `languageId` 補成 `python`；只檢查、不修改時加 `--check`。VS Code 存檔時會拿掉 `languageId`，所以使用者在 VS Code 編輯過的講義，commit 前也要再跑一次。三門課用同一份 `fix_languageid.py`、`strip_blank_lines.py`、`display_widths.py`，修改時三份一起改。
- LaTeX 原始碼要加上適當空格，讓公式容易閱讀：二元運算子與關係符號（如 `+`、`-`、`=`、`\in`、`\le`）兩側留空格，逗號後留空格。例如 `s_b(t) = A\cos(2\pi f_ct + \pi b),\qquad b \in \{0, 1\}`。上下標內例外，見下一條。
- 上標與下標（`_{...}`、`^{...}`）內的原始碼不加空格：TeX 排版上下標時本來就省略運算子、關係符號、逗號周圍的間距，原始碼也比照呈現效果。例如寫 `a_{n+1}`、`(z - a)^{n+1}`、`\sum_{n=0}^\infty`、`\oint_{|z-a|=r}`、`\sum_{n\ge1}`、`\lim_{z\to a}`，不寫 `a_{n + 1}`、`\sum_{n = 0}`、`\oint_{|z - a| = r}`、`\sum_{n \ge 1}`。`\ge`、`\to` 等控制序列前面不加空格；後面只在接字母時保留一個空格，因為 TeX 需要它來結束控制序列名稱（如 `\to a`、`\ge N`）；接數字或其他符號時不加（如 `\ge1`、`\to0`、`\to\infty`）。`\text{...}` 內的文字照常空格。上下標內也不加 `\,` 等間距指令，例如寫 `q^{\max(u-d+1,0)}`。積分的微分符號前的 `\,` 不受這項規則限制，例如 `e^{-\int P\,dx}`。上下標裡並列兩組條件時，用 `\ ` 隔開比較好讀，例如 `_{1\le i\le n,\ 0\le j\le n-k-1}`。上下標以外的部分仍依上一條加空格。
- 行內公式與前後文字的間距依上述混排規則處理；`$` 與公式內容之間不加空格。
- 函數的冪次寫在引數之後，此時引數加括號：`\sin(\pi t)^3`、`\cos(\theta)^2`，不寫成 `\sin^3(\pi t)`、`\cos^2\theta`。指數是對函數值取冪，不是函數名的一部分。
- 除此之外，函數引數**只在會被誤讀時**才加括號，不要一律加。後面緊接另一個因式或上標時加：`\cos(a) I`、`\sin(\pi t)^3`、`\ln(3/2)`、`\sin(x)\cos(x)`。後面是關係符、運算子、逗號、`\frac` 之類的群組邊界或行尾時不加，因為那些本來就分隔得很清楚：`\ln2 \approx 6.93`、`\frac{\ln2}{0.005}`、`$\sin x$`、`\sin y = 0`、`\ln|y|`。
- 算子與其作用對象之間、以及帶有上下標的因式之間，在原始碼留一個空格：`T_a y`、`D y`、`D T_a y`、`P(D) y`、`e^{-ia} z`、`\frac{a^2 D^2}{2!}`。純量並列不加空格，例如 `cy`、`iy'`、`Ce^{rt}`。函數值與其後因式之間同樣留一個空格：`\cos(a) I + \sin(a) D`，不寫成 `\cos a\,I + \sin a\,D`。
- 展示公式 `$$ ... $$` 前後的空行依 TeX 的段落語意處理：空行代表換段，不是單純增加視覺留白。公式延續前文時，前文與公式之間不加空行；後文延續同一段時，公式與後文之間也不加空行。上下都有空行會讓公式獨立成段，通常不合講述脈絡，因此不要慣例性地在兩側都加空行；只在語意確實換段時留空行。
- 展示公式呈現時太長（例如一長串等號，或用 `\qquad` 並列好幾個式子），考慮改用 `$$ \begin{aligned} ... \end{aligned} $$` 分成幾列。一串等號在某個 `=` 前斷開，各列以 `&=` 對齊；並列的式子（例如 $u_1'$ 與 $u_2'$）各佔一列，同樣以 `&=` 對齊；左邊太長、使右邊放不下時，不要在右邊中間斷：讓左邊自成一列，之後每列以 `=` 開頭，寫成 `&\text{左邊} \\ &\quad = \text{右邊}_1 \\ &\quad = \text{右邊}_2`（對齊點放在每列開頭，左邊才不會把右邊推寬）；有自然的短名字時，也可以補一個短的左邊（例如 `y &= ...`、`P(m) &= ...`）。只有右邊本身就太長時，才在它的 `+`、`-` 前斷開，續行以 `&\quad +` 開頭。用 `aligned` 放在 `$$` 內，不用 `align`，三門課都這樣寫。`python3 display_widths.py` 用 pdflatex 量出每個展示公式的寬度，列出超過 25em 的（`--max` 改上限，`--all` 列出全部）；這是候選清單，要不要拆、在哪裡拆仍依語意判斷。使用者說某個展示公式太長時，先用 `display_widths.py --all` 量它的寬度；如果比目前的上限（腳本裡的 `DEFAULT_MAX_EM`）窄，就把上限降到它的寬度以下（取整數），並在 `DEFAULT_MAX_EM` 上方的註解記下這次的寬度，三份腳本一起改。
- 不要連續放兩個以上的展示公式（兩個 `$$ ... $$` 之間沒有文字）：每個 `$$` 是獨立的展示公式，各有上下留白，列距比多列公式大，也無法對齊。並列的式子合併成一個 `aligned`，以共同的關係符號（`=`、`\Longrightarrow`、`\rightleftharpoons` 等）對齊，`(n = 1)`、`\text{second order}` 這類標註放在 `&&` 之後；沒有共同對齊點時改用 `gathered`（同樣放在 `$$` 內，不用 `gather`）。後一式是由前一式推得的步驟時不合併，改在兩式之間加連接詞（如 so、and、hence）。
- 同一段落內要換行時（結尾加兩個空格的 Markdown 換行），依優先順序選擇斷點：句號後幾乎都要換行（`\allowbreak[4]` 的感覺）；分號後盡量換行（`\allowbreak[3]`），除非分號後的子句太短；冒號後與分號同級，也盡量換行，除非冒號後的內容太短，例如 `Superposition fails for nonhomogeneous equations:` 之後換行接 `if $L y_1 = g$ and ...`；非列舉用途的逗號（如 `Because A, so B` 這種連接子句而非列舉項目的逗號）也是很好的斷點，因為這類句子通常很長；行內公式 `$...$` 的開頭與結尾同樣是很好的斷點。這些標點只是提示；真正的判準是句子的語法結構（把句子看成 AST）：選最接近根的連接處斷。離根近的連接詞或介系詞（如 `with`、`and`、`so that`、`exactly when`、`which`）比深層子結構裡的逗號更好，例如 `we let $...$ with $...$ and $...$,` 在 `with` 前斷（`let` 更接近根，但在 `let` 前斷沒有意義）。主詞與述語之間是好斷點；句首的短片語（如 `For A1–A5,`）不要單獨成一行，跟後面的動詞留在同一行。同一層的斷點之間（例如列舉裡的逗號與 `and` 都是同一層的二元連接），選在最長的那一項前面斷，讓長項自成一行、短項留在一起，就像在最長的加項前斷開一個和：`For A1–A5, write $y_1$, $y_2$, $W$,` 換行接 `and the right-hand side $f$ of the standard form only.`，斷在 `and` 前不是因為 `and` 比逗號高，而是因為最後一項最長；不要在動詞與受詞之間、名詞與後面的 `of` 片語之間，或名詞與它的公式之間（如 `the standard form` 與 `$...$`）斷。例外：受詞本身是一個行內公式時，可以在公式前斷，例如 `The chain rule gives` 換行接 `$\frac{dy}{dt} = \frac{dx}{dt}\frac{dy}{dx} = x\frac{dy}{dx}$, so`；這種斷只在原始碼換行，`gives` 後面不加兩個空格，呈現時仍是同一行。不要讓很短的開頭（如 `The chain rule`、`This explains`）單獨成一行。行內公式本身太長時，同樣在它最上層的關係符號（通常是 `=`）前拆成兩段行內公式再換行，第二段以該符號開頭，例如 `Then $u_1 y_1 + u_2 y_2 + u_3 y_3$` 換行接 `$= \ln(\sec x) + 1 - \sin(x) \ln(\sec x + \tan x)$.`。
- Markdown 原始碼的每一行大約不超過 70 個字元：使用者自己斷的行中位數約 40 個字元，九成在 70 以內。行內公式很多時可以到 80 左右；一個短子句（例如 `which is $G(x, 0) f(0)\,dt$`）不要為了湊字數拆成兩行，使用者會把這種拆開的行接回去。超過時依上一條的斷點順序斷開。新寫或修改的段落一開始就照這個長度斷好，不要留下長行讓使用者手動斷；改完用 `len` 檢查一次。使用者自己斷過或接回的行照原樣保留，不要再改。只因為 LaTeX 原始碼很長才需要斷、呈現時並不長的行，用一般換行（行尾不加兩個空格），呈現時仍接在同一行；要在呈現時也換行的地方才加兩個空格。拿不準時寧可斷短，太短比太長好。
- 對 LaTeX 空格的詳細用法有疑問時，參照既有 `.ipynb` 講義與使用者已調整的公式格式。但既有原始碼可能有使用者沒注意到的不一致，不能當作規範的依據，也不要從既有寫法反推出新慣例。新寫的內容依 AGENTS.md 的規則；發現既有寫法與規則衝突，或遇到規則沒涵蓋的情況時，在 chat 中向使用者提出（指出位置與兩種寫法），由使用者決定。
- 同時存在三門課的講義 ~/Correct2026, ~/Complex2026, ~/Differ2026，請互相參考，尤其是互相參考對方的 AGENTS.md
  - 互相參考只限於格式與排版慣例。三門是不同的課，學生不一定同時修，所以每門課的講義都要自成一體：不要引用其他課的內容，也不要假設學生學過（例如 Differ2026 的 exact equation、closed form 或 winding number 作業）；需要的概念在本課講義中自行定義。本課較早的講義則可以沿用。
- 英文標題大小寫依層級統一：`# GOOD JOB`（全大寫）、`## Good Job`（Title Case）、`### Good job`（Sentence case，以下層級亦同）。Title Case 的冠詞、連接詞、介系詞通常小寫，標題開頭、結尾、冒號後開頭除外；Sentence case 保留專有名詞與縮寫的慣用大小寫。數學公式、程式碼、連結網址保持原樣。
- LaTeX 數字的千分位分隔符號使用 `{,}`，括號內不加空格，例如 `201{,}000`；一般列舉項目或參數之間的逗號仍依原規則在逗號後留空格。
- 定義 LaTeX 巨集時使用 `\def`，不使用 `\newcommand` 或 `\renewcommand`，例如 `\def\FF{\mathbb F}`。
- 新建 `.ipynb` 講義時，先加入兩個佔位的作業 section，依序為 `## Homework Due <Today+4>` 與 `## Homework Due <Today+7>`（這門課星期三上課，即 `## Homework Due Sunday` 與 `## Homework Due Wednesday`），之後再補上實際題目內容。

# Kahoot 題型

- 使用者的 Kahoot 帳號為付費版，可用題型為：Quiz（含複選，可標記多個正確答案）、True or false、Type answer（自由輸入文字）、Slider（數值範圍作答）、Pin answer（在圖片上標記位置）、Puzzle（排序）。
- 草擬 Kahoot 題目時依內容挑選合適題型，而不要預設只有傳統四選一：分類題（order／linear 或 nonlinear／homogeneous 等獨立屬性）適合用 Quiz 複選，每個屬性各自標記對錯；數值題（例如「約 6.93 小時」「約 138.63 個月」）適合用 Slider；步驟排序類適合用 Puzzle。
