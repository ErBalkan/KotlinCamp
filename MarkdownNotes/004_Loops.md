# Döngüler – for, while, do-while

## 📌 4.1 for Döngüsü
`💡 Ne işe yarar?`
Belirli sayıda işlem yapman gerektiğinde kullanılır. Mesela 1’den 10’a kadar sayıları yazdırmak.

`🔍 Örnek:`

````kotlin
fun main() {
    for (i in 1..10) {
        println(i)
    }
}
````

- i değişkeni 1’den 10’a kadar (dahil) artar.
- .. operatörü aralık anlamına gelir.

`Alternatif:`

````kotlin
for (i in 10 downTo 1) {  // 10'dan 1'e geriye sayar
    println(i)
}
````

## 📌 4.2 while Döngüsü
`💡 Ne işe yarar?`
Koşul sağlandığı sürece döngü devam eder.

`🔍 Örnek:`

````kotlin
fun main() {
    var i = 1
    while (i <= 5) {
        println(i)
        i++  // i'yi 1 artır
    }
}
````

## 📌 4.3 do-while Döngüsü
`💡 Ne işe yarar?`
En az bir kere çalışır, sonra koşulu kontrol eder.

`🔍 Örnek:`

````kotlin
fun main() {
    var i = 1
    do {
        println(i)
        i++
    } while (i <= 5)
}
````

## 📌 4.4 Döngüde Kontrol Komutları: break ve continue

| Komut      | Ne işe yarar?                             |
| ---------- | ----------------------------------------- |
| `break`    | Döngüyü tamamen sonlandırır               |
| `continue` | O anki döngüyü atlar, sonraki adıma geçer |


`Örnek:`

````kotlin
for (i in 1..10) {
    if (i == 5) break   // 5'te döngü biter
    if (i == 3) continue // 3'ü atla
    println(i)
}
````

