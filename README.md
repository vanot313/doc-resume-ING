## 简介

该简历模板使用 `\XeLaTeX` 编译，无痛支持中文，开箱即用(几乎不需要懂 `\LaTeX` 语法)，除了本地编译外也可使用 Overleaf **在线编译**，无需在本机安装 TeX 发行版。

主要的功能如下：

- 极其容易定制和扩展。
- 完善的 Unicode 字体支持，因为用的是 XeLaTeX 嘛
- 完美的简体中文支持，默认使用 adobefonts 的四套简体中文字型，其他字型可自行添加。
- 支持图标字体 FontAwesome 4.6.3

## 使用方法

### Overleaf 在线编译

感谢万能的『云计算』，`\LaTeX` 编译也可以放到云端了！使用这种方法无需在本机安装诸如 `CTeX/TeXlive/MacTeX` 等发行版，网站上还能有历史版本记录，十分方便！最简单的方法，浏览器中打开 [模板链接](https://www.overleaf.com/latex/templates/bill-ryans-elegant-latex-resume/xcqmhktmzmsw), 按需更改自己的名字和联系方式等。
在线预览时需要注意 Overleaf 自带的 PDF 阅读器对中文支持不太好(可能会显示乱码)，这时在编辑界面的左侧菜单选择使用 native 阅读器即可。

中文模板的文件为 `resume-zh_CN.tex`, 英文模板的文件为 `resume.tex`, 带照片的模板文件为 `resume_photo.tex`.

### latexonline.cc

使用 [LaTeX.Online](https://latexonline.cc/) 在线编译

### 使用较新的 TeX 发行版在本地计算机编译

除了在线编译外，该模板当然也支持传统的本地编译，从 <https://github.com/billryan/resume/tree/zh_CN> 上克隆下来使用 XeLaTeX 编译即可。

```tex
xelatex resume.tex % 编译英文简历
xelatex resume_photo.tex % 编译带照片的简历
xelatex resume-zh_CN.tex % 编译中文简历
```

### 中英文双语支持

\LaTeX 的中文支持一直是不少 TeX 新手心中的梦魇，该简历模板最大的特色就是『无痛』支持中英文双语，『无痛』的含义是指开箱即用——在线或者克隆到本地后只需要更改自己的信息即可，不需要自己设置中文字体支持等操作。

对 git 不了解或使用不方便的朋友可单独下载压缩包，解压即用。下载地址见 [GitHub 官网](https://github.com/billryan/resume/archive/zh_CN.zip), [大陆镜像加速](https://gods.coding.net/p/resume/git)

对 git 比较了解的朋友可选择克隆后切换到`zh_CN`分支，`zh_CN` 是`master`分支的超集，即`zh_CN`包含`master`分支所有的文件。
需要注意的是`zh_CN`分支包含 Adobe 的宋楷黑仿四套中文字体，体积较大(40 MB+)，如果只需要英文简历的可单独克隆`master`分支。

中文使用UTF-8编码，对于大多数 Windows 用户来说，只要使用的不是太老的 CTeX 发行版，WinEdt 的中文支持也是毫无压力的。
编译时务必使用 \XeLaTeX，其他编译方式会报错，因为依赖了 \XeTeX 的一些东西。

### 中英文切换

英文模板范例见 <https://github.com/billryan/resume/blob/zh_CN/resume.tex> 
中文模板范例见 <https://github.com/billryan/resume/blob/zh_CN/resume-zh_CN.tex>

中文模板与英文模板的区别仅有两行——使用中文时仅需反注释以下两行，模板中已默认启用，第一次编译时耗时相对较长(引入了外部中文字型)，耐心等待下。

```tex
\usepackage{zh_CN-Adobefonts_external} % Simplified Chinese Support using external fonts (./fonts/zh_CN-Adobe/)
%\usepackage{zh_CN-Adobefonts_internal} % Simplified Chinese Support using system fonts
\usepackage{linespacing_fix} % disable extra space before next section
```

对于高级用户：如果系统已确定安装有 Adobe 的四套中文字型，在文档的开始处使用包`zh_CN-Adobefonts_internal`，这样第一次编译时也会很快。

### 参考文献

参考文献的引用采用 bib + bst 的方式管理，bib 中存放 BibTeX 格式的引用文本，bst 用于控制 bib 文件的展示形式，默认为 IEEEtran. 编译方式可选如下：

1. OSX/Linux 用户 `latexmk -pdf -pvc -silent myresume-zh_CN.tex` latexmkrc 配置文件可参考我的 [dotfiles/latexmkrc](https://github.com/billryan/dotfiles/blob/master/latex/latexmkrc)
2. Windows 用户可使用 WinEdt 中的 TeXify 选项编译(未测试)

除了以上两种编译方式，你还可以使用传统的编译方式：

```shell
xelatex myresume-zh_CN
bibtex myresume-zh_CN
xelatex myresume-zh_CN
xelatex myresume-zh_CN
```

范例文档中默认Reference 另起一页，想留在当前页的可注释掉`\newpage`

### 宏

普通用户直接使用模板中的宏即可，具体排版使用可直接参考范例 tex 文档，已经十分简洁了。
想自己添加新的宏的可以先看看 [How to write a LaTeX class file and design your own CV (Part 1) - ShareLaTeX](https://www.sharelatex.com/blog/2011/03/27/how-to-write-a-latex-class-file-and-design-your-own-cv.html) 和 [How to write a LaTeX class file and design your own CV (Part 2) - ShareLaTeX](https://www.sharelatex.com/blog/2013/06/28/how-to-write-a-latex-class-file-and-design-your-own-cv.html) 了解下该模板的简单背景。

- `\name`: 姓名
- `\email`: 邮箱
- `\linkedin`: LinkedIn
- `\basicInfo`: 联系信息, 按需加入
- `\section`: 用于分节, 如教育背景, 实习/项目经历等
- `\subsection`: 用于小节标题, 无日期选项
- `\datedsubsection`: 用于小节标题, 简历中使用最广，第二项为时间区间，自动右对齐
- `\itemize`: 清单列表，简历中应用最广
- `\enumerate`: 枚举列表，数字标号

### FontAwesome

首先在 [Font Awesome Icons](http://fortawesome.github.io/Font-Awesome/icons/) 上选中自己想使用的图标，然后在 [fontawesome.sty](https://github.com/billryan/resume/blob/zh_CN/fontawesome.sty) 中找到相应的宏, 将其作为普通文本一样使用。
如果不需要使用 FontAwesome 字体的把那些宏去掉即可。
其他的可以自行参考相应 cls 和 tex 文件。

### 实践参考

这里列举一下其他同学基于本模板的具体**实践心得**, 大家可以自行参考, 也欢迎<u>提交贡献</u>, 分享你的心得:

- [用 Tex 书写优雅的简历 – Jin’s Blog](https://www.imbajin.com/2018-01-20-%E4%BD%BF%E7%94%A8Tex%E4%B9%A6%E5%86%99%E4%BC%98%E9%9B%85%E7%9A%84%E7%AE%80%E5%8E%86/) (简单介绍tex + 常见样式调整)

