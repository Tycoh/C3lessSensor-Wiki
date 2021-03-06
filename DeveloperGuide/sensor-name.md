# センサの命名法

センサの計算方法は、センサの種類ごとに異なります。そのため、センサの名前は、種類ごとに一意である必要があります。

本システムでは、以下の手順に則ってセンサを命名し、重複が発生し得ないようにしております。

## 言語

センサの命名は、原則英語で行います。
例外としてラテン語のみ利用を許可します。

日本語などのマルチバイト文字は、バグの原因となるため利用してはいけません。

## センサの名称の構造

センサの名称は、以下の構造を持ちます。各項目は単語のみで構成され、PascalCase(UpperCamelCase)で入力します。接尾辞以外はすべて必須です。

- 接頭辞
- 計測対象
- Sensor
- 計測範囲
- 接尾辞

### 接頭辞

センサの特徴を表す単語を選択します。

例：

- 貫通型:Transfixed

- クランプ型：Clamp

- 熱電対：TC

### 計測対象

計測対象のデータを表す単語を選択します。

例:
- 電流：Current
- 温度：Temperature

### Sensor

センサ以外のデータの入力がある場合に備えての予約語。現状いずれのセンサでも必ず"Sensor"と入力します。

## 計測範囲

計測範囲が設定されている場合は、計測範囲とその単位`(下限値)-(上限値)(単位)`の順に入力します。ここで、単位はSI単位のみとします。

例：
- 計測範囲が1A-5A
  - 1-5A
- 計測範囲が0.1A-2A
  - 0.1-2A

桁数が多い場合はSI接頭辞のうち1000<sup>n</sup>乗倍数のもののみ利用できるものとします。ただし、文字数の合計が最小になるようにするものとします。

例：
- 計測範囲が0.0001Aから0.1A
  - 接頭辞なしのとき
    - 0.0001-0.1A(11文字)
  - 接頭辞mを利用
    - 0.1-100mA(9文字)
  - したがって接頭辞mを利用したものを採用する
- 計測範囲が0.01Aから1Aのとき
  - 接頭辞なしのとき
    - 0.001-1A(8文字)
  - 接頭辞mを利用
    - 100-1000mA(10文字)
  - したがって接頭辞なしのものを採用する

### 接尾辞
センサのバージョンアップなどで計算式が変わる場合など、計測範囲までの項目が共通するものの、識別する必要がある場合、接尾辞を利用できるものとします。また、必要がない場合は接尾時はつけないものとします。

例：　バージョン2
ver2

## 例

1.  計測範囲が2Aから100Aの、クランプ型電流センサ

    - クランプ型の： Clamp
    - 電流: Current
    - センサ： Sensor
    - 計測範囲2-100A: 2-100A

    - したがって、
      - ClampCurrentSensor2-100A

2. 計測範囲が2Aから100Aの、クランプ型電流センサのversion2
   - クランプ型の： Clamp
   - 電流: Current
   - センサ： Sensor
   - 計測範囲2-100A: 2-100A
   - version2: ver2
   - したがって、
     - ClampCurrentSensor2-100A