# Fonksiyonlar – Modüler ve yeniden kullanılabilir kod

## 📌 5.1 Fonksiyon Nedir?
- Bir işi yapan, kendi içinde isimlendirilmiş, tekrar tekrar çağrılabilen kod bloğudur.
- Kodun okunabilirliğini, yönetilebilirliğini ve tekrar kullanılabilirliğini sağlar.

## 📌 5.2 Kotlin’de Fonksiyon Tanımlama

````kotlin
fun fonksiyonAdi(parametre1: Tip, parametre2: Tip): DonusTipi {
    // yapılacak işlemler
    return donusDegeri
}
````

## 📌 5.3 Basit Fonksiyon Örneği

````kotlin
fun topla(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    val sonuc = topla(5, 7)
    println("Toplam: $sonuc")
}
````

## 📌 5.4 Parametresiz ve Dönüşsüz Fonksiyon

````kotlin
fun selamla() {
    println("Merhaba, Erhan!")
}

fun main() {
    selamla()
}
````

`Unit dönüş tipi fonksiyonun değer döndürmediği anlamına gelir, genellikle yazılmaz.`

## 📌 5.5 Tek Satırlık Fonksiyonlar
Kotlin seni fazlalıklardan kurtarır.

````kotlin
fun carp(a: Int, b: Int) = a * b
````

## 📌 5.6 Varsayılan Parametreler
Fonksiyon çağrılırken parametre verilmezse varsayılan değer kullanılır.

````kotlin
fun selamla(isim: String = "Dünya") {
    println("Merhaba, $isim!")
}

fun main() {
    selamla()          // Merhaba, Dünya!
    selamla("Erhan")   // Merhaba, Erhan!
}
````

## 📌 5.7 Fonksiyonlarda Named Arguments (İsimli Argümanlar)
Parametrelerin sırasını karıştırmadan isim vererek çağırabilirsin.

````kotlin
fun topla(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    println(topla(b = 5, a = 10))  // 15
}
````

