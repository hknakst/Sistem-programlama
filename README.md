# Sistem-programlama
## Bölüm-1 Giriş
### neden Unix?
 modern bir işletim sistemi;
- stable : kararlı, kullanıcı ne kadar zorlasada hata yapmaya yönelik bundan etkilenmez.
- flexible : kullanıcı kendine çalışabilir bir alan oluşturabilir.
- configurable : yapılandırılabilir.
- allows multiple users and programs
- Birçok bilimsel ve endüstriyel ortamda kullanılır
- Çok sayıda özgür ve iyi yazılmış yazılım programı
- Açık kaynaklı işletim sistemi (OS)
- Mükemmel programlama ortamı
- Büyük ölçüde donanımdan bağımsız
- Standartlara dayalı
- İnternet sunucuları ve Unix’te çalışan servisler (Dünyadaki web sunucularının yaklaşık% 65’i Apache çalıştıran Linux / Unix makineleridir)

### Unix versionları
iki ana gelişim kolu vardır.
Two main threads of development:
- Berkeley software distribution (BSD) (http://www.bsd.org)
- Unix System Laboratories (http://www.unix.org) </br>
BSD: SunOS 4, Ultrix, BSDI, OS X, NetBSD, FreeBSD, OpenBSD, Linux (GNU) </br>
SYS V: System V (AT&T -> Novell -> SCO), Solaris (SunOS 5), HP-UX (Hewlett-Packard), AIX

### Unix tabanlı bir sistemin katmanları

- işletim sistemi kernel modda çalışır, sistem çağrıları kernel moddadır.(sistem çağrısı: sistemin kaynağı kullanmak istemesi.)
- Standart Library, sistem çağrısı doğrudanda kullanılabilir, kütüphane çağrısı olarakta kullanılabilir.
- user mode , Bellek ve işletim sistemi üzerinde işlemler yapar.( kullanıcı seviyesinde printf("A") yazıldığında burda printf bir library function'dur, write(1,"A",1) şeklinde sistem çağrısı yapılır .)
- shell , kullanıcı komutlarını kabul eder ve bunları yerine getirmekle sorumludur.
- Unix sistemi ile birlikte dört yüzün üzerinde faydalı program veya araç sunulmaktadır. Bu yardımcı programlar (veya komutlar) dosya kopyalama, metin düzenleme, hesaplama yapma ve yazılım geliştirme gibi çeşitli görevleri destekler.

### Unix hesapları
Bir Unix makinesine giriş yapmak o sistem için bir hesap gerektirir.
Bir kullanıcı hesabı giriş ve şifre ile ilişkilendirilmiştir.
“login” kullanıcı adınızdır, şifreniz siz yazarken gösterilmez.(login shell kullanıcıya hizmet veren ilk shell'dir)

Terminal bağlantısını il karşılayan süreç init sürecidir.Super user ıd'si ile koşar.Bu init süreci fork() sistem çağrısı ile 
süreç oluşturur süreç kendisini iki parçaya böler(parent,child).
Sonra kullanıcıdan username girmesini ister username aldıktan sonra login, username için tanımlanmış şifreyi okur ama bu şifre de şifrelenmiştir bu yüzden girilenide şifreler ve karşılaştırır.Encryted halini okur ve karşılaştırır doğrulama yaptıkdan sonra home dizinine setlenir UID=100 ise UID=110 olur kullanıcıya verilecek hizmet hangisi ise ,hangi shell ise login shell icraya başlar kullanıcının çalışma ortamları açılır.

### Shell(kabul) nedir?
Sadece giriş yaptığınızda bir Unix programı çalıştırılabilir.
Bir komut yorumlayıcısıdır.
 - UNIX yardımcı programlarına temel kullanıcı arabirimini sağlar.
Bir programlama dilidir.
  -kabuk komutlarından oluşan program kabuk komut dosyası olarak adlandırılır.
Komutları bir dosyaya koyabilir ve çalıştırabilirsiniz

### Shell sistemi
Giriş yaptıktan sonra, sistemle ilgili bazı bilgiler görüntülenecek ve ardından komutların girilebileceği bir kabuk istemi görüntülenecektir.
Komut satırında yazdıklarımızı bir dosya içerisine yazarak hepsini icra edebiliriz bu dosya scriptfile dosyası olmuş olur.
Dosya içersine yazdığımız kodların hangi bash'in koşacağını belirtmek gerekir.(ilk satırda)Buradaki syntax hangi shell'e göre yazılmıssa ona göre icra edilir.Size hizmet veren Shell ile script'in sytanx'ı aynıysa belirtmeye gerek yoktur.
Dosyanın hangi shell ile koşacağını belirtmek için;
- #!/bin/bash

#!:Bir script dosyasının ilk satırı bu iki karakterle başlamalıdır. Shebang olarak ifade edilen bu karakterlerden hemen sonra, boşluk bırakmadan hangi bash programı kullanılacaksa o programın mutlak adresi yazılır.

/bin/bash: Burada belirtilmesi gereken diğer bir konu da sisteminizde hangi bash yazılımını kullandığınızdır. which bash komutunun sonucu size mutlak adresi söyleyecektir. #! ifadesinden sonra herhangi bir bash adresi yazmasanız da Script çalışabilir. Fakat sizin yazdığınız Script başka bir sistemde çalıştırılmak istendiğinde hata verme ihtimali vardır. Bu sebeple bash adresini yazmayı alışkanlık haline getirmek daha sağlıklı olacaktır.

- # ifadesiyle başlayan satırlar yorum satırlarıdır. 

Bu satırları Bash yorum olarak farz edecek ve işleme almayacaktır. Dosyanın sahibi, oluşturulma tarihi ve oluşturulma maksadı vb. bilgilere burada yer verebilirsiniz.(not: bash=>komut dili yorumlayıcısı)

shell(kabuk), Unix sistemine komut göndermek için kullandığınız programdır. Bazı komutlar tek bir kelimedir.örneğin;
- who komutu

Bu komutla o anki kullancı detaylarını görebiliriz. aynı şekilde whoami komutu ile o anki kullanıcının adını görebiliriz
w komutu ilede login olmuş kullanıcıları görebiliriz.

- date komutu

Bu komutla terminal ekranında sistem tarih ve saat bilgilerini görebiliriz.

- ls komutu 

bulunduğumuz directory(dizin)'deki dosyaları listeler

- $> komut argüman1 argüman2

argümanlarla komuş işlemini değiştirebiliyoruz, daha detaylı listeleme gibi örneğin;
- ls -l
- ls -a
- ls -la
- ls -a;ls -l
- ls -F
- ls -al textfile1
- ls -al textfile1 textfile2
- ls -al directory

ls -l komutu ile dosların ve dizinlerin çok daha detaylı(izinler,kullanıcı ve grup bilgileri, oluşturulma tarihi vb.) halini liste şeklinde görebiliriz.
ls -a komutu gizli dosya ve dizinleri görebiliriz.
ls -la veya ls -al komutuylada ls -l ve ls -a komutlarını beraber kullanabiliriz.
ls -a;ls -l şeklinde de iki komut calıştırılabilir.
ls bin komutuda bin klasöründekileri listeler
ls textfile1 textfile2 yazarsakta bu dosyaları listeler.

Bir komut satırında komut icra ettiğinzde sistem komutu veya programı ise;
shell fork() ile iki süreçe ayrılır(parent ve child), child süreç exec() ile komutu icra eder bu sırada parent süreci bekler ve arka planda komut yürütülürse devam eder.
shell kendi parça komutu ise herhangi bir child süreç oluşturmadan icra eder.(cd,export,echo... kendi komutlarını kendi icra eder yeni bir süreç oluşturmaz.

Komut satırı tepki vermiyorsa bir işlemi icra ediyor ve bir problem olmuş olabilir.
- ctrl + c 

kesme gönderir, süreci keser.

-ctrl + z

sürecin icrasını durdurur.

-ps 

ps komutu sistem üzerinde çalışan süreçleri görebilmenizi sağlar. Bunların arasından süreç kontrolü, süreç sorumlusu, süreç numarası, çalıştırılan komut, zaman, cpu, bellek gibi birçok bilgi görebilirsiniz.

- fg ve bg 

bg komutu: Bu komut bütün Linux dağıtımlarında mevcut olmayabilir. Ancak genel görevi sistemde durmuş olan bir görevi yada processi arka planda devam ettirir.Bunun dışında sistem üzerinde şuanda koşmakta olan görevleri listeler.

fg komutu: Bu komut sistem üzerinde durmakta olan bir süreci yada görevi ön plana çekerek koşmasını sağlar. Her Shell kabuğu bu komutu koşmaz.

- ctrl + d ve exit

terminali kapatır(logout).


