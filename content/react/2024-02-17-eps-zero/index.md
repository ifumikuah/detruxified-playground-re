+++
title = "React Instalasi"
draft = false
weight = 1
tags = ['javascript', 'react']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "fig2"
src = "fig2.png"
title = ""
+++

## Prerequisites

- [Node.js](https://nodejs.org/en)
- NPM
- NPX

Dengan menginstall [Node.js](https://nodejs.org/en) kamu sudah memenuhi semua persyaratan

{{< expand "Sedikit memberi saran..." >}}
### Testing versi npm dan npx
1. Buka terminal
2. Coba jalankan satu-satu
```plain
> npm -v
> npx -v
```
### Mengetest npx
```plain
> npx cowsay sayhello -d
```
Jika gagal:
1. <kbd>Win</kbd>+<kbd>R</kbd>, Buka `%appdata%`
2. Buat folder baru disitu, namanya `npm`
3. Coba lagi
{{< /expand >}}

## Memulai project baru dengan react

Buat sebuah folder untuk projectmu, di series ini kita memberi nama folder tersebut `react-cleanconfig`:

```plain
> mkdir react-cleanconfig
```

Ke folder tersebut, lalu buka vscode atau apalah code editor kesukaanmu di folder tersebut:

{{< img name=fig1 size=tiny lazy=true >}}

Kamu juga harus membuka terminal di dalam folder project tersebut atau buka terminal yang ada di dalam vscodenya.

### Menginstall react nya

Sekali lagi pastikan *working directory* terminalmu ada di dalam folder proyek.

```plain
PS C:\Users\Owner\Documents\BELAJAR_REACTJS\react-cleanconfig>
```

Install `create-react-app`:

```plain
PS C:\Users\Owner\Documents\BELAJAR_REACTJS\react-cleanconfig> npx create-react-app .
```

Dan tunggu...

## Perkenalan awal lingkungan react kamu

Jika sudah selesai, dipaling bawah terminal kamu dapat ucapan selamat *Happy Hacking*.

Akan ada file-file default *boilerplate*:

- `package.json`: Semua konfigurasi yang ada di project. **Jangan dihapus!!**, karena ini ibaratnya DNA dari project yang mencatat apa saja dependency / package yang diperlukan.

- `src`: Directory sumber/source project, kamu akan sepenuhnya bekerja didalam folder ini.

- `public`: Directory public, broswer akan membaca `index.html` didalam folder ini.

## Preview

Untuk memulai development, mulai live development dengan command:

```js
> npm start
```

Browser akan terbuka otomatis di alamat yang tertera, kamu akan melihat preview default logo react berputar saat pertama kali.

{{< img name=fig2 size=small lazy=true >}}