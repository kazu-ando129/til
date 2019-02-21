# wkhtmltopdf

- 概要
htmlをpdfに変換するツール

- インストール手順（wkhtmltopdf本体）
```
$ cat /etc/os-release
$ wget https://downloads.wkhtmltopdf.org/0.12/0.12.5/wkhtmltox_0.12.5-1.xenial_amd64.deb
$ sudo apt-get install -f
$ sudo dpkg -i wkhtmltox_0.12.5-1.xenial_amd64.deb
$ wkhtmltopdf -V
```

- インストール手順（日本語フォント）
```
$ wget http://dl.ipafont.ipa.go.jp/IPAexfont/IPAexfont00301.zip
$ unzip IPAexfont00301.zip
$ sudo mv IPAexfont00301 /usr/share/fonts/
```

- 参考
  - インストール手順（wkhtmltopdf本体）にて、wgetするdebは[donwload](https://wkhtmltopdf.org/downloads.html)から取得する

- 使い方
```
$ wkhtmltopdf https://google.co.jp hoge.pdf
```