# Karar Yapıları – if, else, when

## 📌 3.1 if ve else Yapısı

`💡 Nedir?`
if yapısı, belirli bir koşulun doğru olup olmadığını kontrol eder ve buna göre kod çalıştırır.

`🔍 Yapısı:`

````kotlin
if (koşul) {
    // koşul doğruysa burası çalışır
} else {
    // koşul yanlışsa burası çalışır
}
````

`🔍 Örnek:`

````kotlin
fun main() {
    val yas = 17

    if (yas >= 18) {
        println("Ehliyet alabilirsin")
    } else {
        println("Yaşın yetmiyor")
    }
}
````

## 📌 3.2 else if ile Birden Fazla Koşul Kontrolü

````kotlin
fun main() {
    val not = 75

    if (not >= 90) {
        println("Puan: AA")
    } else if (not >= 80) {
        println("Puan: BA")
    } else if (not >= 70) {
        println("Puan: BB")
    } else {
        println("Kaldın!")
    }
}
````

`🧠 Burada kod üstten aşağıya doğru çalışır ve ilk doğru koşulda durur.`

## 📌 3.3 if Yapısının Kısa Kullanımı (Expression)

````kotlin
val yas = 20
val mesaj = if (yas >= 18) "Reşit" else "Çocuk"
println(mesaj)
````

`🧠 Bu, if’i bir değişkene atamak için kullanılır.`

## 📌 3.4 when Yapısı – Kotlin’in switch Alternatifi

`💡 Ne işe yarar?`
Bir değişkenin farklı değerlerine göre farklı kodları çalıştırmanı sağlar.

`🔍 Temel Kullanım:`

````kotlin
fun main() {
    val gun = 3

    when (gun) {
        1 -> println("Pazartesi")
        2 -> println("Salı")
        3 -> println("Çarşamba")
        4 -> println("Perşembe")
        5 -> println("Cuma")
        else -> println("Hafta sonu")
    }
}
````

`🔍 Birden Fazla Seçeneği Birleştirme:`

````kotlin
when (gun) {
    1, 2, 3, 4, 5 -> println("Hafta içi")
    6, 7 -> println("Hafta sonu")
    else -> println("Geçersiz gün")
}
````

## 📌 3.5 when Yapısının Değişkene Atanması

````kotlin
val not = 85
val harf = when {
    not >= 90 -> "AA"
    not >= 80 -> "BA"
    not >= 70 -> "BB"
    else -> "FF"
}
println("Not harfi: $harf")
````

`🧠 when ifadesi de if gibi değer döndürebilir.`

