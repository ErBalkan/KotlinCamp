# KOTLIN’DE NULL SAFETY – SIFIR HATA, SIFIR ÇÖKME

## 📌 9.1 Null Nedir?
- Programlama dillerinde “null” bir değişkenin değerinin olmadığını belirtir.
- Null değerlerle uğraşmak hata riskini artırır.

## 📌 9.2 Kotlin’de Null Safety Neden Önemli?
- Kotlin tasarımı itibarıyla null referans hatalarını önlemek için yapıldı.
- Java’daki klasik NullPointerException hatalarının önüne geçmek için özel mekanizmalar var.

## 📌 9.3 Nullable ve Non-Nullable Tipler
- Kotlin’de değişkenler varsayılan olarak null olamaz.
- Eğer değişken null alabilir olacaksa, tipin sonuna ? koyarsın.

`Örnek:`

````kotlin
var isim: String = "Erhan"    // null olamaz
var soyisim: String? = null   // null olabilir
````

## 📌 9.4 Nullable Değişkenlerle Çalışmak
Nullable bir değişkene direkt erişmek risklidir, derleyici izin vermez.

````kotlin
var soyisim: String? = "Kaya"
println(soyisim.length)  // HATA! çünkü soyisim null olabilir
````

Bunun yerine güvenli çağrı operatörü `?.` kullanılır.

````kotlin
println(soyisim?.length)  // null değilse uzunluğu yaz, null ise null döner
````

## 📌 9.5 Elvis Operatörü ?:
__Null__ durumunda varsayılan değer vermek için kullanılır.

````kotlin
val uzunluk = soyisim?.length ?: 0
println(uzunluk)  // soyisim null ise 0 döner
````

## 📌 9.6 !! Operatörü (Non-null Assertion)
Değişkenin kesinlikle __null__ olmadığını garantiliyorsan kullanılır.

Ama null ise program çöker.

````kotlin
println(soyisim!!.length)  // soyisim null ise hata verir!
````

## 📌 9.7 Fonksiyonlarda Nullable Parametreler

````kotlin
fun yazdir(isim: String?) {
    println(isim ?: "İsim yok")
}

fun main() {
    yazdir(null)        // İsim yok
    yazdir("Erhan")     // Erhan
}
````

`Özet:`

| Konsept                | Açıklama                                         |
| ---------------------- | ------------------------------------------------ |
| Non-null tip           | Null değer alamaz                                |
| Nullable tip (String?) | Null veya değer içerebilir                       |
| ?. operator            | Güvenli çağrı, null ise işlemi atlar             |
| ?: operator            | Elvis operatörü, null ise varsayılan değer verir |
| !! operator            | Null değil kesin garantisi, riskli               |

