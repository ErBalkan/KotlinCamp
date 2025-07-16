# Operatörler ve Kullanıcıdan veri alma - readline()

## 📌 2.1 Aritmetik Operatörler
Programlamada sayılarla işlem yapmak için aritmetik operatörler kullanılır. Bunlar matematikte bildiğimiz işlemlerdir:

| Operatör | Anlamı           | Örnek   |
| -------- | ---------------- | ------- |
| `+`      | Toplama          | `a + b` |
| `-`      | Çıkarma          | `a - b` |
| `*`      | Çarpma           | `a * b` |
| `/`      | Bölme            | `a / b` |
| `%`      | Mod (Kalan alma) | `a % b` |

`🔍 Örnek:`

````kotlin
fun main() {
    val sayi1 = 15
    val sayi2 = 4

    println("Toplam: ${sayi1 + sayi2}")
    println("Fark: ${sayi1 - sayi2}")
    println("Çarpım: ${sayi1 * sayi2}")
    println("Bölüm: ${sayi1 / sayi2}")
    println("Kalan: ${sayi1 % sayi2}")
}
````

`🧠 Not: 15 / 4 işlemi 3 döner çünkü Int türünde çalışıyoruz. Ondalıklı sonuç için Double kullan.`

## 📌 2.2 Karşılaştırma Operatörleri
Bu operatörler, iki değeri karşılaştırır ve __Boolean (true/false)__ sonuç verir.

| Operatör | Anlamı              | Örnek    |
| -------- | ------------------- | -------- |
| `==`     | Eşit mi?            | `a == b` |
| `!=`     | Eşit değil mi?      | `a != b` |
| `<`      | Küçük mü?           | `a < b`  |
| `>`      | Büyük mü?           | `a > b`  |
| `<=`     | Küçük veya eşit mi? | `a <= b` |
| `>=`     | Büyük veya eşit mi? | `a >= b` |


`🔍 Örnek:`

````kotlin
fun main() {
    val x = 10
    val y = 20

    println(x == y) // false
    println(x != y) // true
    println(x < y)  // true
}
````

## 📌 2.3 Mantıksal Operatörler
Karar yapılarında sıkça kullanılır. Koşulları birbirine bağlar.

| Operatör | Anlamı                  | Örnek             |                      |         |   |          |
| -------- | ----------------------- | ----------------- | -------------------- | ------- | - | -------- |
| `&&`     | VE (her ikisi doğruysa) | `a > 5 && b < 10` |                      |         |   |          |
| \`       |                         | \`                | VEYA (biri doğruysa) | \`a > 5 |   | b < 10\` |
| `!`      | DEĞİL (tersi)           | `!(a > 5)`        |                      |         |   |          |

## 📌 2.4 Kullanıcıdan Veri Alma (readLine())
Kotlin’de konsoldan veri almak için `readLine()` fonksiyonunu kullanırız.
Ama dikkat: `readLine()`` sana her zaman __String (yani metin)__ döner. Sayısal işlem yapacaksan bunu dönüştürmen gerekir.

`🔍 Örnek: Kullanıcıdan sayı al`

````kotlin
fun main() {
    print("Bir sayı gir: ")
    val girilenDeger = readLine()
    val sayi = girilenDeger!!.toInt()  // String -> Int

    println("Girdiğin sayının karesi: ${sayi * sayi}")
}
````

`💡 Açıklamalar:`
1. __readLine()!! →__ Kullanıcının giriş yapacağını garanti ederiz. (!! boş gelmediğini varsayar)
2. __toInt() →__ String veriyi Int’e çevirir.
3. __print() →__ Satır sonunda alt satıra geçmeden yazar.

