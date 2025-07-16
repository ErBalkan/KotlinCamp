# Kotlin Temelleri – Değişkenler ve Veri Tipleri
## 📌 1.1 - Kotlin Nedir?
- __Google__ tarafından desteklenen, modern bir programlama dilidir.
- Android uygulamaları, backend servisleri ve daha fazlası için kullanılır.
- Kotlin, Java’nın daha sade, daha güvenli halidir.

## 📌 1.2 Kotlin’de İlk Adım: val ve var Anahtar Kelimeleri 

### Değişken Nedir?

Değişken, bir veriyi saklamak için kullandığın isimli bir kutudur.
Mesela: bir öğrencinin adını tutmak istiyorsan:

````kotlin
val ad = "Erhan"
````
#### Kotlin’de İki Tür Değişken Tanımı Vardır:

| Anahtar Kelime | Açıklama                                         |
| -------------- | ------------------------------------------------ |
| `val`          | **Sabit** değer. Sonradan değiştirilemez.        |
| `var`          | **Değişebilir** değer. Sonradan güncellenebilir. |

`Örnek:`

````kotlin
val yas = 21      // bu değeri daha sonra değiştiremezsin
var sehir = "İzmir"
sehir = "Ankara"  // bu satır geçerli çünkü var ile tanımlandı
````

## 📌 1.3 Kotlin Veri Türleri
Kotlin'de her veri bir türe sahiptir. Aşağıda en temel veri türleri yer alıyor:

| Tür       | Açıklama                | Örnek              |
| --------- | ----------------------- | ------------------ |
| `Int`     | Tam sayı                | `val sayi = 5`     |
| `Double`  | Ondalıklı sayı          | `val pi = 3.14`    |
| `Boolean` | Doğru ya da yanlış      | `val aktif = true` |
| `String`  | Metin (karakter dizisi) | `val ad = "Erhan"` |
| `Char`    | Tek bir karakter        | `val harf = 'A'`   |


## 📌 1.4 Kotlin’de Yorum Satırları
Koduna notlar ekleyebilirsin. Bilgisayar bunları dikkate almaz.

````kotlin
// Bu bir satırlık yorum
/*
   Bu da
   çok satırlı
   bir yorumdur
*/
````

## 📌 1.5 İlk Kotlin Kodun: main Fonksiyonu

Kotlin’de programlar `main` fonksiyonundan başlar:

````kotlin
fun main() {
    val ad = "Erhan"
    println("Merhaba, $ad!")  // Ekrana yazdırır
}
````

````
📌 println(...) komutu, ekrana yazı yazdırır.

💡 $ad yazdığında Kotlin, ad değişkeninin içeriğini otomatik olarak yazıya ekler.
````

## 📌 1.6 Sabitler Neden val ile Tanımlanır?
Programlamada bazı veriler hiç değişmemelidir. Örneğin:

````kotlin
val dogumYili = 2004
val pi = 3.14159
````

Bunlar bir kez tanımlanır ve asla değişmez. Kodunun güvenliğini artırır.

