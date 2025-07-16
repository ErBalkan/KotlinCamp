# LAMBDA İFADELERİ VE FONKSİYONEL PROGRAMLAMA

## 📌 11.1 Fonksiyonlar Birinci Sınıf Vatandaştır
- Kotlin’de fonksiyonlar değişken gibi ele alınabilir.
- Fonksiyonları parametre olarak alabilir, döndürebilir.

## 📌 11.2 Lambda Nedir?
- İsimsiz fonksiyon.
- Kısa ve okunaklı kod yazdırır.

`Örnek:`

````kotlin
val kareAl = { x: Int -> x * x }
println(kareAl(5))  // 25
````

## 📌 11.3 Lambda Syntax

````kotlin
val lambdaAdi: (ParametreTipi) -> DonusTipi = { parametre -> fonksiyonGovdesi }
````

`Örnek:`

````kotlin
val topla: (Int, Int) -> Int = { a, b -> a + b }
println(topla(3, 4))  // 7
````

## 📌 11.4 Koleksiyonlarla Lambda Kullanımı

````kotlin
val sayilar = listOf(1, 2, 3, 4, 5)
val kareler = sayilar.map { it * it }
println(kareler)  // [1, 4, 9, 16, 25]
````

`it: Lambda içindeki tek parametreyi ifade eder.`

## 📌 11.5 Filter, Map, Reduce
- __filter:__ Koşulu sağlayanları seçer.
- __map:__ Her elemana işlem yapar, yeni liste döner.
- __reduce:__ Listeyi tek bir değere indirger.

`Örnek:`

````kotlin
val sayilar = listOf(1, 2, 3, 4, 5)
val ciftSayilar = sayilar.filter { it % 2 == 0 }
println(ciftSayilar)  // [2, 4]

val toplam = sayilar.reduce { acc, sayi -> acc + sayi }
println(toplam)  // 15
````

| Fonksiyon | Açıklama                       |
| --------- | ------------------------------ |
| map       | Her elemana işlem yapar        |
| filter    | Şarta uyan elemanları seçer    |
| reduce    | Elemanları tek değere indirger |


## 6. Bonus: filterNot (Olumsuzu seç)

````kotlin
val sayilar = listOf(1, 2, 3, 4)
val tekSayilar = sayilar.filterNot { it % 2 == 0 }
println(tekSayilar)  // [1, 3]
````

