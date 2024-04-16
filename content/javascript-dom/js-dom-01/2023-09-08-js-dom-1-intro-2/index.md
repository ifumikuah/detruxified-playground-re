+++
title = "Intro: Document Object Model"
draft = false
weight = 2
tags = ['javascript','html']

[[resources]]
name = "dom-tree"
src = "dom-tree.gif"
title = "Document Object Tree"
+++

## Document Object Model

**D**ocument **O**bject **M**odel adalah sebuah standard yang digunakan untuk memperbolehkan program seperti JS merubah struktur dokumen HTML.

Standard ini digambarkan sebagai struktur atau *tree* model.

{{< img name=dom-tree size=medium >}}

## Hierarchy

Terdapat dua "kasta" dalam struktur DOM:

- Element node, element dalam HTML pada umumnya seperti, `<ul>`,`<ol>`,`<li>`,`<h1>`,`<body>`, dsb.
- Text node, text/isi yang ada di dalam element tersebut.

Umumnya JS berinteraksi melalui Element node agar bisa memanipulasi Text node didalamnya.

## Apa yang bisa dilakukan dengan DOM

- Memanipulasi semua element yang ada di halaman HTML.
- Memanipulasi semua style CSS di halaman HTML yang sama.
- Menambah interaktif halaman HTML dengan event listener.