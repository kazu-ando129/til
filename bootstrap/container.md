# .containerとcontainer-fluidの違い

- 環境
  - Bootstrap v4.0.0

- 内容
  - .containerはディスプレイサイズによって、幅が変更される
    - ソースコード参照
  - .container-fluidはディスプレイに関係なく、ディスプレイいっぱいに

- ソースコード
```bootstrap.css
.container {
  width: 100%;
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
}

@media (min-width: 576px) {
  .container {
    max-width: 540px;
  }
}

@media (min-width: 768px) {
  .container {
    max-width: 720px;
  }
}

@media (min-width: 992px) {
  .container {
    max-width: 960px;
  }
}

@media (min-width: 1200px) {
  .container {
    max-width: 1140px;
  }
}

.container-fluid {
  width: 100%;
  padding-right: 15px;
  padding-left: 15px;
  margin-right: auto;
  margin-left: auto;
}
```