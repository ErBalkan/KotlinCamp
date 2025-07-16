# TASARIM KALIPLARI (DESIGN PATTERNS)

## 📌 13.1 Design Pattern Nedir?
- Yazılım mühendisliğinde tekrar eden problemlere çözüm sunan, denenmiş kod yapılarıdır.
- Projeye hız, esneklik ve sürdürülebilirlik katar.
- Tasarım kalıpları kod şablonları değil, çözüme götüren konseptlerdir.

## 📌 13.2 Tasarım Kalıplarının Faydaları
- Kod tekrarı azaltır.
- Bakımı ve genişletmeyi kolaylaştırır.
- Takım içinde ortak dil oluşturur.

## 📌 13.3 Design Pattern Kategorileri

| Kategori                 | Açıklama                          | Örnekler                      |
| ------------------------ | --------------------------------- | ----------------------------- |
| Creational (Yaratıcı)    | Nesne yaratmayı yönetir           | Singleton, Factory, Builder   |
| Structural (Yapısal)     | Nesneler arası ilişkileri yönetir | Adapter, Decorator, Composite |
| Behavioral (Davranışsal) | Nesneler arası iletişimi yönetir  | Observer, Strategy, Command   |


# SINGLETON DESIGN PATTERN

## 📌 14.1 Singleton Nedir?
- Sadece bir tane nesne oluşturulması gereken durumlarda kullanılır.
- Global erişim sağlar.
- Kaynak kullanımı ve tutarlılık için kritik.

## 📌 14.2 Singleton Kullanım Alanları
- Logger (Loglama işlemleri)
- Config dosyası yönetimi
- Veritabanı bağlantısı
- Cache yönetimi

## 📌 14.3 Kotlin’de Singleton Nasıl Yazılır?
Kotlin’de object anahtar kelimesi ile singleton tanımlamak süper kolay:

````kotlin
object DatabaseConnection {
    init {
        println("Database bağlantısı kuruldu.")
    }

    fun query(sql: String) {
        println("SQL sorgusu çalıştırıldı: $sql")
    }
}
````

- object bloğu JVM’de thread-safe tekil nesne oluşturur.
- init bloğu ilk erişimde çalışır.

## 📌 14.4 Kullanım Örneği:

````kotlin
fun main() {
    DatabaseConnection.query("SELECT * FROM users")
    DatabaseConnection.query("DELETE FROM users WHERE id = 10")
}
````

* Her çağrıda aynı nesne kullanılır.
* Performans ve kaynak tasarrufu sağlar.

## 📌 14.5 Alternatif: Lazy Initialization (Tembel Başlatma)
- Nesne, ihtiyaç duyulana kadar oluşturulmaz.
- `by lazy` ile uygulanabilir.

````kotlin
object Logger {
    val logFile by lazy {
        println("Log dosyası açıldı.")
        "app.log"
    }
}
````

`İlk erişimde logFile oluşturulur.`

# FACTORY DESIGN PATTERN

## 📌 15.1 Nedir Bu Factory Pattern?
- Alt sınıfların örneklerini (instance) oluşturan bir fabrika sınıfı tanımlar.
- Nesne oluşturma işlemini merkezi bir yere taşır.
- Kodun yeni türlerle genişletilmesini sağlar, mevcut kodu değiştirmeden.

## 📌 15.2 Ne Zaman Kullanılır?
- Hangi sınıfın örneğinin gerektiğini çalışma zamanında (runtime) belirlemek istediğinde.
- Yeni sınıflar eklenebilirken eski kodu modifiye etmeden genişletmek istediğinde.
- Eğer “new” ile obje oluşturduğun kodda karışıklık artıyorsa, Factory pattern tam burada devreye girer.

## 📌 15.3 Kotlin'de Basit Factory Pattern Örneği
1. Ortak bir arayüz tanımla:

````kotlin
interface Sekil {
    fun ciz()
}
````

2. Bu arayüzü implement eden sınıfları oluştur:

````kotlin
class Daire : Sekil {
    override fun ciz() = println("Daire çiziliyor.")
}

class Kare : Sekil {
    override fun ciz() = println("Kare çiziliyor.")
}
````

3. Factory sınıfını oluştur:

````kotlin
object SekilFactory {
    fun getSekil(tip: String): Sekil? {
        return when (tip.lowercase()) {
            "daire" -> Daire()
            "kare" -> Kare()
            else -> null
        }
    }
}
````

4. Kullanım:

````kotlin
fun main() {
    val sekil1 = SekilFactory.getSekil("daire")
    sekil1?.ciz()

    val sekil2 = SekilFactory.getSekil("kare")
    sekil2?.ciz()
}
````

````
🧠 Faydaları:
Kodun açık/kapalı prensibine (Open/Closed Principle) uygun olmasını sağlar.

Yeni nesne türleri eklerken, factory’e küçük bir ekleme yapmak yeterlidir.

Nesne oluşturma işlemi tek merkezden yönetildiği için karmaşa azalır.
````

Şekil yerine gerçek dünya örneği olarak mesela `Notification -> EmailNotification, SmsNotification...` => `NotificationFactory`

# BUILDER DESIGN PATTERN

## 📌 16.1 Builder Pattern Nedir?
- Çok sayıda parametreye sahip karmaşık nesneleri adım adım oluşturmak için kullanılır.
- constructor kullanmak yerine yapılandırmayı daha okunabilir hale getirir.
- Aynı nesneyi farklı kombinasyonlarla yaratmanı sağlar.

## 📌 16.2 Ne Zaman Kullanılır?
- Nesneye ait çok fazla alan (field) varsa.
- Bazı alanlar opsiyonel, bazıları zorunlu ise.
- Kod okunabilirliği ve sürdürülebilirliği ön plandaysa.

## 📌 16.3 Kotlin’de Builder Pattern Kullanımı
Kotlin DSL benzeri yazım tarzı ve default parametrelerle builder pattern çok etkili olur.

`✅ Klasik Yöntemle Nesne Oluşturma (Sorunlu 👎):`

````kotlin
class Kullanici(val isim: String, val soyisim: String, val yas: Int, val email: String)

val kullanici = Kullanici("Erhan", "Yılmaz", 25, "erhan@example.com")
````

Kod karmaşıklaştığında parametre sırasını karıştırmak kolaydır.

`✅ Builder Pattern ile (Okunabilir 👍):`
1. __Model Sınıfı:__

````kotlin
class Kullanici private constructor(
    val isim: String?,
    val soyisim: String?,
    val yas: Int?,
    val email: String?
) {
    data class Builder(
        var isim: String? = null,
        var soyisim: String? = null,
        var yas: Int? = null,
        var email: String? = null
    ) {
        fun isim(isim: String) = apply { this.isim = isim }
        fun soyisim(soyisim: String) = apply { this.soyisim = soyisim }
        fun yas(yas: Int) = apply { this.yas = yas }
        fun email(email: String) = apply { this.email = email }
        fun build() = Kullanici(isim, soyisim, yas, email)
    }
}
````

2. __Kullanım:__

````kotlin
val kullanici = Kullanici.Builder()
    .isim("Erhan")
    .soyisim("Yılmaz")
    .yas(25)
    .email("erhan@example.com")
    .build()

println("${kullanici.isim} - ${kullanici.email}")
````

