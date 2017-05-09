---
layout: default
---

# LATEX中使用Alpha引用方式
2017.05.09

使用的是TexStudio 2.12.2版本。

### 正文

```
\documentclass{article}
\begin{document}
Daeman and Rijmen proposed AES, which is a very famous block cipher. Lightweight block ciphers are designed with the development of IOT (Internet of Things), such as PRESENT \cite{bogdanov2007present}, RECTANGLE \cite{zhang2015rectangle}, SIMON \cite{beaulieu2015simon} and so on. 
\bibliographystyle{alpha}%% this is the type
\bibliography{cipher}%% cipher is the name of the .blb file.
\end{document}
```

### 效果

![alpha-ref-in-latex](./../images/alpha-ref-in-latex.png?raw=true)
