# KOTLIN COROUTINES VE ASENKRON PROGRAMLAMA

## 📌 12.1 Asenkron Programlama Nedir?
- Bir işlemin diğerini beklemeden, arka planda çalışması.
- Backend’de IO, veri tabanı, API çağrılarında performans patlaması sağlar.

## 📌 12.2 Kotlin Coroutine Nedir?
- Hafif, eş zamanlı çalışan kod parçacıkları (lightweight threads).
- Thread’den çok daha az kaynak kullanır.

## 📌 12.3 Coroutine Başlatmak

````kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Dünya!")
    }
    println("Merhaba,")
}
````

````
* runBlocking ana coroutine.

* launch yeni coroutine başlatır.

* delay non-blocking bekleme.
````

## 📌 12.4 Suspend Fonksiyonlar

- Coroutine içinde çalışacak, beklenebilen fonksiyonlar.
- suspend anahtar kelimesiyle tanımlanır.

````kotlin
suspend fun bekleVeYazdir() {
    delay(1000L)
    println("1 saniye geçti")
}
````

## 📌 12.5 Coroutine Scope
- Coroutine’lerin yaşam döngüsünü kontrol eder.
- GlobalScope, CoroutineScope gibi farklı scope’lar var.

## 📌 12.6 Örnek: Asenkron Veri Çekme

````kotlin
fun main() = runBlocking {
    val veri = async {
        veriTabanindanVeriAl()
    }
    println("Veri: ${veri.await()}")
}

suspend fun veriTabanindanVeriAl(): String {
    delay(2000L)
    return "Kotlin Backend Verisi"
}
````

`Özet:`

| Konsept           | Açıklama                                       |
| ----------------- | ---------------------------------------------- |
| Coroutine         | Hafif eş zamanlı iş parçacıkları               |
| suspend fonksiyon | Beklenebilen fonksiyon                         |
| launch            | Coroutine başlatır, sonuç döndürmez            |
| async             | Coroutine başlatır, sonuç döner                |
| runBlocking       | Ana thread’i bloke ederek coroutine çalıştırır |

## 📌 13.1 Coroutine Dispatcher
- Coroutine’in hangi thread veya thread havuzunda çalışacağını belirler.
- Örnekler: Dispatchers.Main, Dispatchers.IO, Dispatchers.Default.

````kotlin
launch(Dispatchers.IO) {
    // IO işlemleri burada çalışır
}
````

- IO dispatcher veri tabanı ve dosya işlemleri için ideal.
- Default CPU yoğun işleri için.

## 📌 13.2 Coroutine Scope’ları Yönetmek
- `GlobalScope:` Uygulama boyunca yaşayan global scope. Genelde tavsiye edilmez, hata yönetimi zor.
- `CoroutineScope:` Yaşam döngüsü kontrolü için kullanılır. Özellikle Android veya backend servislerde özel scope yaratılır.

````kotlin
val scope = CoroutineScope(Dispatchers.Default)

scope.launch {
    // İşlem
}
````

## 📌 13.5 Cancel ve Timeout
- Coroutine iptal edilebilir.
- withTimeout ile işlem süre limiti koyulur.

````kotlin
withTimeout(1300L) {
    repeat(1000) { i ->
        println("İşlem $i")
        delay(500L)
    }
}
````

Süre aşılırsa `TimeoutCancellationException` fırlatılır.


