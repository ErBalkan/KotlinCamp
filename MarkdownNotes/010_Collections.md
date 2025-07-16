# KOTLIN KOLEKSİYONLARI – LIST, SET, MAP

## 📌 10.1 Koleksiyonlar Nedir?
- Birden fazla veriyi bir arada tutan yapılar.
- Kodunu daha düzenli ve etkili yapar.

## 📌 10.2 List (Liste)
- Sıralı, indeksli, eleman tekrarı olabilir.
- Mutable (değiştirilebilir) ve Immutable (değiştirilemez) listeler vardır.

### Immutable List (sadece okunabilir)

````kotlin
val meyveler = listOf("Elma", "Armut", "Muz")
println(meyveler[1])  // Armut
````

### Mutable List (değiştirilebilir)

````kotlin
val meyvelerMutable = mutableListOf("Elma", "Armut")
meyvelerMutable.add("Muz")
println(meyvelerMutable)  // [Elma, Armut, Muz]
````

## 📌 10.3 Set (Küme)

- Tekrarsız, sırasız veri kümesi.
- Mutable ve Immutable tipleri var.

````kotlin
val renkler = setOf("Kırmızı", "Mavi", "Yeşil", "Mavi")
println(renkler)  // Tekrarsız: [Kırmızı, Mavi, Yeşil]
````

## 📌 10.4 Map (Harita / Sözlük)
- Anahtar (key) - Değer (value) çiftleri.
- Hızlı erişim için kullanılır.

````kotlin
val telefonRehberi = mapOf("Erhan" to "555-1234", "Ayşe" to "555-5678")
println(telefonRehberi["Erhan"])  // 555-1234
````

## 📌 10.5 Koleksiyonlarda Dolaşmak (Loop)

````kotlin
for (meyve in meyveler) {
    println(meyve)
}
````

`Özet:`

| Koleksiyon | Özellik                    |
| ---------- | -------------------------- |
| List       | Sıralı, indeksli, tekrarlı |
| Set        | Sırasız, tekrarsız         |
| Map        | Key-Value çiftleri         |
