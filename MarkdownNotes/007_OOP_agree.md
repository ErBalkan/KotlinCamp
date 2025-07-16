# OOP İleri Kavramlar

## 📌 7.1 Kalıtım (Inheritance)
- Bir sınıf başka bir sınıftan özellik ve davranışları devralır.
- Kod tekrarı azalır, yapısal hiyerarşi kurulur.

`Kotlin’de kalıtım için:`

````kotlin
open class Hayvan {
    open fun sesCikar() {
        println("Hayvan ses çıkarıyor")
    }
}

class Kedi : Hayvan() {
    override fun sesCikar() {
        println("Miyav")
    }
}

fun main() {
    val kedi = Kedi()
    kedi.sesCikar()  // Miyav
}
````

````
open sınıfın veya fonksiyonun kalıtıma açık olduğunu belirtir.

override ile fonksiyonun davranışı değiştirilir.
````

## 📌 7.2 Polimorfizm (Çok Biçimlilik)
Aynı metodun farklı nesnelerde farklı davranmasıdır.

````kotlin
fun hayvaninSesi(hayvan: Hayvan) {
    hayvan.sesCikar()
}

fun main() {
    val kedi = Kedi()
    val hayvan = Hayvan()

    hayvaninSesi(hayvan) // Hayvan ses çıkarıyor
    hayvaninSesi(kedi)   // Miyav
}
````

Burada fonksiyon farklı nesne tipleriyle farklı çıktı verir.

## 📌 7.3 Encapsulation (Kapsülleme)
- Sınıfın özelliklerini koruma altına alıp, dışarıdan direkt erişimi engelleme.
- Getter ve Setter metotlarıyla kontrollü erişim sağlama.

`Kotlin’de private kullanımı:`

````kotlin
class BankaHesabi {
    private var bakiye: Int = 0

    fun paraYatir(miktar: Int) {
        if (miktar > 0) {
            bakiye += miktar
        }
    }

    fun bakiyeGoster(): Int {
        return bakiye
    }
}

fun main() {
    val hesap = BankaHesabi()
    hesap.paraYatir(1000)
    println(hesap.bakiyeGoster())  // 1000
    // hesap.bakiye = 500 -> Hata! private olduğu için erişilemez.
}
````

# DATA CLASSES, INTERFACES VE EXTENSION FUNCTIONS

## 📌 8.1 Data Classes (Veri Sınıfları)
Sadece veri tutmak için kullanılır.

* toString(), equals(), hashCode() gibi metotlar otomatik gelir.
* Kotlin’in kod tekrarıyla savaşan süper gücü.

`Örnek:`

````kotlin
data class Kullanici(val isim: String, val yas: Int)

fun main() {
    val kullanici1 = Kullanici("Erhan", 25)
    println(kullanici1)  // Kullanici(isim=Erhan, yas=25)
}
````

## 📌 8.2 Interfaces (Arayüzler)
- Sınıfların uyması gereken kuralları belirler, sadece metot imzaları içerir.
- Çoklu kalıtım gibi davranır, farklı sınıflar aynı interface’i implemente edebilir.

`Örnek:`

````kotlin
interface Ucan {
    fun uc()
}

class Kus : Ucan {
    override fun uc() {
        println("Kuş uçuyor")
    }
}

fun main() {
    val kus = Kus()
    kus.uc()
}

````

## 📌 8.3 Extension Functions (Genişletme Fonksiyonları)
Var olan sınıflara sonradan fonksiyon ekleme imkanı verir, kodunu daha okunaklı yapar.

diyelim ki String sınıfına, yani hazır gelen sınıfa yeni fonksiyon eklemek istiyorsun.

Kotlin, var olan sınıflara dışarıdan yeni fonksiyon ekleme imkanı sunuyor. Böylece o sınıfı değiştirmene gerek kalmadan yeni fonksiyonlar yazabilirsin.

`Örnek:`

````kotlin
fun String.tekrarla(sayi: Int): String {
    return this.repeat(sayi)
}

fun main() {
    println("Erhan".tekrarla(3))  // ErhanErhanErhan
}
````
Burada:

- String sınıfına tekrarla adında bir fonksiyon ekledik.
- this kelimesi, o fonksiyonun çağrıldığı String nesnesini temsil eder.

`Kullanımı:`

````kotlin
fun main() {
    println("Erhan".tekrarla(3))  // ErhanErhanErhan
}
````



















