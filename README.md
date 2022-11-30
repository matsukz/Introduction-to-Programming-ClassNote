# テスト用まとめ<br>

## セル関連

* セルの選択

    * セル`A1`選択するだけの基本構造<br>
        ```VBA:A1の選択
        Range("A1")
        ```

    * セル`A1からC3・D5`を選択する
        ```VBA:選択応用
        Range(A1:C3,D5)
        ```
        後述の文字入力や色変更にも使用できます。

* セル内の変更する

    * セル`A1`に文字を入力する
        ```VBA:A1に文字を入力
        Range("A1")=100
        Range("A1")="あほばかまぬけ"
        ```
    * セル`A1`の色を変更する
        ```VBA:セル色変更
        Range("A1").Interior.ColorIndex=色コード
        ```
    * セル`A1`の文字の色を変更する
        ```
        Range("A1").Font.ColorIndex=色コード
        ```
    色コードについて<br>
    |  赤   |  青   |  黄   |  緑   |
    | :---: | :---: | :---: | :---: |
    |   3   |   5   |   6   |  10   |

    * シート内セルの全クリア
    ```VBA:クリア
    Cells.delete
    ```
## シート関連
 **初期シート以外の選択は予めシートを追加しておく必要があります。**<br>
 **マクロが実行されるのは現在表示されるシート上となります。**<br>
* シートの選択（移動）
    * `sheet2`へ移動する。
        ```
        Worksheets("sheet2").select
        ```
    * `sheet2`のセル`A1`を選択する
        ```
        Worksheets("sheet2").Range("A1")
        ```
        上記の色変更などが利用できます。

## 計算
* 基本
    * セル`A1`に計算結果を表示する
        ```VBA:四則計算
        Range("A1")=1+2
        Range("A1")=3-4
        Range("A1")=5*6
        Range("A1")=7/8
        ```
    * セル`A1`に`B2`と`C4`の計算結果を表示する
        ```
        Range("A1")=Range("B2")+Range("C4")
        ```
        セル同士計算でも四則計算同様の演算子を利用します。
    * その他の演算子
        | 商（整数部） | 商（余り） | べき乗 |
        | :------------: | :----------: | :------: |
        | /            | Mod        | ^      |
* シートをまたいだ計算
    * 現在のシート`Sheet1`の`A1`に`B1`と`Sheet2`の`C1`を計算した結果を表示する
        ```VBA:シート演算
        Range("A1")=Range("B1")+Worksheets("sheet2").Range("C1")
        ```
## その他便利機能
* オートフィル
    1. 数値のオートフィル<br>
    **連続したセルに数値が入力されている必要があります。**
    * `A1`に100、`A2`に200と手で入力しから`A10`まで100・・200・・300と連続した数値を表示する。
    ```VBA:数値オートフィル
    Range("A1:A2").Autofill Destination:=Range("A1:A10")
    ```
