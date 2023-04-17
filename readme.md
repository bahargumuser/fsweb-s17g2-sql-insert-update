# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu

Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/]

# Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını yazın.

    1) ÖRNEK SORU: Yazar tablosunu KEMAL UYUMAZ isimli yazarı ekleyin.
    insert into yazar (yazarad, yazarsoyad) values ("Kemal", "Uymaz");


    2) Biyografi türünü tür tablosuna ekleyiniz.

    insert into tur (turadi) values ("Biyografi");

    3) 10A sınıfı olan ÇAĞLAR ÜZÜMCÜ isimli erkek, sınıfı 9B olan LEYLA ALAGÖZ isimli kız ve sınıfı 11C olan Ayşe Bektaş isimli kız öğrencileri tek sorguda ekleyin.

    insert into ogrenci (ograd, ogrsoyad, cinsiyet, sinif) values ("Çağlar", "Üzümcü", "e","10A"), ("Leyla" , "Alagöz", "k", "9B"),("Ayşe", "Bektaş", "k", "11C");


    4) Öğrenci tablosundaki rastgele bir öğrenciyi yazarlar tablosuna yazar olarak ekleyiniz.

    insert into yazar (yazarad, yazarsıyad) select ograd, ogrsoyad from ogrenci order by rand() limit 1;

    5) Öğrenci numarası 10 ile 30 arasındaki öğrencileri yazar olarak ekleyiniz.

    insert into yazar (yazarad, yazarsoyad) select ograd, ogrsoyad from ogrenci where ogrno between 10 and 30;

    6) Nurettin Belek isimli yazarı ekleyip yazar numarasını yazdırınız.
    (Not: Otomatik arttırmada son arttırılan değer @@IDENTITY değişkeni içinde tutulur.)

    <!-- BOŞ  -->

    7) 10B sınıfındaki öğrenci numarası 3 olan öğrenciyi 10C sınıfına geçirin.

    update ogrenci set sinif = "10C" where sinif = "10B" limit 3;

    8) 9A sınıfındaki tüm öğrencileri 10A sınıfına aktarın

    update ogrenci set sinif = "10A" where sinif="9A";

    9) Tüm öğrencilerin puanını 5 puan arttırın.

    update ogrenci set puan = (puan + 5);

    10) 25 numaralı yazarı silin.

    delete from yazar where yazarno=25;

    11) Doğum tarihi null olan öğrencileri listeleyin. (insert sorgusu ile girilen 3 öğrenci listelenecektir)

    select * from ogrenci where dtarih is null;

    12) Doğum tarihi null olan öğrencileri silin.

    delete from ogrenci where dtarih is null;

    13) Kitap tablosunda adı a ile başlayan kitapların puanlarını 2 artırın.

    update kitap set puan = (puan + 2) where kitapadi like"a%";

    14) Kişisel Gelişim isimli bir tür oluşturun.

    insert into tur (turadi) values ("Kişisel Gelişim");

    15) Kitap tablosundaki Başarı Rehberi kitabının türünü bu tür ile değiştirin.

    <!-- BOŞ -->

    16) Öğrenci tablosunu kontrol etmek amaçlı tüm öğrencileri görüntüleyen "ogrencilistesi" adında bir prosedür oluşturun.

       <!-- DELIMITER - Sınırlayıcı karakterler için kullanılır.
       STORED PROCEDURE - Veri kayıt etmemiz için hazırlanmış sql kodudur. -->

       CREATE PROCEDURE ogrencilistesi()
       BEGIN
       SELECT * FROM ogrenci;
       END //
       DELIMITER;

    17) Öğrenci tablosuna yeni öğrenci eklemek için "ekle" adında bir prosedür oluşturun.

     <!-- BOŞ -->

    18) Öğrenci noya göre öğrenci silebilmeyi sağlayan "sil" adında bir prosedür oluşturun.

    <!-- BOŞ -->

    19) Öğrenci numarasını kullanarak kolay bir biçimde öğrencinin sınıfını değiştirebileceğimiz bir prosedür oluşturun.

    <!-- BOŞ -->

    20) Öğrenci adı ve soyadını "Ad Soyad" olarak birleştirip, ad soyada göre kolayca arama yapmayı sağlayan bir prosedür yazın.

    <!-- BOŞ -->

    21) Daha önceden oluşturduğunu tüm prosedürleri silin.

    <!-- BOŞ -->

    #Esnek görevler (Esnek görevlerin hepsini Select in Select ile gerçekleştirmeniz beklenmektedir.)
    22) Select in select yöntemiyle dram türündeki kitapları listeleyiniz.

    select * from kitap where turno = (select turno from tur where turadi = "Dram");

    23) Adı e harfi ile başlayan yazarların kitaplarını listeleyin.

    select * from kitap where yazarno in (select yazarno from yazar where yazarad like "e%" );

     <!-- yazarno = yazarların hem ad hem de soyad bilgilerini içeriyor -->

    24) Kitap okumayan öğrencileri listeleyiniz.

     <!-- BOŞ -->

    25) Okunmayan kitapları listeleyiniz.

     <!-- BOŞ -->

    26) Mayıs ayında okunmayan kitapları listeleyiniz.

     <!-- BOŞ -->
