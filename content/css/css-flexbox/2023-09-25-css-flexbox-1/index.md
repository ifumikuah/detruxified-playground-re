+++
title = "CSS Flexbox I"
draft = false
weight = 1
tags = ['css']

[[resources]]
name = "flexbox_1"
src = "flexbox-1.png"
title = ""

[[resources]]
name = "flexbox_2"
src = "flexbox-2.png"
title = ""
+++

Flexbox adalah sistem layout satu dimensi di CSS, ini merupakan cara terbaik jika ingin membuat distribusi kotak-kotak yang rapi.

{{< img name="flexbox_1" size="medium" >}}

Main axis atau row adalah sumbu utama dari flexbox, sedangkan cross axis atau column merupakan sumbu lawan dari flexbox.

## Membuat Flexbox

Untuk membuat flexbox, kamu memerlukan sebuah container dan beberapa item didalamnya.

{{< img name="flexbox_2" size="medium" >}}

```html
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div>3</div>  
</div>
```
```css
.flex-container {
  display: flex;
  background-color: DodgerBlue;
}

.flex-container > div {
  background-color: #f1f1f1;
  margin: 10px;
  padding: 20px;
  font-size: 30px;
}
```