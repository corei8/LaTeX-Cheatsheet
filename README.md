# LaTeX-Cheatsheet

Collection of links, articles, tricks and snippets for making LaTeX documents.

## Contents

1. [Snippets](#snippets)
2. [Tricks](#tricks)
3. [GregorioTeX](#gregorio)

## Posts/Articles

- [Set Initial Fonts](https://tex.stackexchange.com/a/250479/254874)
- [Scale the Document](https://tex.stackexchange.com/a/70240/254874)
- [Samples of Custom Chapters](http://zoonek.free.fr/LaTeX/LaTeX_samples_chapter/0.html)

## [Snippets](#snippets)

#### Scale the Document's Fonts

```LaTeX
\usepackage{relscale}
\relscale{0.95} % or whatever scaling is desired
```

#### Set font for initials

```LaTeX
\usepackage{Carrickc,lettrine}
\renewcommand\LettrineFontHook{\Carrickcfamily}
```
![Options for Fancy Dropcaps](./images/initials.jpg)

#### Linebreaks with Tikz Trees

```LaTeX
\begin{tikzpicture}
    \tikzset{every tree node/.style={align=center}}
    {
	\Tree [.{\textit{de fide...}} 
		[.{\textit{creden\ae\ }} 
		[.{``divine faith''\\ Authority of God} ]
	]
		[.{\textit{tenend\ae\ }} 
			[.{``ecclesiastical faith''\\ Authority of the Church} 
				[.{mediately divine} ]
				[.{virtually revealed} ]
			]
		]
	]
	}
\end{tikzpicture}
```
![Tikz Tree Line Breaks](./images/line_breaks_trees.png)

#### Add a DRAFT watermark

```latex
\usepackage{draftwatermark} % automatically puts it on every page
\SetWatermarkLightness{.92} % the higher the number, the lighter the mark
\SetWatermarkScale{1.3}     % increases the default font size
```

## [Tricks](#tricks)

#### Symmetrical dots using `\dotfill`.

Add before `\begin{document}`:

```LaTeX
\makeatletter
\renewcommand \dotfill {\leavevmode \leaders \hb@xt@ .44em{\hss .\hss }\hfill \kern \z@}
\makeatother
```
## [GregorioTeX](#gregorio)

#### Initial settings for 10pt

```LaTeX
\grechangestyle{annotation}{\fontsize{8}{8}\selectfont}
\grechangestyle{initial}{\fontsize{35}{35}\selectfont}
```

#### Settings for large change, in the style of a _Pontificale_

```latex
% !TEX program = lualatex
% !TEX encoding = UTF-8

\documentclass[20pt, extrafontsizes]{memoir}
\usepackage[letterpaper,vmargin={1in,1in},hmargin={1in,1in}]{geometry}
\usepackage{fullpage}
\usepackage{microtype}
\usepackage{fontspec}
\usepackage{gregoriotex}
\gresetlinecolor{gregoriocolor}
\grechangestaffsize{27}
\gresetlinesbehindpunctumcavum{visible}
\grechangestafflinethickness{50}
\grechangedim{spacelinestext}{2.7ex}{fixed}
\grechangedim{spaceabovelines}{1.9ex}{scalable}
\gresetgregoriofont[op]{greciliae}
\usepackage[latin]{babel}
\defaultfontfeatures{Ligatures=TeX}
\setmainfont{Libertinus Serif}
\usepackage{Carrickc,lettrine}
\renewcommand\LettrineFontHook{\Carrickcfamily}
\pagestyle{empty}
\begin{document}
\setlength{\parindent}{0pt}
\gresetbracerendering{font} 
%% YOUR CHANT HERE
\end{document}
```
