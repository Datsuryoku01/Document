# echo コマンド

## echo の出力をファイルに入力
```bash
$ echo abc > abc.txt
$ echo def > def.txt
```
## ファイル連結結果をファイルにリダイレクトして保存
```bash
$ cat abc.txt def.txt > abcdef.txt

$ cat abcdef.txt
#abc
#def
```
## 確認用のファイルを作る
```bash
$ echo a > a.txt
$ echo c > c.txt
```
## a.txt, b\n:, c.txt を連結して abc.txt に出力
```bash
$ cat a.txt - c.txt > abc.txt
#b
```

## 確認
```bash
$ cat abc.txt
#a
#b
#c
```

## ファイルに echo 内容を出力
標準出力ではなくファイルに内容を出力するにはリダイレクトします。

>: ファイルに echo 内容で作成・上書き
    > で echo 内容を使ってファイル内容を上書きしたり、ファイルが存在しなければ作成したりできます。ファイル内容は echo の内容そのままになります。
```bash
$ echo 'abc' > a.txt
$ cat a.txt
#abc
```
>>: ファイルに echo 内容を追記する
    >> でリダイレクトすると、ファイルに echo 内容を追記します。既存のファイルデータの末尾に echo 内容が追記されます。
```bash
    $ echo 'abc' > a.txt
    $ echo 'def' >> a.txt
    $ cat a.txt
    abc
    def
```
---
```bash
$ echo '1\t2\t3'
#1\t2\t3
```
-e 指定時に使えるようになるデータ  
-e オプションを指定した時に使えるようになる制御文字やデータは以下のようなものがあります。  
単純にテキストで出力されるような内容だけでなく特殊な効果が得られるようになるデータもあります。

    \\: バックスラッシュ
    \a: ベル文字(警告音?が鳴ります。)
    \b: バックスペース
    \c: この文字以降の出力がされなくなります。
    echo -e 'abc\cdef' は 'abc' しか出力されません。
    \e: \c との違いがよくわかりません。。。
    \f: form feed
    \n: 改行文字
    \r: キャリッジリターン
    \t: タブ
    \v: 垂直タブ

---
【参考】
echoコマンドはC言語で書かれています。echoコマンドは、テキストを標準出力に表示するコマンドです。　　
echoコマンドは、C言語で書かれたライブラリ関数を利用して、テキストを標準出力に表示します。　　
echoコマンドは、次のC言語のコードで書かれています。

```C
int main(int argc, char *argv[]) {
  for (int i = 1; i < argc; i++) {
    printf("%s ", argv[i]);
  }
  printf("\n");
  return 0;
}
```

このコードは、コマンドラインから渡された引数を順番に表示します。  
例えば、コマンドラインから「echo hello world」と入力した場合、このコードは「hello world」を標準出力に表示します。  
このコードは、コマンドラインから渡された引数を順番に表示します。  

>int main(int argc, char *argv[])は、C言語のメイン関数です。
argcは、コマンドラインから渡された引数の数を表します。argvは、コマンドラインから渡された引数を格納した配列です。  
for (int i = 1; i < argc; i++) {は、iがargc未満の間、繰り返すループです。
printf("%s ", argv[i]);は、引数argv[i]を標準出力に表示します。
printf("\n");は、改行を標準出力に表示します。
return 0;は、正常終了コードを0で返します。
例えば、コマンドラインから「echo hello world」と入力した場合、このコードは「hello world」を標準出力に表示します。

