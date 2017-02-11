Raspberry Pi で Arduino のスケッチを書き込む
---

* [Arduino Uno R3互換ボード](http://item.rakuten.co.jp/marutsuelec/605620/)
* Raspberry Pi Model B+

# Raspbian の設定

## arduino

```
# apt-get install arduino
```

## python-pip

```
# apt-get install python-pip -y
```

## platformio

```
# pip install platformio
```

# プロジェクトを作成します

```
$ mkdir arduino-led
$ cd arduino-led
$ platformio init --board=uno
```

platformio.ini の最後に次の記述を追記します

```
upload_port=/dev/ttyACM0
```

# ソースコードを記述します

```
#define LED_PIN (13)
void setup() {
	pinMode(LED_PIN, OUTPUT);
}
void loop() {
	digitalWrite(LED_PIN, HIGH);
	delay(5000);
	digitalWrite(LED_PIN, LOW);
	delay(5000);
}
```

# ビルドと実行

```
platformio run --target=upload
```
