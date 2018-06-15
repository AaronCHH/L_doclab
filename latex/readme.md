# LaTeX 教學

摘自 [新手安裝LaTeX懶人教學(Step by step)
](http://leavedcorn.pixnet.net/blog/post/24773932-%E6%96%B0%E6%89%8B%E5%AE%89%E8%A3%9Dlatex%E6%87%B6%E4%BA%BA%E6%95%99%E5%AD%B8%28step-by-step%29)

<!-- TOC -->

- [LaTeX 教學](#latex-教學)
  - [安裝 LaTeX 包含以下兩部分](#安裝-latex-包含以下兩部分)
    - [(a) 選擇「系統套件」(包含編譯器)](#a-選擇系統套件包含編譯器)
    - [(b) 選擇「編輯器」（講白話點就是打文章的介面啦！）](#b-選擇編輯器講白話點就是打文章的介面啦)
  - [有了基本認知之後，以下是正文](#有了基本認知之後以下是正文)
    - [一、安裝 MiKTeX 2.8](#一安裝-miktex-28)
    - [二、更新 MiKTeX](#二更新-miktex)
    - [三、為 MiKTeX 安裝 xeCJK (optional)](#三為-miktex-安裝-xecjk-optional)
    - [四、安裝 Texmaker](#四安裝-texmaker)
    - [五、設定 Texmaker](#五設定-texmaker)
    - [六、簡單範例](#六簡單範例)

<!-- /TOC -->

## 安裝 LaTeX 包含以下兩部分

### (a) 選擇「系統套件」(包含編譯器)

常用的免費windows版本套件有這兩種

MiKTex http://www.miktex.org/

fpTeX http://www.fptex.org

這篇文章要安裝的是前者，搭配 xeCJK 可以處理 UTF-8 的中文

(原本的 CJK 只能處理 Big-5 的中文)

### (b) 選擇「編輯器」（講白話點就是打文章的介面啦！）

 
## 有了基本認知之後，以下是正文

### 一、安裝 MiKTeX 2.8

http://miktex.org/2.8/setup

### 二、更新 MiKTeX

裝完 MiKTeX 2.8 之後到開始→程式集→MiKTeX 2.8→Maintenance (Admin)→Update (Admin)

預設會選 I want to get updated packages from a remote package repository

不用更改，下一步

接著會預設勾選所有有更新的套件，也是按下一步

然後去泡個咖啡等他完成吧
 

### 三、為 MiKTeX 安裝 xeCJK (optional)

開始→程式集→MiKTeX 2.8→Maintenance (Admin)→Package Manager (Admin)

你會看到很多套件，可以挑有關 xeCJK 的全部安裝

但初學者也可以略過此步

反正到時候編譯中文文件，系統也會自動問你要不要裝 xeCJK

  

到目前為止其實已經可以自己試著建立中文 PDF 文件了

只要用 MiKTeX 內建的編輯器 TeXworks 即可

它的優點是視窗左邊放原始碼，快速編譯之後，右邊馬上會出現 PDF 文件預覽

缺點是預覽的 pdf 若是有中文，字會破破碎碎的
 
下面開始則是介紹另一個編輯器：Texmaker 


### 四、安裝 Texmaker

LaTeX 原本並不是一個所見即所得的文件編輯語言

這是另一個對初學者的門檻

也就是說，不像 M$ 的 word 打什麼就出現什麼，令很多人望之卻步

雖然已經有很多編輯器提供方便的介面可以使用，但大多不支援 UTF-8 中文 

在這裡推薦安裝另一個 Texmaker，支援 UTF-8 中文

開啟PDF則是使用外部程式預覽，所以不會有中文破字問題

可以自行 google Texmaker 或者到以下網址下載

http://www.xm1math.net/texmaker/texmakerwin32_install.exe
 

### 五、設定 Texmaker

選項→設定 Texmaker

會看到左邊有三個部分：__「指令」、「快速編譯」、「編輯器」__

(a)

指令→第一項 LaTeX 加入「xe」，變成

__「xelatex -interaction=nonstopmode %.tex」- (1)__

PDF 檢視器裡面打你用來看 PDF 的程式，像我的是

__「"C:/Program Files/Foxit Software/Foxit Reader/Foxit Reader.exe" %.pdf」- (2)__

(b)

__快速編譯→快速編譯組合選「自訂」__

把剛剛的 (1)+(2) 打進去，記得中間用「|」分開

結尾再補上「|bibtex %.aux|xdvi %.dvi」(雖然初學可能用不到)

(c)

__編輯器→編輯器字型編碼選 「UTF-8」__

 

### 六、簡單範例

以下範例取自 LaTeX 板友 iampincky 的文章
直接複製貼上到編輯器，按F1就可以快速編譯，然後看產生的 PDF 檔囉

(記得檔案要存成 UTF-8 格式)

```latex
\documentclass{article}

\usepackage{fontspec}                 %加這個就可以設定字體
\usepackage{xeCJK}                    %讓中英文字體分開設置
\setCJKmainfont{標楷體}               %設定中文為系統上的字型，而英文不去更動，使用原TeX字型
\XeTeXlinebreaklocale "zh"            %這兩行一定要加，中文才能自動換行
\XeTeXlinebreakskip = 0pt plus 1pt    %這兩行一定要加，中文才能自動換行
\title{我是標題標題標題}
\author{我是作者}
\date{} %不要日期

\begin{document}
\maketitle

中文測試中文測試中文測試中文測試中文測試中文測試，中文測試中文測試，中文
測試中文測試中文測試中文測試中文測試中文測試，中文測試中文測試。中英文可以連打。

English Test. 插入中文字，看看如何？ This is a simple template for a
XeLaTeX document using the article class, with the fontspec package to
easily select fonts.
\end{document}
```