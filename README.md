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

- \# ifadesiyle başlayan satırlar yorum satırlarıdır. 

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

ls -l komutu ile dosların ve dizinlerin çok daha detaylı(izinler,kullanıcı ve grup</br> bilgileri, oluşturulma tarihi vb.) halini liste şeklinde görebiliriz.
ls -a komutu gizli dosya ve dizinleri görebiliriz.</br>
ls -la veya ls -al komutuylada ls -l ve ls -a komutlarını beraber kullanabiliriz.</br>
ls -a;ls -l şeklinde de iki komut calıştırılabilir.</br>
ls bin komutuda bin klasöründekileri listeler</br>
ls textfile1 textfile2 yazarsakta bu dosyaları listeler.

Bir komut satırında komut icra ettiğinzde sistem komutu veya programı ise;</br>
shell fork() ile iki süreçe ayrılır(parent ve child), child süreç exec() ile komutu icra eder bu sırada parent süreci bekler ve arka planda komut yürütülürse devam eder.
shell kendi parça komutu ise herhangi bir child süreç oluşturmadan icra eder.(cd,export,echo... kendi komutlarını kendi icra eder yeni bir süreç oluşturmaz.

Komut satırı tepki vermiyorsa bir işlemi icra ediyor ve bir problem olmuş olabilir.
- ctrl + c 

kesme gönderir, süreci keser.

- ctrl + z

sürecin icrasını durdurur.

- ps 

ps komutu sistem üzerinde çalışan süreçleri görebilmenizi sağlar. Bunların arasından süreç kontrolü, süreç sorumlusu, süreç numarası, çalıştırılan komut, zaman, cpu, bellek gibi birçok bilgi görebilirsiniz.

- fg ve bg 

bg komutu: Bu komut bütün Linux dağıtımlarında mevcut olmayabilir. Ancak genel görevi sistemde durmuş olan bir görevi yada processi arka planda devam ettirir.Bunun dışında sistem üzerinde şuanda koşmakta olan görevleri listeler.

fg komutu: Bu komut sistem üzerinde durmakta olan bir süreci yada görevi ön plana çekerek koşmasını sağlar. Her Shell kabuğu bu komutu koşmaz.

- ctrl + d ve exit

terminali kapatır(logout).


## Bölüm-2 Unix dosya sistemi

Dosya sistemi, makinenizdeki fiziksel depolama(diskler) , diğer makinelerdeki depolama (NFS), giriş/çıkış cihazları ve benzeri durumlar için sizin arayüzünüzdür. </br>
Unix'de herşey bir dosyadır.(porgramlar, text dosyaları, çevre birimleri, terminaller...) </br>
Dizinler diğer dosyaları içeren(referanslara) bir dosyadır. </br>
Unix'de sürücü harfleri yoktur.Dosya sistemi, depolama aygıtlarına mantıksal bir görünüm sağlar. </br>

### Çalışma dizini(working directory) </br>
Çalışma dizini: dosya sisteminin geçerli konumu yani sistemdeki konumunuz.
- pwd komutu  </br>

pwd (print working directory) komutu çalışma dizininizin mutlak yolunu (daha sonra) verir.
Başka bir dizin belirtmediğiniz sürece, bir komut çalışma dizini içerisinde çalışmak istediğinizi varsayar.

### Başlangıç(ana) Dizini(home directory) </br>
Ana dizin: kişisel kullanıcı alanı.
Oturum açıldığında, çalışma dizininiz ana dizininize ayarlanacaktır.
Ana dizininize giden yol, ~ (tilde) sembolüyle belirtilebilir.
Kullanıcı1'in ana dizini ~ kullanıcı1 şeklinde belirtilebilir.
Başka bir dizindeysek cd ~/ komutunu vererek ana dizine gidebiliriz.

### Unix Dosya Hiyerarşisi

 ![foto1](https://github.com/hknakst/Sistem-programlama/blob/master/photos/b%C3%B6l%C3%BCm-2/photo1.png)
 
Kök dizini(Root directory) : / , bütün dosyalar root'a bağlanır.
Dizinler düz dosyalar veya başka dizinler içerebilir.
Sonuç, dosya sistemi bir ağaç yapısıdır.
Unix, herhangi özel bir dosya adı uzantısını tanımıyor.

### Unix yolları (Unix paths)

Dizinler / ile ayrılır.
Absolute path(tam yol): Root(kök)'dan başlayarak ağacın takip edildiği yoldur.Örneğin: </br>
/home/user1/textfile </br>
~user1/textfile </br>
~/textfile </br>
Absolute path kullanıcı dizini referans alınarak bildirim yapar. 

Relative path(göreceli yol): çalışma dizininden başlar. </br>
- ..  bir üst dizindir(parent)
- .  çalışma dizinidir(yani dizinin kendisini ifade eder.

textfile </br>
bil318/lec1.txt </br>
çalışma dizinini referans alma : ./../textfile </br>
parent'ı referans alma : ../textfile </br>

### Bazı standart dizinler

Bu dizinler / yani root altındadır. </br>
/ bin - standart komutlar ve yardımcı programlar; yürütülebilir.Kullanıcının koşabildiği tüm programlar bu dizindedir. </br>
/ sbin - root tarafından icra edilebilen programlar, sistem komutları ve yardımcı programları (önyükleme için gerekli) bulunur </br>
/ dev - blok ve karakter aygıtı dizini.Dosya linleri yazıcı,cdrom sürücü tanımlamaları bu dizin altındadır.Terminale tty komutunu verirsek bizim kullandığımız terminal device numarasını verir </br>
/ etc - ana bilgisayara özgü yapılandırma; host hizmetleri </br>
/ home - kullanıcıların ana dizinleri.Kullanıcının login ismiyle dizinler açılır (home/hakan)</br>
/ lib - çeşitli diller için kütüphane dizini.(.so unix dosyaları , .dll windows dosyaları)</br>
/ tmp - geçici dosyalar.(veritabanında taplo update ,update set işlemlerinde tmp kullanılır) </br>
/ usr - kullanıcı yardımcı programları ve uygulamaları; / Usr / local /. Kurulumda değil daha sonra sisteme dahil olan programlardır olsada olur olmasada.</br>
/ var - çeşitli log işlemleri,değişken olan sistem dosyaları için bu dizin kullanılır (günlükler, makaralar, e-posta)


### Dizin değiştirme (changing directories) </br>

- cd komutu </br>

Çalışma dizinini değiştirmek için kullanılır. cd \<dizin yolu> şeklinde kullanılır. Absolute veya relative yollar kullanılabilir. </br>
Herhangi bir argüman verilmezse cd ~ komutu verilmiş varsayılır ve home dizinine gidilir.Eğer ..(ikinokta) parametresi verilirse bir üst dizin .(teknokta) parametresi verilirse de mevcut çalışma dizinine gidilir. </br> 
cd /home/user1 </br>
cd ../../user1

### Dosya bilgisi (ls -al) </br>

 ![foto2](https://github.com/hknakst/Sistem-programlama/blob/master/photos/b%C3%B6l%C3%BCm-2/photo2.png)

### Dosya türleri 

Plain (düz) (-): çoğu dosya bu türdedir, ikili(binary) veya metin dosyaları. </br>
Directory (dizin) (d): bir dosya kümesini gösterir </br>
Symbolic (sembolik) link (l): Başka bir dosya veya dizine işaretçi(pointer).</br>
Özel dosyalar; </br>
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Karakter cihazı (c): klavye, yazıcı, joystick.</br>
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Block cihazı (b): disk, CD-ROM.</br>
İletişim dosyaları;</br>
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FIFO (p): geçici bir depolama cihazı (sıra).</br>
     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Soket (ler): soket dosyaları </br>

- ls -F komutu

ls -F komutu bir dosyanın türünün ne olduğunu gösterir ve dosyanın adının sonuna özel bir karakter yazdırılır.</br>

(boş): Normal dosya</br>
*:&nbsp;&nbsp; Yürütülebilir program veya komut dosyası</br>
/:&nbsp;&nbsp; Dizin </br>
@ :&nbsp;&nbsp; Sembolik bağlantı </br>
| :&nbsp;&nbsp; FIFO (named pipe)
=:&nbsp;&nbsp; Soket </br>

-ls -i komutu

ls -i komutu her dosya için i-node numarasını yazdırır.

### I-nodes

Dosya sistemindeki her nesne için yönetim bilgisidir.
İnode'lar diskte bulunur ve isimleri yoktur. Bunun yerine, inode dizisindeki pozisyonlarını belirten endekslere (sayılara) sahiptirler. </br>
Her inode genellikle şunları içerir:

- Varsa, öğenin içeriğinin diskteki konumu
- Öğenin türü (örneğin, dosya, dizin, sembolik bağlantı)
- Varsa, öğenin bayt cinsinden boyutu
- Dosyanın inode'unun en son değiştirildiği saat (ctime)
- Dosyanın içeriğinin en son değiştirildiği saat (saat)
- Dosyanın en son erişildiği zaman (atime), okuma, yürütme vb.
- Referans sayısı: Dosyanın sahip olduğu adların sayısı
- Dosyanın sahibi (bir UID)
- Dosyanın grubu (bir GID)
- Dosyanın mod bitleri (ayrıca dosya izinleri veya izin bitleri olarak da bilinir)

(inode yapısı cizilebilir)

### Dosya işlemleri 

- touch <file> komutu
 
 touch komutu ile dosya oluşturulur veya oluşturulmuş dosyanın son değiştirilme tarihi değiştirilir. </br>
 
 - mv <file1> <file2>
 
 mv komutunu bu şekilde kullanırsak file1 dosyasının adını file2 olarak değiştirmiş oluruz yani dosyaları yeniden adlandırmada kullanılabilir. </br>
 
 - mv <file1> <dir> 
 
 mv komutunun ikinci parametresine dizin verirsek , birinci parametredeki dosyayı bu dizine taşır. </br>
 
 - mv <file1> <dir/file2>
 
 mv komutunu bu şekilde de kullanabilir. Bu şekilde kullanıldığı zaman dizine dosyayı taşır aynı zaman dosyanın adını file2 olarak değiştirir. </br> 
 
 
 - cp <file> [<file2>|<dir>|<dir/file2>] komutu
 
 cp komutu dosya kopyalama işlemlerinde kullanılır kopyalanır ad değiştirilir veya ikisini birden yapar. cp a deneme/b komutunu verirsek a dosyasını deneme dizininde b dosyası olusturarak bunu içine kopyalar. </br>
 
- rm [-i] <files(s)>

dosya veya dosya listesini siler. link varsa oda eksilir ,dizin ile bağlantısı kopar dizinde o dosyanın yerine null atanır.Dosya silme işlemlerinde çoğu zaman parametre vermeye gerek kalmaz rm dosya_adı yazılarak dosya silinebilir.

### Dizin oluşturma ve silme

- mkdir <directory_name> komutu

Geçerli dizinin altında yeni bir dizin oluşturur.

- rmdir <directory_name> komutu

sadece boş dizini silebilir.

- rm -r <directory_name> komutu

Dizini ve alt dizinler de dahil olmak üzere içeriğinin tümünü yinelemeli olarak kaldırır. r parametresi recursive anlamına gelmektedir silerken altdan yukarıya doğru siler.

### Links(bağlantılar) oluşturma

- ln –s <existing_file> <link_name> komutu

sembolik bir bağ (-s) oluşturur. </br>
link_name, başka bir dizinde veya başka bir fiziksel makinede bulunabilecek varolan dosyanın bir göstergesidir. </br>
hard link(sert bir bağlantı) oluşturmaktan kaçınılmalıdır,aynı cihazın aynı fiziksel bölümünde olmalıdır; link_name, mevcut dosya için başka bir addır. </br>

 ![foto3](https://github.com/hknakst/Sistem-programlama/blob/master/photos/b%C3%B6l%C3%BCm-2/photo3.png)

ln -s fileA fileB  yazarsak, oluşmamış fileB dosyasına sembolik link oluşturuluyor ve fileA'yı işaret ediyor.Oluşturulan bu fileB'ye farklı bir inode atanıyor fakat yapı gereği fileA'ı işaret ediyor.Eğer fileA'da içerik değişirse fileB'de de bu değişiklik görülür. fileB yani sembolik link olam dosyaya birşey yazılırsa fileA'da da içerik değişir çünkü fileB, fileA'nın bölgesini işaret ediyor. </br>

ln fileC fileD  yazarsak, fileD yapı gereği fileC'yi işaret etmek yerine direk fileC'dir yani inode'ları aynıdır bu hard link'tir. fileC'nin link sayısı bir artar bu hard link'lerde böyledir sembolik link'lerde bu artma yoktur.</br>



### Dosya sahipliği

Her dosyanın tek bir sahibi var. </br>
chown komutu sahibini değiştirmek için kullanılabilir; genellikle sadece root bu komutu kullanabilir. </br>
Her dosya aynı zamanda tek bir gruba aittir. </br>
Gruplar herkesten farklı izinlere sahip olabilir. </br>

### Dosya izinleri

Dosyalara veya dizinlere erişime izin vermek veya vermemek için kullanılan izinler aşağıdaki gibidir; </br>
Üç tür izin vardır :</br>
- Oku (r)
- Yaz (w)
- Yürüt (x) (örneğin dosyalarda arama yapmak)

İzinler üç düzeyde verilebilir:</br>
- Kullanıcı (u)
- Grup (g)
- Diğer (o)

- chmod <mode> <file(s)>  komutu 
 
  ![foto4](https://github.com/hknakst/Sistem-programlama/blob/master/photos/b%C3%B6l%C3%BCm-2/photo4.png)

chmod komutu dosya sahibini(owner) değiştirmede kullanılır.Genellikle sadece root bu komutu kullanabilir.Yukarıda görüldüğü gibi chmod komutu iki farklı şekilde kullanılır; </br>
Daha çok kullanılan sayılar kullanılarak verilen izinlerdir sayılar belirli bir düzene göre verilebilir;
- r=4	w=2	x=1

chmod 200 a.txt 	yazarsak a dosyasında kullanıcıya sadece yazma hakkı verilir, grup ve diğer(herkese) herhangi bir yetki verilmez.</br>
chmod 635 a.txt		yazarsak kullanıcıya okuma ve yazma, gruplara yazma ve calıstırma, herkese okuma ve calıstırma izni vermiş oluruz.</br>
ikinci kullanım şeklinde grup için g,kullanıcı için u, digerleri icin o harfleri kullanılır.</br>
chmod g-r a.txt 	yazarsak gruplardan okuma yetkisini alır veya benzer şekilde g+rw yazarsak gruplara okuma yazma yetkisi veririz.</br>

- chgrp komutu

chgrp asd a.txt		yazarak a.txt dosyasının grubunu değiştirerek asd grubuna alabiliriz.

- chown komutu 

chown hkn a.txt		yazarak a.txt dosyasını başka bir kullanıcıdan alıp hkn kullanıcısına verebiliriz.


### Dosyanın içeriğine bakmak

- cat komutu

cat komutunu dosyaların içeriğine bakmak veya içeriğini değiştirmek için kullanılır. </br>
cat textfile1 textfile2 şeklinde kullanırsak önce textfile1'in içeriği hemen ardından textfile2'nin içeriğini terminalde görebiliriz.Eğer dosyanın içeriğini değiştirmek istersek cat >> textfile1 yazarak terminalde textfile1'in içine gidilir ve dosyaya yazma yapılabilir cıkmak için ctrl+c kullanılır,ama burada dikkat edilmesi gereken şey dosyanın üzerine yazma yapılır yani önceki içerik kaybolur.

- more komutu

Uzun bir dosyayı açmak istediğiniz zaman bütün yazılar birden önünüze açılır ve öününzde son satırların olduğu kısımları görürsünüz. Bu gibi durumlarda "more" kullanarak önce ekrana sığabilecek kadar veriyi ekrana yazdırıp daha sonra ENTER ile birer birer satır atlatma yapabilirsiniz.

Herhangi bir satır numarasından itibaren veri çekme işlemi; </br>
more +satir_numarası  dosya_adi  şeklinde olmaktadır.

Belirli bir kelime ile başlayan satırı içeren kısımdan itibaren veri çekme işlemi; </br>
more  +/"kelime"   dosya_adi şeklinde olmaktadır. 


- less komutu 

"less" komutu verileri geriye doğru ilerleterek işleme alır. Öyle ki, bir dosyayı açmaya çalıştığı zaman dosyanın tamamını açıp sonra işlemlere geçmez, herhangi bir text editör programı(mesela vi) dosyayı açaçağı zaman dosyanın hepsini yükledikten sonra açma işlemi yapar, fakat "less" komutu bunun aksine dosyayı tamamiyle ele almaz sadece istenilen, belirtilen kısımlarını işleme alır. Bu yüzden "less" diğer kelime işlemcilerden daha hızlıdır. Performans açısından daha iyidir. Kullanımı "Vi" programına benzemektedir. "more" ile kıyaslandığında "less" daha iyidir.

Komutların kullanımı, "less dosya_adi" şeklinde dosya açıladıktan sonra da herhangi bir komut harfine tıklayarak kullanabilirsiniz. Mesela dosya açıldıktan sonra "q" harfine basarsanız çıkış yapar, "-N" ile satırları numaraları ile gösterir, "& /aranan_kelime" ile aradığınız kelimeleri satırları ile beraber bulur gösterir, "G" ile sayfa sonuna gider, "g" ile sayfa başına gider, "53g" ile 53. satıra gider vb. </br>
"less" ile dosyalar üzerinde herhangi bir düzenleme yapamazsınız. "v" tuşuna basarsanız varsayılan olarak ayarlı olan text editör programınız ile dosya, düzenlenmek üzere açılacaktır.


### Wildcards(joker karakterler)(Globbing)

Linux işletim sistemi, yazdığınız komutları daha kısa ve işlevsel hale getiren joker karakterleri(wildcards) desteklemektedir. Wildcard' lar, size, nispeten daha kompleks işlemler yaparken, kolaylık sağlar. Örnek olarak bir dizin altında bulunan .cfg uzantılı dosyaları başka bir dizine kopyalamak istediğimizi düşünelim. Bunun için normal şartlar altında, ya bir görsel arayüz programı kullanarak, ya da tüm dosyaları tek tek kopyala komutu kullanarak, kaynak dosyaları başka bir dizine yerleştirebiliriz. Ancak wildcards' lar sayesinde aşağıdaki gibi, çok daha kısa bir söz dizimi ile bu işlemi kolaylıkla gerçekleştirebiliriz.</br>

cp ~/workspace/*.cfg ~/workspace2

-  *Bütün karakterler, çoğul seçim
- ?	 Herhangi bir karakter, tekil seçim
- [karakterler]	 Karakter kümesi, veya operatörü ile çalışır.
- [!karakterler]	 Karakter kümesi haricinde demektir.
- [[:sınıf:]]	 Belirtilen bir karakter sınıfına ait olan eşleşme. Karakter sınıfları bir sonraki tabloda anlatılmaktadır.

örnekler; </br>

*.cfg -> Sonu .cfg ile biten dosyalar

A*.cfg -> A ile başlayan Sonu .cfg ile biten dosyalar

???.txt-> 3 harfli olup sonu .txt ile biten dosyalar

[abc]* veya [a-c]-> a, b ya da c ile başlayan dosyalar,[a-c] demek a'dan c'ye kadar olan harfleri temsil etmekdir veya [a-cn-z] ifadesi ile a'dan c'ye ve n'den z'ye kadar olan karakterleri temsil ederiz.

Version.[:digit:] [:digit:] -> Version.rakam rakam formatındaki dosyalar

*[[:upper:]] -> Sonu buyuk harfli biten dosyalar

### Unix komutlarında yardım almak

- man <command_name> komutu

Bu komut ile herhangi bir komut hakkında detaylı bir dökümana erişebiliyoruz. Komutun tüm belgelerini gösterir.

- apropos <keyword> komutu
 
 Belirtilen anahtar kelimeyle birlikte komutların tümünü açıklamalarında gösterir. apropos yerine  man -k  'da kullanılabilir.
 
 - type <string>
 
 komutun sistem yolunu verir.
 
 ### Diğer dosya sistemleri 
 
SunOS'ta 3 farklı dosya sistemi vardır

- Disk tabanlı
- Dağıtılmış
- Sözde(pseudo)

Disk tabanlı dosya sistemleri sabit diskler, CDROM'lar, disketler içerir. </br>
Dağıtılmış dosya sistemleri ağ kaynaklarını yönetir. </br>
Sözde dosya sistemleri bellek tabanlıdır ve disk alanı kullanmaz </br>



## Bölüm-3 Text Editing

Şimdiye kadar dosya sistemindeki dosyaları değiştirdik (cp, mv, rm, ln) ve içeriğini (cat, daha az) görüntüledik. </br>
Dosyaların içeriğini nasıl düzenlersiniz?
Unix editörleri düz ASCII metin dosyalarıyla çalışır: vi, emacs, pico.

### Neden vi?
Kullanılabilirlik
- Herhangi bir Unix / Linux sisteminde çalışabilir.

Komutlar anahtarlardır.

- Uzaktan oturum açma yoluyla erişilebilir (ör. Ssh).
- Fare kullanımını önler.

Basit ve güçlü bir metin editörü.

viden baska emacs,pico gibi editörlerde vardır
vi uzakdan erişim ile teriminale bağlanabilir.

- vi yazarak editörü açabiliriz
- :help yazarak vi editörü hakkında detaylı bir bilgiye ulaşabiliriz
- :q! ile çıkabiliriz
- vi deneme.txt  diyerek bir deneme dosyasını editörde açabiliriz. </br>

iki modu vardır.
- 1. command modu: komutlar icra edilir. ilk açıldığında bu moddadır
- 2. insert modu: dosya iceriği düzenlemesi yapılır. esc'ye basınca komut moduna geceriz.

üç komut modu var biri normal, ikincisi :'dan sonraki komutu, üçüncüsü i modu yani yazma modu
- escape tuşu ile geri gelebiliriz

insert modunda(i'e basınca) backspace ile silebiliriz ama insert modunun dışında x ile veya shift-x ilede silebiliriz.
shift+c alt satırla üst satırı birleştirir

### cursor hareketi:
yön tuşları veya h sol j asağı k yukarı l ise sağ yönde hareket etmemizi sağlar</br>
4j yazınca 4 satır aşağıya gider</br>
CTRL-F sonraki sayfa</br>
u (undo) yazarsak son değişikliği iptal eder </br>
:7 yazarsak direk 7.satıra gider </br>
x  cursorun üzerinde olduğu karekteri siler.(imlecin üzerindeki karekteri)</br>
dd , D  yazarsak cursorun üzerinde olduğu satırı siler</br>
cc ,C 	cursor üzerinde oldugu kelimeyi değiştirir</br>
rx	karakteri x ile yer değiştirir </br>
yy	bir satırın kopyasını alır </br>
p	yapıstırır </br> 
j	üzerinde bulundugu satır ve alt satırı birleştirir. </br>
/bil yazarsak ilk bil yazan yeri bulur //bil ikinci bil yazan yeri bulur </br>
?bil yazarsak bu sefer yukarıya doğru arar </br>

### file operation:
wq	 write quit (kaydeder ve çıkar) </br>
w	 sadece write </br>
w  filename 	dosyaya yaz </br> 
q!	 değişiklik olsa bile değiştirmeden çıkabilirz </br>
e filename	 editöre dosyayı yükle </br>
r filename 	cursor'ın oldugu satırdan itibaren dosyanın oldugu satıra ekle </br>
en son :W yazarsak dosyayı yazar :w! yazarsak üzerine yazar </br>
:wq yazıp yazıp cık denebilir eğer dosyada değişiklik yapıp kaydetmeden cıkmak istiyorsak :q! yazmalıyız :q ile cıkamayız </br>
daha fazla detay için :help dışında http://www.belgeler.org/lis/archive-tlkg-lis-7.2.html kullanılabilir. </br>

### arama:
/kelime	 ileri doğru ara </br>
?kelime  geri doğru ara</br>
n  son aranan tekrar</br>
N  son aranan tersi yönde tekrar</br>



## Bölüm-4 Shell operatörleri

### Üç standart dosya

- stdin , standart giriş

giriş karakter akışı, varsayılan giriş klavye'dir.

- stdout , standart çıkış

çıkış karakter akışı, varsayılan çıkış terminaldir.

- stderr , standart hata(error)

hata mesajlarını alır, varsayılan olarak terminal ayarlıdır.

### stdout yönlendirme

stdout'u terminale yönlendirmek yerine bir programı bir dosyaya yazmasını söyleyebilirsiniz. </br>
\>filename : stdout'u bir dosyaya yönlendirir.Eğer dosya yoksa dosyayı oluşturur.Eğer dosya varsa dosyayı sıfırlar.</br>
\>>filename : varolan bir dosyaya stdout ekler. örneğin; </br>
man ls > ls_help.txt (man ls komutunun cıktısını terminale yazdırmak yerine belirlenen dosyaya yazar)</br>
echo $PWD > current_directory </br>
cat file1 >> file2 (file1 dosyasını file2ye yazar ama file2deki mevcut bilgiyi korur üstüne yazmaz dosyanın devamına yazar.)

### stdin yönlendirme

stdin'in terminalden okumak yerine bir dosyadan okumasını söyleyebiliriz. </br>
<filename : stdin'i mevcut bir dosyaya yönlendirir. </br> 
<<kelime  : takip eden satırlandarn sadece kelime'yi içeren satırada kadar, stdin'i yönlendirir. örneğin; </br>
mail user@domain.com < message.txt </br>
at 3am < cmds or at 0945 < cmds </br>
sort < friends > sorted_friends </br>
cat << end (end kelimesi girilip stdin okuyana kadar yönlendirme yapılır, end kelimesi girildiği an yönlendirme biter ve yazılanları ekrana basar)</br>

### Standart dosya tanımlayıcıları

Bir dosya bir tanımlayıcı ile ilişkilendirilebilir. </br>
Kabuk(shell), sırasıyla her bir komut için üç standart dosyayı üç standart dosya tanımlayıcısı ile ilişkilendirir.</br>
- 0 : standard input (STDIN)
- 1 : standard output (STDOUT)
- 2 : standard error (STDERR)

Standart tanımlayıcılar, kullanıcının terminali ile ilişkilendirilir, ancak başka dosyalara da yönlendirilebilirler.

### Dosya tanımlayıcı oluşturma

Yazmak üzere bir dosyayı açmak için bunlardan birini kullanın. </br>
exec n> filename (dosyayı yazma işlemi için açıyoruz , yazma işlemi kullanıldığında n dosya tanımlayıcıyı oluşturuyor. </br>
exec n>> filename (sonundan itibaren yazmak üzere n oluşturuluyor)</br>
n bir tamsayıdır ve dosya adı, yazmak için açılan dosyanın adıdır. </br>
İlk form, eğer böyle bir dosya varsa, belirtilen dosyanın üzerine yazar. </br>
İkinci form belirtilen dosya adına eklenir. </br>
Bir dosyayı okumak üzere açmak için </br>
exec n<filename (okuma işlemi için açılıyor, okumak için n'nin file nesnesi oluşturuluyor)</br>
Hem okuma hem de yazma için bir dosyayı açmak için </br>
exec n<> filename (n adında dosya tanımlayıcısı oluşturuluru)</br>

### Dosya Tanımlayıcıları ile Yönlendirme

Standart çıktıyı, dosya tanıtıcısı n ile ilişkilendirilmiş dosyaya yönlendirmek için,</br>
komut>& n (n bağlı olduğu dosyaya yazıyor, terminalde yazılacak veri n'nin bağlı olduğu dosyaya yazılır) </br>
Standart girişi, dosya tanımlayıcısı n ile ilişkilendirilmiş dosyadan yönlendirmek için,</br>
komut<&n (komut bilmez veriyi nereden aldığını) </br>
exec n> & -: çıktı dosyası tanımlayıcısı n kapalı.
    exec 1>&- , exec>&-: standart çıkış kapalı.
exec n <& -: giriş dosyası tanımlayıcısı n kapalı.
    exec 0<&- , exec<&-: standart giriş kapalı.
    
    
Bir dosyaya yazma; </br>
exec 4> dosya  ("dosya" yı açın, fd 4 atayın.) </br>
ls> & 4   (ls çıktısını "dosya" ya yaz)</br>

Bir dosyadan okuma  </br>
exec 5 <dosya  ("dosya" yı açın, fd 4 atayın.)  </br>
wc <& 5   ("dosya" dan giriş oku)  </br>

Bir dosyada belirtilen bir yere yazma  </br>
echo 1234567890 > dosya  ("dosya" ya dize yaz.) </br> 
exec 3<> dosya  ("dosya" yı açın, ona fd 3'ü atayın.)</br>
read -n 4 <&3  ( Sadece 4 karakter oku.) </br>
echo -n . >&3   (Oraya bir ondalık işareti yazın.) </br>
exec 3>&-  (fd 3'ü kapatın.) </br>
cat dosya    ( ==> 1234.67890) </br>

### Genel Giriş / Çıkış Yönlendirme
Standart çıkış veya giriş yönlendirmesi açıkça aşağıdaki genel şekilde belirtilir. </br> 
- komut 1>dosya 
- komut 1>>dosya 
- komut 0<dosya 

STDOUT ve STDERR dosyalarını ayrı ayrı dosyalara  yönlendirmek için kullanılan temel sözdizimi; </br>
- komut 1>dosyaA 2>dosyaB </br>
Belirtilen komutun STDOUT dosyası A dosyasına yönlendirilir ve STDERR (hata mesajları) fileB dosyasına yönlendirilir.

### Ayrı Dosyaları Yeniden Yönlendirme

- komut >> dosyaA 2> dosyaB
- komut > fileA 2 >> fileB
- komut  >> dosyaA 2 >> dosyaB

İlk form STDOUT dosyasını fileA'ya ekler ve STDERR'yi fileB'ye yönlendirir. </br>
İkinci form STDOUT'u fileA'ya yönlendirir ve STDERR'yi fileB'ye ekler. </br>
Üçüncü form STDOUT dosyasını fileA'ya ekler ve STDERR'yi fileB'ye ekler. </br>

### Tek Bir Dosyaya Yönlendirme.

Aynı dosyaya STDOUT ve STDERR yönlendirmek veya eklemek için temel sözdizimi; </br>
komut >file2>&1 veya command &> file </br>
komut >>file2>&1 </br>
STDOUT (dosya tanımlayıcısı 1) ve STDERR (dosya tanımlayıcısı 2) belirtilen dosyaya yönlendirilir veya eklenir. </br>
komut 2>&1>>file (bunu yukarıdakiyle karşılaştır). </br>

m> & n: dosya tanımlayıcıları m, n'ye yönlendirilir. </br>
  >&n: standart çıkışı n dosya tanımlayıcısına yönlendirilir
Örnek; </br>
rm -rf /tmp/my_tmp_dir > /dev/null 2>&1
rdate ntp.nasa.gov >> /var/log/rdate.log 2>&1
if [ ! -f $FILE ]; then echo "$FILE is not a file" >&2; fi

### Pipes ( veri yolu)

Pipe (|): Bir komutun stdout'unu diğerinin stdinine bağlar. </br>
Örnekler; </br>

ls –la | less </br>
ls –al | wc </br>
ls-al | sort +4r </br>
cat file | wc </br>
man bash | grep "history" </br>
ps aux | grep user1 | wc –l </br>


### Süreçler(Processes)

Bir seferde birden fazla program çalıştırmak için;. </br>
Noktalı virgülle (;) ayrı komutlar yazılabilir  </br>
- date; who  (sıralı bir şekilde koşar)

Aynı anda birden fazla program çalıştırmak için; </br>
Komutun sonunda ve işaretini (&) kullanın. </br>
ls -al & wc *  (paralel bir şekilde koşar hangisinin nezaman biteceği kesin değildir.) </br>

### Filtreler ( Filters)

Filtre,girişi alan ve bir şekilde dönüştüren bir programdır.

- wc komutu </br>
wc , satır / sözcük / karakter sayısı verir </br>

- grep komutu </br>
grep , belirli bir örneğe sahip hatları arar </br>
grep <pattern> <filename> (örnek RE olabilir) </br>
 
- sort komutu </br>
sort , satırları alfabetik veya sayısal olarak sıralar </br> 
sort -r: normal sıralama düzenini tersine çevirir </br> 
sort -n: sayısal sırada sıralar </br> 
sort + 2n: ikinci sütundaki öğeleri sıralar</br>

- cut komutu </br>
cut - stdout'a gönderilecek her satırın parçalarını seçer. </br>
cut -c1-5: her satırın ilk 5 karakterini seç </br> 
cut -c1,5: her satırın ilk ve beşinci karakterlerini seç </br> 
cut -d: -f1,3 /etc/passwd: kullanıcı adlarını ID'leriyle eşleştir </br>

- head komutu </br>
head , dosyaların ilk birkaç satırını gösterir. </br>
head -n <dosyaadı>    , n: bir tam sayı </br>

- tail komutu </br>
tail , dosyanın son bölümünü görüntüler </br>
tail -n <dosyaadı> : son n satırı . </br>
tail + n <dosyaadı>: n. satırdan sonraki satırlar </br>

- diff komutu </br>
diff ,farklı olan tüm satırları gösterir. </br>

- cmp komutu </br>
cmp , iki dosyanın farklı olduğu ilk yeri bul </br>
<diff / cmp> <dosya1> <dosya2>   </br>

- od komutu </br>
od , Bir dosyanın içeriğini sekizlik(oktal) gösterimini gösterir. </br>
Örneğin. od –c: tüm baytların görsel gösterimi </br>

- ls -lt komutu </br>
ls –lt , zaman sırasına göre dosya listesi </br>

- crypt komutu </br>
crypt , bir dosyayı kodlama veya kod çözme </br>
Örneğin. şifreli anahtar <clear.file> encrypted.file </br>

- tr komutu </br>
tr , girişindeki karakterleri çevirir. </br>
tr "[: lower:]" "[: upper:]" < <dosya>    (dosyadaki küçük harfleri büyük harflere çevirir.)</br>
 
- uniq komutu </br>
uniq , bir dosyadaki tekrarlanan satırları rapor eder veya filtreler. </br>
uniq –d <dosya>    , <dosya> 'da tekrarlanan satırları görüntüleme </br>
uniq –u <dosya>    , <dosya> da tekrarlanmayan ekran satırları görüntüleme  </br> 
uniq –c <dosya>    , <dosya> 'daki tekrarlanan satırları tekrar sayılarıyla birlikte görüntüleme </br>


- pr komutu </br>
pr , dosyaları çeşitli şekillerde yazdırır.
ls -a | pr -n -h $ (pwd) , geçerli dizindeki tüm dosyaların numaralandırılmış bir listesini yazdırır.


Aşağıdaki komut ne yapar?
cat * | tr -sc A-Za-z '\012' | sort | uniq –c | sort –n | tail | pr -5 –t

### Communication(iletişim) komutları

- talk komutu</br>
talk ,sisteme kayitli olan baska bir kullanici ile etkileşimli sohbet</br>
Örneğin. talk hakan pts/2 </br>
- write komutu  </br> 
write, başka bir kullanıcıya mesaj gönderme</br> 
Örneğin. write hakan pts/2  </br> 
mesg [n | y] :  mesajlara izin ver / reddet</br> 

- mail, pine : text tabanlı e-posta programı </br>
- ftp, sftp : metin tabanlı FTP programı </br>
- telnet, ssh : doğrudan diğer makinelere bağlanmak için kullanılır </br>
- lynx : metin tabanlı web tarayıcısı </br>

### Processes(süreçler) komutları
- ps komutu </br>
ps , mevcut süreçleri listeler </br>

- top komutu </br>
top , sistemin süreçler tarafından kullanımının dinamik gösterimini yapar

- kill komutu </br>
kill , belirlenen bir süreci sonlandır (varsayılan: SIGTERM) </br>
kill –9 <pid> (SIGKILL sinyali gönderiliyor)</br>

- time komutu </br>
time,  bir süreç için zamanlama bilgisini tutar ve gösterir. </br>
time ls (real / user / sys zamanı gösteriliyor).</br>

- wait komutu </br>
wait , & ile başlayan tüm işlemleri bekliyor.(belli bir işlemi bekleme) </br>

- nohup komutu </br>
nohup , oturumu kapattıktan sonra komutu çalıştırmaya devam ettirir.

- nice komutu </br>
nice , komutu düşük öncelikle çalıştırmaya devam et. </br>
nohup / nice <komut> &

### Daha fazla dosya sistemi komutları

- file komutu  </br>
file , dosya türünü belirler(gösterir)  </br>
file /bin/ed  </br>
/bin/ed: saf çalıştırılabilir  </br>

Çalıştırılabilir binary bir program, başında "sihirli sayı" ile işaretlenmiştir.  </br>
od / bin / ed  </br>
0000000 **077505** 046106 000402 000400 000000  </br>

- du komutu  </br> 
du , ne kadar disk alanı kullandığını gösterir.  </br>
du <dosya / dizin>    (disk blokları cinsinden)  </br>

- df komutu 
df , bağlı dosya alt sistemlerindeki alanı gösterir.  </br>
df –k   (disk blokları cinsinden) (bir blok = 512 veya 1024 bayt)  </br>



## Bölüm-5 Regular Expressions(Düzenli ifadeler)

### RE kullanan UNIX Programları

- grep   (dosya içinde ara).
- egrep   (genişletilmiş RE'ler ile grep).
- vi / emacs   (metin editörleri).
- ex   (çizgi(line) editörü).
- sed   (akış(stream) editörü).
- awk   (örüntü(pattern) tarama dili).
- perl   (betik dili).


### Temel ve Genişletilmiş RE'ler

Temel düzenli ifadelerde; </br> 
meta karakterleri ?, +, {,}, (,), |, ve ) özel bir anlamı yoktur (grep) </br>
  Onlara özel bir anlam vermek için kaçış versiyonlarını kullanın: \?, \+, \{, \}, \(, \) ve \| </br>
  
Genişletilmiş düzenli ifadeler kullanıldığında, bu meta karakterlerin özel bir anlamı vardır </br>
  grep –E = egrep </br>

### egrep kullanımı 

egrep pattern filename(s)

Güvenli olmasu için, pattern(model) çevresine tırnak işaretleri yerleştirin.
Örnekler: </br>
egrep "abc" textfile </br>
(dosyada “abc” içeren satırları yazdırır) </br>
egrep -i "abc" textfile </br>
(yukardakiyle aynı, ancak büyük/küçük harf farkını yoksayar ikisinide gösterir.) </br>
egrep -v "abc" textfile </br>
(dosyada “abc” içermeyen satırları yazdırır) </br>
egrep -n "abc" textfile </br>
(satır numaralarını ile beraber yazdırır) </br>
egrep -c "abc" textfile </br>
(dosyada “abc” içeren satır sayısı yazdırır) </br>

### Metacharacters (Özel karakterler)

- Nokta(period)(.): Herhangi bir karakterle eşleştirir. </br>  
“a.c”   abc, adc, a&c, a;c, ... ile eşleşir </br>
“u..x”  unix, uvax, u3(x, ...ile eşleşir </br>

- Yıldız işareti(*): önceki RE'nin sıfır veya daha fazla oluşumuyla eşleşir. </br>  
Kabuktaki joker karakterlerle(wilcards) aynı değildir! </br>  
“ab*c” ac, abc, abbc, abbbc, ... ile eşleşir. (yani a karakteri ile c karakteri arasında b karakterinden kaç tane olduğu önemsizdir. çünkü * işareti önceki RE'yi kasteder yani b'yi )</br>  
“. *” Herhangi bir string'le eşleşir. </br>  

- Artı(+): önceki RE'nin bir veya daha fazla tekrarını eşleştirir </br> 
“ab+c” abc, abbc ile eşleşir ancak ac ile eşleşmez (yani a karakteri ile c karakteri arasında b karakterinden en az bir tane olmalı, en fazla kaçtane olduğu ise önemsizdir.çünkü * işareti önceki RE'yi kasteder yani b'yi )</br> 

- Soru işareti (?): Önceki RE'nin sıfır veya bir tekrarı ile eşleşir </br> 
“ab?c” ac, abc ile eşleşir ancak abbc ile eşleşmez </br>  

- Mantıksal veya (|): bar öncesi RE veya bar sonrası RE ile eşleşir </br> 
“abc | def”, abc veya def ile eşleşir </br> 

- Şapka (^): satırın başlangıcı anlamına gelir </br>
“^D.*”, D ile başlayan bir satırla eşleşir </br>

- Dolar işareti ($) satır sonu anlamına gelir </br>
“.*d$”, d ile biten bir satırla eşleşir

- Ters eğik çizgi (\\): diğer meta karakterlerden kaçar yani meta karakterler ile normal karakterlerin karışmasını önler</br> 
“file\\.txt”, file.txt ile eşleşiyor ancak file_txt ile eşleşmiyor</br>

- Köşeli parantez ([]): bir karakter kümesi listesini belirtir. </br>
kümedeki herhangi bir karakter eşleşecek </br>
^ 'den sonraki karakterler ile eşleşmeyecek . </br>
-bir karakter aralığını belirtir. </br>
Örnekler:</br>
 
“[fF]un” fun,Fun ile eşleşir. Yani F yada f olmalı. </br>
“b[aeiou]g” bag, beg, big, bog, bug ile eşleşiyor. </br> 
“[A-Z].*”, Büyük harfle başlayan bir dizeyle eşleşir </br>
“[^Abc].*”  a, b veya c ile başlamayan dizelerle eşleşir </br>

- Parantezler (()): gruplamak için kullanılır.</br>

“a(bc)*” ifadesi a, abc, abcbc, abcbcbc, ... ile eşleşir.</br>
“(foot|base)ball” football ya da baseball ile eşleşir</br>

- Süslü Parantez ({}): bir RE'nin tekrar sayısını belirtmede kullanılır. </br>

“[a-z]{3}” üç küçük harfle eşleşiyor.Yani en az üç küçük harf barındırıyorsa </br>
“m.{2,4}” dizeleri m ve ardından 2 ile 4 karakter arasında eşleştirir. </br>


### Bunlar ne anlama geliyor?

Örnekler </br> 
egrep ”^B.*s$” dosya </br>
egrep ”[0-9]{3}” dosya </br>
egrep ”num(ber)? [0-9]+” dosya </br>
egrep ”word” dosya | wc -l </br>
egrep ”[A-Z].*\?” dosya </br>
ls -l | egrep "^....r.-r.-" </br>

Ya grep kullanılırsa?
En az iki 0 içeren kullanıcı kimliğine sahip kullanıcıları arayın </br>
  grep "^[^:]*:[^:]*:[^:]*0[^:]*0[^:]*:.*" /etc/passwd </br>

/etc/passwd dosya formatı; </br>
\<username>:\x:\<userid>:\<groupid>:\<useridinfo>:\<homedir>:\<loginshell> </br>
x karakteri, şifreli parolanın /etc/shadow dosyasında saklandığını gösterir. </br>


### Egrep ile kelime arama 

Sistem yazım denetimi için küçük bir sözlüğe sahip olabilir:/usr/dict/words  </br>
Beş sesli harfin tümünü içeren kelimeleri alfabetik sırayla bulun. </br>

cat alphvowels.</br>
^[^aeiou]*a[^aeiou]*e[^aeiou]*i[^aeiou]*o[^aeiou]*u[^aeiou]*$ </br>
egrep -f alphvowels /usr/dict/words </br>

Harfleri alfabetik sırada olan altı veya daha fazla harften oluşan tüm kelimeleri bulun. </br>
cat > monotonic </br>
^a?b?c?d?e?f?g?h?i?j?k?l?m?n?o?p?q?r?s?t?u?v?w?x?y?x?$ </br>
egrep -f monotonic /usr/dict/words | grep "......" </br>

pratik:  </br>
En az 10 karakterden oluşan bir sözcükle başlayan satırlar. </br>
Standart 3 bölümlü formda öğrenci kimliği içeren satırlar. </br>
Ardışık 2 büyük harfli sözcük içeren satır sayısı. </br>
Alfabetik karakterle bitmeyen satır sayısı. </br>
Bir cümlenin sonunda sesli harfle başlayan bir kelimeyi içeren satırlar. </br>


## Bölüm-6 UNIX Kabuk Ortamları

### Kabuk özellikleri

Kullanıcı ve işletim sistemi arasındaki komut satırı arayüzüdür. </br>
Giriş sırasında otomatik olarak başlar. </br>
Hem komut yorumlayıcısı hem de programlama dilidir. </br>
Kabuk betiği(Shell script), kabuk yorumlaması için mantık içeren bir metin dosyasıdır. </br>

### Kabuk Etkileşimi

- Komut satırı ayrıştırma(parsing)  </br>
- Ortam </br>
- Metin tamamlama (tab tuşu ile) </br>
- Takma adlar.(Aliases) </br>
- Komut satırı düzenleme </br>
- Komut geçmişi </br>
- Yapılandırma. </br>

### Kabuk Programlama

- Değişkenler
- Kontrol Yapıları (Döngüler ve şartlamalar).
- Fonksiton tanımı ve çağırma.
- Kabuk betiği(scripts).
- Sonraki bölüm.

### Çeşitli Unix Kabukları

- sh (Bourne kabuğu, orijinal Unix kabuğu)
- ksh (Korn kabuğu)
- csh (Berkeley'de geliştirilen C kabuğu)
- tcsh
- bash (Bourne Kabuğu.) Linux'ta varsayılan kullanıcı kabuğu
...
Çoğunlukla etkileşim düzeyindeki farklılıklar desteklenir. </br>
http://www.faqs.org/faqs/unix-faq/shell/shell-differences/ </br>

### Kabuk Özellikleri. 
(foto) burası güncellenecek :\)

### Bourne Again SHell (bash)

Bash bu döküman için standart kabuktur.  </br>
Bourne kabuğunun üst kümesidir(sh).  </br>
Sh, csh, tcsh & ksh'dan ödünç alınan özellikler vardır.  </br>
GNU projesinin bir parçasıdır.  </br>

### Değişkenler

Çalışan bir kabuk için üç ana değişken türü vardır; </br>

Yerel(local) değişkenler; </br>
Şu anki kabuğun içinde mevcut olan değişkenlerdir.
Komut isteminde, değişkene değer atanır. </br>

Ortam(environment) Değişkenleri; </br>
Herhangi bir alt kabuk işlemi(child process) için kullanılabilir</br>

Kabuk değişkenleri; </br>
 Kabuk tarafından değer atanması(set) gerekir. </br>
 
### Kabuk Değişkenleri

Kabuğun belirli işlemler için kullandığı değişkenler kümesidir. </br>
Kabuk değişkenleri şunları içerir: </br>
- yerel değişkenler
- Ortam Değişkenleri

</br> 

- env komutu </br>

Geçerli ortam değişkenlerinin listesi, env komutu ile görüntülenebilir. </br>
Değişkenlerin bir adı ve değeri vardır.Varname değerini(listedeki herhangi bir değişkenin adı), echo $varname ile standart çıktıya gönderilerek terminale yazdırılabilir. </br>


### Ortam Değişkenleri

Bazı ilginç değişkenler: HOME, PWD,PATH, PS1, USER, HOSTNAME </br>
$ HOME: home dizini (cd için varsayılan değişken)</br>
Örnek: /home/0607/student </br>
$ PWD: mevcut çalışma dizini </br>
Örnek: /export/home/staff/usern </br>
$ PATH: komutlar için arama yolu </br>
Örnek: /usr/local/bin:/bin:/usr/bin </br>
$ PS1: komut istemi (varsayılan “$”) </br>
Örnek: \u@\h:\w\$ </br> 
$ USER: kullanıcı adı </br>
Örnek: usern </br>
$ HOSTNAME: bilgisayar hostname </br>
Örnek: ktuce </br>

Diğer ilginç değişkenler: UID, PPID, RANDOM, HISTFILE, HISTSIZE, MAIL, MAILCHECK, PS2 </br>
$ UID: mevcut kullanıcı kimliği </br> 
$ PPID: Kabuğu çalıştıran programın işlem kimliği </br> 
$ RANDOM: 0-32767 arasında rastgele bir tam sayı oluşturur </br>
$ HISTFILE: komut geçmişini saklamak için dosya </br>
$ HISTSIZE: saklanacak komut sayısı </br>
$ POSTA: posta gelmişmi diye kabuk tarafından kontrol edilen dosya </br>
$ MAILCHECK: kontroller arasındaki saniye sayısı </br>
$ PS2: İkincil komut istemi (varsayılan ">") </br>

### Değişkenlere atama

Değişkeni varname = value ile ayarlayın </br>
PS1 = $USER@$HOSTNAME: </br>
&nbsp;&nbsp;   Varsayılan kabuk istemini değiştirir </br>
PS1 = "bash_prompt>" </br> 
PATH = $PATH:$HOME/bin , $HOME/bin yolu PATH değişkenine atandı</br> 
PATH = $PATH:~:.  ,  ~ :. PATH'a atandı </br>
DATE=\`date\` veya DATE=$(date)  , DATE değişkeni oluşturduk ve bu değişkene sistem saatini atadık.</br>


### Metin Tamamlama

\<tab> geçerli komutu veya dosya adını tamamlama girişiminde bulunur. </br>
pus\<tab> genişler(tamamlar) için pushd\<space> </br>
pu\<tab> alternatifleri verir. yani pu ile başlayan alternatif komutları gösterir bazen 2 kez \<tab> yapmak gerebiliyor.</br>
   pu pup pushd </br>
/etc içinde, ls init <tab> girildiğinde aşağıdakileri verir </br>
init init.d. initpipe inittab </br>
[lecture]$ ls init </br>

### Aliases (Takma adlar)

Takma adlar, sık kullanılan komutlar için kısa yol olarak kullanılır. </br>
Sözdizimi: alias kısayol=komut </br>
Örnekler: </br>
alian asd=ls  (artık ls komutuna asd adında bir kısayol atadım terminale asd yazdığım zaman ls komutunu çalıştıracak. </br>
alias pu=pushd </br>
alias po=popd </br>
alias l= " ls –F -C " </br> 
alias ll= " ls –L –l -F " </br>
alias d=dirs </br>
alias hide= " chmod og-rwx " </br>
alias unhide= " chmod og+r " </br>

### Komuta Tarihi(geçmişi)

- history komutu</br>

history,önceden girilmiş komutları listelemek için kullanılır.</br>
m'den n'ye kadar önceden yazılmış komutları listelemek için (fc -l \<m> \<n>) kullanılabilir.Bu komutla ilk m ile başlayan satırdan sonra ilk n ile başlayan satıra kadarki geçmiş komutları yazdırır. fc -l ls man tarzı bir kullanımda mümkündür</br>
Geçmiş listesinde gezinmek için imleç tuşlarını yukarı ve aşağı kullanılabilir.</br>

### Komut Satırında Düzenleme

bash bir dizi satır düzenleme komutu sağlar.</br>
Varsayılan emacs modu komutları.(Terminalde komut yazarken uygulanabilecek kısa yollar.) </br>
   Esc-b Bir kelime geri git </br>
   Esc-f Bir kelime ileri git  </br>
   Ctrl-a Satırın başına gitme </br>
   Ctrl-e Satırın sonuna gitme </br>
   Ctrl-k İmleçten satır sonuna kadar olan metini siler.  </br>
Diğer taraftan, ksh kullanıyorsanız komut satırını etkileşimli olarak birkaç şekilde düzenleyebilirsiniz. </br>
   set -o vi, komut satırını düzenlemek için vi komutlarını kullanmanızı sağlar. </br>
   set -o vi-tabcomplete ayrıca bir TAB girerek komutları/dosya adlarını tamamlamanıza izin verir. </br>
   
   
### Login(giriş) Script'leri

Her oturum açtığınızda takma adlar, ortam değişkenleri, komut satırı düzenlemeleri vb. Girmek istemezsiniz. </br>
Bütün bunlar, kabuk her başlatıldığında çalıştırılan bir betikte(script) yapılabilir. </br>

Başlangıçta çalıştırılan başlangıç komut dosyaları; </br>
&nbsp;  /etc/profile </br>
&nbsp;  ~/.bash_profile  </br>
 &nbsp;&nbsp; &nbsp;&nbsp;    ~/.bash_login (eğer .bash_progile yoksa) </br>
&nbsp; &nbsp;&nbsp; &nbsp;    ~/.profile (eğer ikiside yoksa) </br>

Giriş yaptıktan sonra komut dosyası çalıştırıldı </br>
&nbsp;&nbsp;   ~/.bashrc </br>
Oturum kapatıldıktan sonra komut dosyası çalıştırıldı </br>
&nbsp;&nbsp;  ~/.bash_logout </br>
   
   
örnek .bash_ profile (partial);</br>

\# .bash_ profile: oturum açma kabukları için bash tarafından yürütülür. </br>
umask 022 (0666 & ~022 = 0644 = rw-r--r--) </br>
\# varsa, .bashrc komutunu ekleyin </br>
if [ -f ~/.bashrc ]; then </br>
&nbsp;&nbsp; &nbsp;&nbsp;. \~/.bashrc </br>
fi </br>
\# değişkenleri ayarla </br> 
export CVSROOT=\~/.cvsroot </br>
export EDITOR=/bin/vi </br>
export PAGER=/usr/bin/less </br>


örnek .bashrc (partial)</br>

\# .bashrc
\# bazı genel komutların kısaltmaları
alias bye=logout
alias h=history
alias l='ls –F -C'
alias ll='ls-L –l -F'
alias po=popd
alias pu=pushd

Csh için, giriş kabukları çalıştırılır: </br> 
  ~/.profile </br>
ENV ayarlanmışsa: </br>
  &nbsp; Bu dosya her yeni terminal için yürütülür </br>
  &nbsp; örnek: </br>
    &nbsp;&nbsp;ENV=$HOME/.cshrc </br>
   &nbsp;&nbsp;EXPORT ENV (for bash) </br>


## Bölüm-7 Temel Kabuk Betiği (basic shell script)

Bir kabuk betiği nedir?

.......

### Komut dosyası yürütme (Script Execution)

komut dosyasını bir argüman gibi kabuk komutuna verin;</br>
bash my_script</br>

veya komut dosyasının ilk satırında kabuğu(shell) belirleyin; </br>
\#!/bin/bash </br>
&nbsp;&nbsp; komut dosyasının çalıştırılabilir olduğundan emin olun. </br>
&nbsp;&nbsp; my_script 'i doğrudan komut satırında çalıştırın.

Derlemek yoktur, kabuk tarafından yorumlanır.</br>

Basit bir script;</br>
\#!/bin/bash</br>
echo "Hello, World!"</br>
path=$(pwd)</br>
echo $path</br>

Result:</br>
Hello, World!</br>
/home/user2</br>


## Kabuk Değişkenleri
- Numeric (Sayısal)</br>
- String(Dize)</br>
- Arrays (Diziler)</br>
- Komut satırı argümanları; yalnızca okur
- Fonksiyonlar
- var değişkenin adını belirtir, $ var değere</br>
  var = 100 &nbsp;&nbsp;  \# değeri 100 olarak ayarlar </br>
echo ”\\$ var = $ var”  &nbsp;&nbsp; \# $ var = 100 yazdıracak
- unset var ile, bir değişkeni kaldırabiliriz.
- İsimler bir harfle başlar ve harf, rakam ve alt çizgi içerebilir.


##Sayısal Değişkenler

Tamsayı değişkenleri bash'te kullanılabilecek tek saf sayısal değişkenlerdir.</br>
beyan(declaration) ve set değeri:</br>
- declare -i var = 100</br>

Sayısal ifadeler çift parantez içine alınır (C stilinde).</br> Genel format:

var = $((ifade)) veya var = $[ifade] </br>
Örneğin. i = $((var ++)) veya ((var + = 1))</br>
Örneğin. i = $((var2 = 1 + $ var)) veya ((var2 = 1 + var))</br>
Örneğin. i = $[var + 2] - [var + = 2] Hata!</br>
Örneğin. echo $((var * 7)) veya echo $[var * 7]</br>
Örneğin. echo ((var2 = 1 + var)) veya echo [var2 = 1 + var]</br>


Operatörler C / C ++ ile aynıdır.</br>
! +, -, *, /,%, &, |, <,>, <=,> =, ==, =, &&, ||,
\+ =, -! =, * =, / =,% = ~, ~ =, <<, >>, ^


### Dize(string) Değişkenleri 
Açıkça başka bir tür olarak bildirilmediği sürece, değişkenler string'dir.</br>
var = 100, var'ı "100" string'i yapar.</br>
Bununla birlikte, değişkeni çift parantez içine koymak bir tamsayı olarak kabul edilir. ((var2 = 1 + $ var))


Alt stringlerin kullanılması;</br>
- ${string:n}  \# n: index </br>
 &nbsp;&nbsp;&nbsp;${string:5}  \# ilk 5 karakter haric</br>
 &nbsp;&nbsp;&nbsp;${string:(-2)}  \# son iki karakter</br>
- ${string:n:m}  \# n: index, m: number</br>
&nbsp;&nbsp;&nbsp; ${string:0:5}  \# ilk 5 karakter</br>
 &nbsp;&nbsp;&nbsp; ${string:1:3}  \# 2.ile 4. arasındaki 3 karakter</br>
- ${#string}  \# length of string</br>

Birleştirilen strings;</br>
- var1="$var1 $var2"</br>

 Manipüle string</br>
 - y=${x:${#x}-1}${x:1:${#x}-2}${x:0:1}</br>
 bu örnekte x string'inin ilk ve son karakterleri değiştirilerek y'ye atanır.


Değişkenin Yerine koyma;</br>
- $name veya ${name} # name değerini kullanır </br>
- ${name:-value} # eğer name ayarlanmadıysa, değeri(value) kullan
- ${name:=value} # name ayarlanmadıysa, değeri kullanın ve name'e degeri ata
- ${name:?value} # name ayarlanmadıysa, değeri stderr'e yazın
- ${name:+value} # eğer name ayarlanmışsa, değeri kullanın; aksi takdirde null kullanın
- ${name%pattern} # en küçük sonek kalıbını kaldır
- ${name%%pattern} # en büyük sonek kalıbını kaldır
- ${name#pattern} # en küçük önek kalıbını kaldır
- ${name##pattern} # en büyük önek kalıbını kaldır

Dosya adı değiştirme karakterleri (*,?, [...],!) modelde kullanılabilir.


### Dizi Değişkenleri

- Dizi bir değerler listesidir. Boyut bildirmek zorunda değilsiniz
- Bir değere $ {name [index]} ile referans verilebilir.
 - ${a[3]}&nbsp;&nbsp;&nbsp;&nbsp; #dördüncü konumdaki değer
- $a  &nbsp;&nbsp;&nbsp;&nbsp;#${a[0]} ile aynıdır

Bir dizi bildirmek için declare –a komutu kullanılabilir.
- declare -a sports 
- sports=(basketball football soccer)
- spor [3] = hokey

- dizi oluşturma </br> 
sports=(football basketball) </br>
moresports=($sports tennis) </br>
- ${array[@]} or ${array[*]} dizinin tüm içeriğini belirtir.</br>
echo ${moresports[*]} </br>
Çıkış: football tennis </br>
- ${#array[*]} dizideki değerlerin sayısını döndürür.
echo ${#moresports[*]}
Output: 2

### Dışa aktarılan değişkenler 

Export komutu , kabuğun alt(child) süreçlerin değişkene erişmesine izin verir.</br>
- export \<variables>
- declara -x \<vars>

export –p değişkenlerin ve kabuğunuz tarafından verilen değerlerin bir listesini gösterir.

vartest bir program</br>
$> cat vartest</br>
echo x = $x</br>
echo y = $y</br>
$> x=100</br>
$> y=10</br>
$> vartest</br>
x =</br>
y =</br>
$> export y</br>
$> vartest</br>
x =</br>
y = 10</br>


Parantez içinde bir veya daha fazla komut alt kabukta yürütülür</br>
- $> (cd kutusu; ls;)</br>
Cwd'yi değiştirmeyen bin dizinindeki dosyaları listele</br>
- $> (prog1; prog2; prog3) 2> error.txt &</br>
Arka planda üç program yürütür.</br
error.txt dosyasına üç programdaki hataları yazar
- $> x=50; (x=100); echo $x 50 çıktılar

Kıvrımlı ayraçlar içindeki bir veya daha fazla komut geçerli kabuk tarafından yürütülür
- $> {cd bin; ls; }
Cwd'yi değiştiren bin dizinindeli dosyaları listeler
- $> x=50; {x =100; }; echo $x çıktı 100
Giriş ve çıkış bu yapılardan piped yapılabilir. ve G / Ç yönlendirilebilir.

### Komut Satırı Argümanları

Eğer argümanlar bir betiğe(script) geçirilirse, $1,$2,$3, vb. Değerlere sahiptirler. </br>
- $0, betiğin(script) adıdır. </br>
- $*, $0 hariç, boşluklarla ayrılmış tüm argümanların bir dizesidir.
- $@, $0 hariç argümanların bir dizisidir.
- $#, argümanların sayısıdır.

### Çıktı ve alıntılama(quoting)

- echo message  , &nbsp;&nbsp;&nbsp;&nbsp;stdout'a yazdırır.
- echo –n "yes/no? " , &nbsp;&nbsp;&nbsp;&nbsp;bir bilgi istemi
Çıktıdan sonra yeni satır(newline) yazdırmıyor.

Shell, $ ve ‘ ‘(çift tırnak) işaretleri içindeki ifadeleri yorumlar
- $ —değşken yerine geçer
- ‘ —komut yerine geçer
echo "\`date +%D`"   &nbsp;&nbsp;&nbsp;&nbsp; # 04/30/05

Shell özel karakterleri tek tırnak işaretleri içinde yorumlamaz.
- echo '\`date +%D\`' &nbsp;&nbsp;&nbsp;&nbsp; # \`date +%D`

- \\ &nbsp;,&nbsp;&nbsp; karakterlerden kaçmak için kullanılır (örneğin, \ ”, \ $)

### Dönüş değerleri(Return values)
Komut dosyaları bir tamsayı değeri döndürebilir</br>
return N kullanılır.</br>
$? Değişkeni Son çalıştırılan komutun dönüş değerini içerir. </br>
Koşulları test etmek için kullanılabilir </br>
$> pwd</br>
/home/user</br>
$> echo $?</br>
0</br>
$> pwdd</br>
pwdd: not found</br>
$> echo $?</br>
127</br>

### Kullanıcı tanımlı değişkenler

Örnekler:</br>
- $> name =Ali , name değişkenine Ali değeri atanır</br>
- $> echo $ name , Ali görüntülenecek</br>
- $> echo Hello $name! , Welcome to $HOME
 ,bunun bilgisayarınızda çıktısını görün.

Değişken isimleri:</br>
__FRUIT, TRUST_NO_1, _2_TIMES (geçerli) </br>
2_TIMES, _2*2, NO-1  Invalid (geçersiz) </br>


FRUIT=peach</br>
FRUIT=2apples</br>
FRUIT=apple+pear+kiwi</br>

Boşluk kullanımına dikkat edin.</br>
$> FRUIT=apple orange plum</br>
bash: orange: command not found.</br>
Tırnak kullanın. </br>
$> FRUIT="apple orange plum"</br>


### Kullanıcı Girişi Okuma

Genel biçim:
 - read <değişken>

Okuma yürütüldüğünde, kabuk;</br>
standart girdiden bir satır okur.</br>
ilk sözcüğü <değişken> 'de listelenen ilk değişkene atar .</br>
ikinci sözcüğü ikinci değişkene atar. buna benzer şekilde okuma ve atama yapar.</br>

Satırda listelenen değişkenlerden daha fazla kelime varsa, fazla sözcük son değişkene atanır.

- read x y </br>

girilen ilk satırı okur, ilk sözcüğü x değişkeninde saklar ve satırın kalanını y değişkeninde saklar.
Örnek

- $> cat read.sh </br>
 echo &nbsp;&nbsp;–n "Lütfen adınızı ve soyadınızı girin:" </br>
 read name1 name2</br>
         echo "KTU bilg. müh bölümüne hoşgeldiniz, $name1 $name2"



### Komut ve Aritmetik yerdeğiştirme

Komuttan stdout ile değiştirme; </br>
var=\`komut` (' ' arasında geri alıntı yapar)</br>
var=$(komut)</br>

İfade değeri ile değiştirme;</br>

var = $((expresssion)) </br>

Örnekler: </br>
$> echo ‘date‘ # date komutunun çıktısını görüntüler</br>
$> echo sistemde çalışan  \`who | wc –l` kişi var
&nbsp;&nbsp;
 \# bunun çıktısını görün</br>
c = $ ((2 + 3 * 4)) # "echo $ c" 14 görüntüleniyor


### Tamsayılı(integer) Aritmetik

Bash, aritmetik ifadeleri, aritmetik yerdeğiştirme olmadan değerlendirmeyi destekler.</br>
Sözdizimi dolar işareti olmadan $((...))'a benzer.</br>
$> x=10</br>
$> ((x=x*12))</br>
$> echo $x # 120 verir. </br>
Aritmetik ifadeler, if, while ve until komutlarında kullanılabilir.</br>

Karşılaştırma operatörleri çıkış durumunu ayarlar(set'ler)</br>
Karşılaştırma sonucu yanlış ise sıfır olmayan bir değer </br>
sonuç doğruysa sıfır değeri</br>
((i == 100)) eğer i, 100'e eşit ise çıkışa 1(true)dönderir, aksi halde çıkışa sıfır(false) dönderir.</br>
if((i == 100)) ... [“$i” –eq 100] ile aynı etkiye sahip</br>

### expr(ifade) komutu

expr komutu, kullanıcı tanımlı değişkenler üzerinde hesaplamalar yapmak için başka formlar sağlar</br>

expr val1 op val2 (boşluklarla ayrılmış)</br>
expr $val1 op $val2 </br>
val3 = \`expr $val1 op $val2`

Örnekler; </br>
$>expr 5 + 7 &nbsp;&nbsp; #12 döndürür </br>
$>expr 6 – 3 – 2 # gives 1 </br>
$>expr 3 + 4 \\* 5 # gives 23</br>
$>expr 24 / 3 # gives 8</br>
$>sum= \`expr 5 + 6\`</br>
$>echo $sum  # gives 11</br>
$>a=12</br>
$>b=90</br>
$>echo sum is $a + $b &nbsp;&nbsp; # sum is 12 + 90</br>
$>echo sum is \`expr $a + $b\`&nbsp;&nbsp; # sum is 102</br>

### Önceden Tanımlanmış Değişkenler

Kabuk tarafından dahili olarak ayarlanan ve kullanıcıya sunulan bazı değişkenler vardır:</br>
1$ - $9: Konumsal parametreler </br>
$0: Komut adı</br>
$#: Konumsal argümanların sayısı</br>
$? : Yürütülen son komutun çıkış durumu ondalık dizgesi (0,1,2 ..) olarak verir.</br>
$$: Eşsiz(unique) dosya isimleri oluşturmak için yararlı olabilen, çalışılan kabuğun süreç(process) numarası. </br>
$! : Arka planda çalışan son komutun işlem kimliği (Son arka plan işleminin PID'sini tutar). </br>
$- : Kabuğun bu çağrısına uygulanan tedarik edilmiş mevcut seçenekler.</br>
$* : $1 'dan başlayan, kabuğun tüm argümanlarını içeren bir dize.</br>
$@: Alıntılananlar hariç, yukarıdakiyle aynı.</br>

Not: $* ve$ @ alıntı yapıldığında aynıdır ve değişkenlere genişler.</br>
"$*", boşlukla birleştirilmiş, kabuğun tüm argümanlarını içeren tek bir kelimedir. Örneğin, '1 2' 3 , "1 2 3" olur. </br>
"$@", kabuk tarafından alınan argümanlarla aynıdır, sonuçta ortaya çıkan sözcük listesi, kabuğa verilenlerle tamamen eşleşir. Örneğin, '1 2' 3 , "1 2" "3" olur.


### Argümanları komut dosyalarına geçirme

Standart UNIX komutları gibi, kabuk komut dosyaları(shell scripts)'da komut satırından değişken alabilir.</br>
Bağımsız değişkenler, komut satırından $1 ile $9 arasındaki konumsal parametreler kullanılarak bir kabuk programın içine geçirilir.</br>
$0  konum parametresi, komut adını veya kabuk komut dosyasını içeren yürütülebilir dosyanın adını belirtir.</br>
Tüm konumsal parametreler $* özel parametresi kullanılarak ifade edilebilir.</br>


Examples

$ cat pass_arg. &nbsp;&nbsp;
 \# 5 sayı kabul eden ve toplamını gösteren bir script.</br>
aktarılan parametrelerin gösterimleri(echo ile) : $1, $2, $3, $4, $5</br>
betiğin adının gösterimi (echo ile) : $0</br>
aktarılan parametrelerin sayısı(echo ile) : $#</br>
sum=\`expr $1 + $2 + $3 + $4 + $5\`</br>
toplamları : $sum</br>


### shift komutu

Bir komut dosyasına 9'dan fazla parametre iletilirse, parametrelere erişmek için iki alternatif vardır:</br>

Notasyonu ${n}</br>
shift komutu</br>

Shift komutu parametreleri bir konum sola kaydırır.</br> Shift komutunun yürütülmesinde, ilk parametrenin üzerine ikincisi yazılır, ikinci'nin üzerine üçüncü yazılır ve bunun gibi devam eder.

Örnek;</br>

Farklı sayıları kabul edecek ve toplamlarını bulacak bir komut dosyası yazalım. Parametrelerin sayısı değişebilir.</br>

$ cat sum_arg</br>
sum=0</br>
while [ $# -gt 0 ]</br>
do</br>
 &nbsp;&nbsp;&nbsp;&nbsp;    sum=\`expr $sum + $1\`</br>
&nbsp;&nbsp;&nbsp;&nbsp;     shift</br>
done</br>
echo sum is $sum</br>

Örnek; Bu örneği birtane script dosyasının içine yazıp daha sonra sh script\.sh 1 2 3 4... şeklinde parametreler vererek terminalden çağırıp deneyebilirsiniz.</br>

\#!/bin/bash</br>
echo "arg1=$1 arg2=$2 arg3=$3"</br>
shift</br>
echo "arg1=$1 arg2=$2 arg3=$3"</br>
shift</br>
echo "arg1=$1 arg2=$2 arg3=$3"</br>
shift</br>
echo "arg1=$1 arg2=$2 arg3=$3"</br>


### Null komutu

Kabuk yerleşik bir null komutuna sahiptir

formatı basit;
- :

Amaç hiçbir şey yapmamak

Genellikle bir komutun, özellikle de komutlarda görünmesi gerekliliğini yerine getirmek için kullanılır. </br>

if grep “^$system” ~/mail/systems > /dev/null</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;:</br>
else</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo “$system is not a valid system”</br>
&nbsp;&nbsp;&nbsp;&nbsp;exit 1</br>
fi</br>
Kabuk, bundan sonra bir komut yazmanızı gerektirir.
Sistem geçerliyse, hiçbir şey yapılmaz



### && ve || operatörleri

Kabuk, bir önceki komutun başarılı veya başarısız olmasına bağlı olarak bir komutu çalıştırmanıza olanak tanıyan iki özel yapıya sahiptir.

&& operatörü eğer önceki komut başarılı bir şekilde derlenirse sonraki komutu uygular.
- komut1 && komut2

komut2 yalnızca komut1 sıfır çıkış durumunu döndürürse çalıştırılır.</br>
örnek; </br>
[ -z $EDITOR ] && EDITOR=/bin/ed

|| operatörü eğer önceki komut başarısız bir şekilde derlenirse sonraki komutu uygular.
- komut1 || komut2

komut2 yalnızca komut1 sıfır olmayan bir çıkış durumu döndürdüğünde çalıştırılır

Örnekler; </br>
[ -z $PATH ] || echo $PATH </br>
 grep "$name" phonebook || echo \ </br>
“Not found $name“ </br>
 who | grep "^$name " > /dev/null || echo \ </br>
"$name's not logged on“ </br> 

(Satırın sonunda \ kullanıldığında, kabuğun satıra devam ettiğini bildirir.)

&& ve || Aynı komut satırında da birleştirilebilir:

who | grep "^$name " > /dev/null && \\</br>
echo "$name is logged on" || echo "$name’s \\</br>
not logged on"

Grep başarılı olursa ilk echo gerçekleşir;başarısız olursa ikinci echo.

Bu operatörler if komutları ile temsil edilebilir.

if grep "$name" phonebook</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;:</br>
else</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo "Couldn't find $name“</br>
fi</br>


### Koşullu İfadeler

Her Unix komutu, çıkışta kabuğun sorgulayabileceği bir değer döndürür. Bu değer salt okunur kabuk değişkeni $? İçinde tutulur.

0 (sıfır) değeri başarıyı gösterir; 0 (sıfır) dışında herhangi bir şey başarısızlık anlamına gelir.

Tamsayı kullanıyorsanız: ((koşul))</br>
Dizeler kullanılıyorsa: [[koşul]]</br>
Çıkış durumları duruma bağlı olarak sıfır veya sıfır değildir </br>
Örnekler:</br>
(( a == 10 ))</br>
(( b >= 3 ))</br>
[[ $1 = -n ]]</br>
[[ ($v != fun) && ( $v != games) ]]</br>
(( Z > 23 )) && echo Yes</br>

Dosya varlığı, dosya izinleri, sahiplik, dosya türü vb. İçin özel koşullar.

- [[ -e $file ]] –File exists?  (dosya mevcut mu?)
- [[ -f $file ]] –Regular file? (dosya normal mi?)
- [[ -d $file ]] –Directory? (dizin mi?)
- [[ -L $file ]] –Symbolic link? (sembolik link?)
- [[ -r $file ]] –File has read permission? (dosya okuma izni varmı)
- [[ -w $file ]] –File has write permission? (dosya okuma yazma varmı)
- [[ -x $file ]] –File has execute permission? (dosya çalıştırma izni varmı)
- [[ -p $file]] –File is a pipe?

 
 ### İf deyimi

İf ifadesi verilen komutun çıkış durumunu kullanır ve şartlı olarak aşağıdaki ifadeleri çalıştırır.

Genel sözdizimi:</br>
if koşul</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;komutlar (koşul doğruysa)</br>
else</br>
&nbsp;&nbsp;&nbsp;&nbsp;komutlar (koşul yanlışsa)</br>
fi</br>

İç içe if ifadesi:</br>
if (-----)</br>
then ...</br>
else if ...</br>
&nbsp;&nbsp;&nbsp;&nbsp;...</br>
&nbsp;&nbsp;fi</br>
fi</br>

elif ifadesi, else if ifadesi için kısa yol olarak kullanılabilir.

örnek: </br>
if [[ -r $fname ]]</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo “$fname is readable”</br>
elif [[ -w $fname && -x $fname ]]</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo “$fname is writeable and
executable”</br>
fi

### test komutu

Unix sistemi, önceki komutun çıkış durumunu araştıran ve sonucu başarı ya da başarısızlık biçiminde çeviren, yani sonucu 0 ya da 1 olan test komutu sağlar.

Test komutu herhangi bir çıktı üretmez, ancak testin başarısız olup olmadığını kontrol etmek için çıkış durumu if ifadesine geçirilebiliriz.

Herhangi bir komutun çıkış durumunu nasıl öğrenebilirim?

Tüm komutlar çıkış durumunu, echo komutu kullanılarak görüntülenebilen önceden tanımlanmış bir Shell Değişkenine ‘?’ Döndürür. Örneğin;</br>
echo$?</br>
Bunun çıktısı 0 (Sıfır) ise önceki komut başarılı olmuş demektir veya çıktı 1 (Bir) ise önceki komutun başarısız olduğu anlamına gelir.

Test komutunun aşağıda açıklanan dosyalar, sayısal değerler ve diziler üzerinde çalışması için belirli operatörleri vardır:
Test komutuyla kullanılan Sayısal 

Değişkenlerdeki İşleçler:
- -eq : equal to(eşittir)
- -ne : not equals to(eşit değildir)
- -gt : grater than (dan büyüktür)
- -lt : less than (dan küçüktür)
- -ge : greater than or equal to(büyük veya eşittir)
- -le : less than or equal to(küçük veya eşittir.)


Test komutuyla kullanılan String Değişkenleri işleçleri:
- =  : equality of strings(dizgelerin eşitliği)
- !=  : not equal (eşit değil)
- -z : zero length string (sıfır karakter içeren dize yani null dize).
- -n : String length is non zero.(dize uzunluğu sıfır değil)

Örnekler: </br>
$> a=12; b=23 </br>
$> test $a –eq $b </br>
$> echo $? &nbsp;&nbsp;&nbsp;&nbsp; # 1verir </br> 
$> name=”Ahmet” </br>
$> test –z $name &nbsp;&nbsp;&nbsp;&nbsp; #return 1 </br> 
$> test –n $name &nbsp;&nbsp;&nbsp;&nbsp; #return 0</br>
$> test –z “$address” </br>
$> test $name = “Ali” </br>

Test komutuyla kullanılan dosyalardaki operatörler:</br>
- -f: dosya var.
- -s: dosya var ve dosya boyutu sıfır değil.
- -d: dizin var.
- -r: dosya var ve okuma iznine sahip.
- -w: dosya mevcut ve yazma iznine sahip.
- -x: dosya var ve yürütme iznine sahip.

Örnekler: </br>
$> test –f “mydoc.doc”</br>
\# mydoc.doc dosyasını kontrol eder, varsa 0, yoksa 1 döndürür.</br>
$> test –r “mydoc.doc”</br>
\# mydoc.doc için okuma izni olup olmadığını denetler</br>
$> test –d “$HOME”</br>
\# kullanıcıların ana dizininin varlığını kontrol eder..</br>


### Test komutuyla kullanılan Mantıksal Operatörler:
Birden fazla koşulu birleştirmek mantıksal AND, OR ve NOT işleçleriyle yapılır.
- -a: mantıksal AND(VE)
- -o: mantıksal OR(VEYA)
- ! : mantıksal NOT(DEĞİL)

$> test –r “mydoc.doc” –a –w “mydoc.doc”</br>
\# mydoc.doc dosyasının hem okuma hem de yazma iznini kontrol eder ve sonucA bağlı olarak 0 veya 1 döndürür.

if who | grep -s hakan > /dev/null</br>
then</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo hakan CE sunucusuna giris yapti </br>
else</br>
&nbsp;&nbsp;&nbsp;&nbsp;echo hakan CE sunucusunda mevcut degis</br>
fi

Bu script, şu anda sisteme giriş yapmış olan kişileri listeler ve çıktıyı grep üzerinden pipe ile yönlendirir.


### durum(case) açıklamaları

Sözdizimi:</br>
  case expression in</br>
&nbsp;&nbsp;pattern1)</br>
&nbsp;&nbsp;&nbsp;&nbsp;commands ;;</br>
&nbsp;&nbsp;pattern2)</br>
&nbsp;&nbsp;&nbsp;&nbsp;commands ;;</br>
...
*)</br>
&nbsp;&nbsp;&nbsp;&nbsp;commands ;;</br>
esac</br>

örnekler: </br>
örnek1:  
case $1 in </br>
-a)</br>
&nbsp;&nbsp;&nbsp;&nbsp;a seçeneğiyle ilgili komutlar ;;</br>
-b)</br>
&nbsp;&nbsp;&nbsp;&nbsp;b seçeneğiyle ilgili komutlar ;;</br>
*)</br>
&nbsp;&nbsp;&nbsp;&nbsp;diğer tüm seçenekler ;;</br>
esac</br>

örnek2:  
clear</br>
echo "1. Date and time"</br>
echo  
echo "2. Directory listing"    
echo  
echo "3. Users information "  
echo  
echo "4. Current Directory"  
echo  
echo –n "Enter choice (1,2,3 or 4):"  

örnek3:  

read choice  
case $choice in  
&nbsp;&nbsp;&nbsp;&nbsp;1\) date;;  
&nbsp;&nbsp;&nbsp;&nbsp;2) s -l;;  
&nbsp;&nbsp;&nbsp;&nbsp;3) who ;;  
&nbsp;&nbsp;&nbsp;&nbsp;4) pwd ;;  
&nbsp;&nbsp;&nbsp;&nbsp;*) echo wrong choice;;  
esac  

bu komutları birtane script dosyasının içine yazıp bu dosyayı terminalden çalıştırdığımız zaman bizden birtane argüman ister bu argümanı okuduktan sonra 1,2,3,4 veya diğer olacak şekilde ayırarak farklı komutları çalıştırır.

### for döngüsü

Sözdizimi:  
for var [in list ]  
do  
&nbsp;&nbsp;&nbsp;&nbsp; commands  
done  

Tek bir satırdaki komutlar noktalı virgülle (;) ayrılır.  
Liste belirtilmezse, $@ kabul edilir.  
Aksi takdirde ${list [*]}   , Burada liste bir dizi değişkenidir.

örnekler:  

for colors in Red Blue Green Yellow Orange Black Gray  
&nbsp;&nbsp;do  
&nbsp;&nbsp;&nbsp;&nbsp;echo $colors  
&nbsp;&nbsp;done  
echo

Bu örnek verilen tüm renkleri terminale yazdırır.

### While döngüsü

Sözdizimi:  
while command-list1  
do  
&nbsp;&nbsp; command-list2  
done  

command-list1'deki son komutun çıkış durumu 0 (sıfır) ise, command-list2'deki komutlar yürütülür.  

Anahtar kelimeler break, contiune ve return , C / C ++ ile aynı özelliklere sahiptir.

break [num] veya contiune [num] # num döngü sayısıdır  


### Until döngüsü

Sözdizimi:  
Until command-list1  
do  
&nbsp;&nbsp; command-list2  
done  

Döngü, command-list1'in çıkış durumu sıfır olmadıkça gerçekleştirilir.

While/until komutunun çıkış durumu, command-list2'de yürütülen son komutun çıkış durumudur. Eğer böyle bir komut listesi çalıştırılmazsa, while/until  çıkış 0 durumundadır.

örnekler:  

### eval komutu 
...
(Bölüm 7 henüz bitmedi devam edicek :))



## Bölüm-8 Gelişmiş Kabuk Betiği(Advanced Shell Scripting )

### Fonksiyon oluşturma ve kullanma

Bir kabuk fonksiyonunun tanımı aşağıdaki gibidir:  
isim(){list ;}  

Geçerli ve geçersiz fonksiyon tanımları:
lsl(){ ls -l ; } &nbsp;&nbsp;&nbsp;&nbsp;# geçerli  
lsl { ls -l ; } &nbsp;&nbsp;&nbsp;&nbsp;# geçersiz  

sh için takma ad tanımlama:  
$> cat mycd  
cd () { chdir ${1:-$HOME} ; PS1="\`pwd\`$ " ; export PS1 ; }  
$> source mycd  


Örnekler:

yazdir(){  
&nbsp;&nbsp;&nbsp;&nbsp;for i in {1..13}  
&nbsp;&nbsp;&nbsp;&nbsp;	do  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		echo "hakan"  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		echo "$i"  
&nbsp;&nbsp;&nbsp;&nbsp;	done  
}  

Bu fonksiyon 13 kere hakan ve sırasıyla sayıları yazar ama bu fonksiyonu terminalde koşabilmek için dosyayı source etmemiz gerekir.Bunuda şu şekilde yaparız.  

- source dosya_adı

Bu komuttan sonra dosyamızdaki fonksiyonu ismiyle çağırabiliriz(sadece mevcut terminalde):  
yazdir    
hakan  
1  
hakan  
2 ...  


Her dizinin tek bir satırda listelenmesiyle, PATH'nin geçerli değerini listelemek:  

lspath() {  
&nbsp;&nbsp;&nbsp;&nbsp;OLDIFS="$IFS"  
&nbsp;&nbsp;&nbsp;&nbsp;IFS=:  
&nbsp;&nbsp;&nbsp;&nbsp;for DIR in $PATH ; do echo $DIR ; done  
&nbsp;&nbsp;&nbsp;&nbsp;IFS="$OLDIFS"  
}  
$> lspath | grep "/usr/dt/bin"  


</br>
Dizinini uygun hale getirmek: 

setPath() {  
&nbsp;&nbsp;&nbsp;&nbsp;PATH=${PATH:="/sbin:/bin"};  
&nbsp;&nbsp;&nbsp;&nbsp;for _DIR in "$@"  
do  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if [ -d "$_DIR" ] ; then  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PATH="$PATH":"$_DIR" ; fi  
&nbsp;&nbsp;&nbsp;&nbsp;done  
&nbsp;&nbsp;&nbsp;&nbsp;export PATH  
&nbsp;&nbsp;&nbsp;&nbsp;unset _DIR  
}

Örnek bir çağrı:  
$> setPath /sbin /usr/sbin /bin /usr/bin /usr/ccs/bin  
Her argümanının bir dizin olup olmadığını kontrol eder ve bir dizin varsa PATH'ye eklenir.  


### Fonsiyona parametre verme

Bir parametre script'e iletildiği gibi bir fonsiyona da iletilebilir.  
fonksyion tanımlamak için sözdizimi:  
fonksyion fonksyion_adı()
{  
deyim1  
deyim2  
deyimN  
}  
Bu işlev komut satırından veya kabuk betiğinin içinde aşağıdaki şekilde çağrılır:
fonsiyon-adı arg1 arg2 arg3 argN  

örnek:  

$ vi pass  
function demo()  
{  
echo "All Arguments to function demo(): $*"  
echo "First argument $1"  
echo "Second argument $2"  
echo "Third argument $3"  
return  
}  
\# fonksyionu cağrıyoruz.  
demo -f foo bar  

çıktısı:  
All Arguments to function demo(): -f foo bar  
First argument -f  
Second argument foo  
Third argument bar  

### Değer döndürme(return)

Örnek tanım:  
function topla {  
(( toplam=$1+$2 ))  
return $toplam  
}  

fonksiyonu çağırmak:  
topla 2 3  
echo $?  

$? son işlev çağrısından veya komut tarafından döndürülen değerdir.


### Fonksiyonlar arasında veri paylaşımı

C kabuğu(shell),csh, UNIX dosya sisteminde hızlı hareket etmek için üç yardımcı komut sağlar:  
- popd
- pushd
- dirs

Bu komutlar, dahili olarak bir dizin yığınını korur ve kullanıcının yığından dizinleri ekleyip, çıkarmasına olanak tanır ve yığının içeriğini listeler.


dirs uygulaması:  
</br>
dirs() {  
&nbsp;&nbsp;\# IFS'yi kaydedin, ardından şuna ayarlayın:   
&nbsp;&nbsp;\# _DIR_STACK öğelerine ayrı ayrı erişmek için.  
&nbsp;&nbsp; OLDIFS="$IFS"  
&nbsp;&nbsp;IFS=:  
&nbsp;&nbsp;# her dizini ve ardından bir boşluk yazdır  
&nbsp;&nbsp;for i in $_DIR_STACK  
&nbsp;&nbsp;do  
&nbsp;&nbsp;&nbsp;&nbsp;echo "$i \c“  
&nbsp;&nbsp;done  
&nbsp;&nbsp;# tüm girişlerden sonra yeni bir satır ekle  
&nbsp;&nbsp; \# _DIR_STACK yazdırıldı
&nbsp;&nbsp;echo  
&nbsp;&nbsp; \# IFS'yi geri yükle 
&nbsp;&nbsp;IFS="$OLDIFS"  
}  

pushd uygulaması:  
...(gelecek)  
popd uygulaması:  
...(gelecek)  

### echo komutu

metin veya değişken değerlerini gösterir.  
echo [options] [string, değişkenler ...]

Seçenekler:  
- -n Sondaki yeni satırı çıkışa vermez.
- -e Aşağıdaki kaçış karakterleri yorumlar.
- \\c Sondaki yeni satırı bastırır.
- \\a Bir uyarı (zil).
- \\b geri al.
- \\n yeni satır.
- \\r satır başı.
- \\t yatay sekme(tab).
- \\ters eğik çizgi.

### renkli metin gösterme

echo ile birlikte kullanılan bazı kontrol karakterleri vardır.  
Bu kod, mesajı Mavi renkte yazdırır:  
$> echo "\033[34m Hello Colorful World!"  
Hello Colorful World!  

Bu ANSI kaçış dizisini kullanır (\033[34m).  
\033, kaçış karakteri, biraz harekete geçiyor  
[34m kaçış kodu ön plan rengini Mavi olarak ayarlar  
&nbsp;&nbsp;&nbsp;&nbsp;[ CSI'nin başlangıcıdır (Komut Dizisi Giriş).  
&nbsp;&nbsp;&nbsp;&nbsp;34, parametredir.  
&nbsp;&nbsp;&nbsp;&nbsp;m harfdir (eylemi belirtir).  

Genel sözdizimi:  
echo -e "\033[ escape-code your-message "
</br>
(Bu başlık vakit bulursam genişletilebilir...)

### Komut dosyası yürütme(script execution)

Komut dosyasını kabuk programına bir argüman olarak verin (ör. Bash my_script).  
Veya komut dosyasında hangi kabuğun kullanılacağını belirtin.  
- script'in ilk satırı #!/bin/ bash
- Komut dosyasını chmod kullanarak yürütülebilir duruma getirin.
- PATH'in geçerli dizini içerdiğinden emin olun.
- Doğrudan komut satırından çalıştırın 

Derleme gerekmez!



## Bölüm-9 Yazılım Geliştirme: g++ ve make

### Yazılım geliştirme süreçi

- Kaynak dosyalarının oluşturulması.(.c, .h, .cpp)
- Derleme (*.c , *.o) ve bağlama(linking)
- Programları çalıştırma ve test etme.  


Geliştirme araçları:  
Kaynak dosyalarının oluşturulması.(.c, .h, .cpp)  
&nbsp;&nbsp;&nbsp;&nbsp; Text editörleri; vi ,emacs  
&nbsp;&nbsp;&nbsp;&nbsp; versiyon kontrol sistemleri; rcs, cvs  
Derleme (*.o) and bağlama.  
&nbsp;&nbsp;&nbsp;&nbsp;Derleyiciler; gcc, g++    
&nbsp;&nbsp;&nbsp;&nbsp;Otomatik yapı(building) araçları; make  
Çalıştırma ve test etme(xdb,gdb)  

### Derleme şüreci

(foto gelecek)

### Temel g++ Örnekleri

- g++ hello.cpp  
&nbsp;&nbsp;&nbsp;&nbsp; hello.cpp derlenir  
&nbsp;&nbsp;&nbsp;&nbsp; çalıştırılabilir a.out dosyası üretir  
- g++ -o hello hello.cpp  
&nbsp;&nbsp;&nbsp;&nbsp; hello.cpp derlenir  
&nbsp;&nbsp;&nbsp;&nbsp; çalıştırılabilir hello dosyası üretir.  
- g++ -o hello hello.cpp util.cpp  
&nbsp;&nbsp;&nbsp;&nbsp; hello.cpp ve util.cpp derlenir  
&nbsp;&nbsp;&nbsp;&nbsp; çalıştırılabilir hello dosyası üretir.  

Ayrı ayrı derleme:  Herhangi bir kaynak dosyadan, daha sonra çalıştırılabilir yapmak için bağlanacak bir nesne dosyası oluşturabilirsiniz.  
- g++ -c hello.cpp
- g++ -c util.cpp
- g++ -o hello hello.o util.o  


### g++ seçenekleri

- -c  
&nbsp;&nbsp;&nbsp;&nbsp;kaynak dosyalarını derler ama bağlantı(link) yapmak  
&nbsp;&nbsp;&nbsp;&nbsp;çıktı(output) kaynak dosyaya karşılık gelen bir nesne dosyasıdır.  
- o \<dosya\>  
&nbsp;&nbsp;&nbsp;&nbsp;çıktıyı \<dosya\> adlı bir dosyaya koyar.  
- g  
&nbsp;&nbsp;&nbsp;&nbsp;çıktıdaki hata ayıklama(debugging) sembollerini dahil et.  
&nbsp;&nbsp;&nbsp;&nbsp;daha sonra hata ayıklama programı(gdb) tarafından kullanılacak.  
- Wall  
&nbsp;&nbsp;&nbsp;&nbsp;Tüm uyarıları göster(program hala derlenebilir).  
- -D\<macro\>  
&nbsp;&nbsp;&nbsp;&nbsp;macro '1' string'i ile tanımlanır  
- -l\<name\>  
&nbsp;&nbsp;&nbsp;&nbsp;lib\<name\>.a adlı kütüphaneyi dahil eder.
- -I\<path\>  
&nbsp;&nbsp;&nbsp;&nbsp;verilen dizinde bulunan dosyalar dahil etmek(include) için bakar.  
- L\<path\>  
&nbsp;&nbsp;&nbsp;&nbsp;verilen dizinden bulanan kütüphanelere bakar.  

g++'nın kütüphaneler ve dahil edilen dosyalar için varsayılan dizinleri vardır.


### g++ 'da tanımlar

Genellikle programlar aşağıdakilere dayanan koşullu parçalar içerir:  
\#ifdef DEBUG  
printf(“value of var is %d”, var);  
\#endif  

Önişlemci tanımlarını komut satırından ayarlayabilirsiniz:  
g++ -DDEBUG -o prog prog.c  


(genişletilecek...)  

### Derlemede'de make kullanımı

Çok sayıda dosya içeren orta ve büyük çaplı yazılım projelerini derlemek şu sebeblerden zor olur:  
- Her seferinde tüm dosyaları doğru bir şekilde derlemek için komutların yazılması
- Hangi dosyaların değiştirildiğinin takip edilmesi
- Dosyalar arasındaki bağlılıkların takip edilmesi  

make, bu işlemleri otomatikleştirir.  

### make'in temek işlemleri

Programı oluşturmak için, kurallar içeren [Mm]akefile adlı bir dosyayı okur.  
- Eğer program başka bir dosyaya bağlıysa, ozaman bu dosya oluşturulur.
- Tüm bağımlılıklar bağımlılıklar zincirinde geri doğru çalışacak şekilde inşa(build)edilir.
- Programlar yalnızca bağlı(depend) oldukları dosyalardan daha eski ise inşa(built) edilebilir.

### Temel Makefile Örnekleri

\# mydb için Makefile  
mydb: mydb.o user.o database.o  
&nbsp;&nbsp;&nbsp;&nbsp;g++ -o mydb mydb.o user.o database.o  
mydb.o : mydb.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;g++ -c mydb.cpp  
user.o : user.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;g++ -c user.cpp  
database.o : database.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;g++ -c database.cpp  

(foto)  


### Bir Makefile'ın parçaları

Bağımlılık satırları:  
- Hedef(target) adlarını ve bağımlılıklarını içerir (isteğe bağlı)
- bağımlılıklar(dependencies)  
&nbsp;&nbsp;&nbsp;&nbsp;Dosyalar  
&nbsp;&nbsp;&nbsp;&nbsp;hedefler
Komutlar:  
- bağımlılık satırın altında olmalı
- her zaman bir çıkıntıyla(tab) başla
- bağımlılığı karşılamak için komutlar

(foto)

### Makrolar(macros) ve özel değişkenler

Makefile'daki metni temsil etmek için makrolar kullanılır.  
- yazarken kaydeder.
- Makefile'ın kolayca değiştirilmesine izin verir.
- atamalar(assignment)  
&nbsp;&nbsp;&nbsp;&nbsp;Kullanımı: ${MACRONAME}  

Komutlarda özel değişkenler kullanılır:
- $@ hedefi temsil ediyor.
- $? bağımlılıkları temsil ediyor.  

### örneği basitleştirme

OBJS = mydb.o user.o database.o  
CC = /usr/bin/g++  

mydb: ${OBJS}  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} -o $@ $?  
mydb.o: mydb.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} -c $?  
user.o: user.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} -c $?  
database.o: database.cpp mydb.h  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} -c $?  


### Make'i cağırmak (invoking make)

- açıklama dosyası olduğundan emin olun  
&nbsp;&nbsp;&nbsp;&nbsp;makefile veya Makefile olarak adlandırılır  
&nbsp;&nbsp;&nbsp;&nbsp;kaynak dosyalarının bulunduğu dizinde  
- make  
&nbsp;&nbsp;&nbsp;&nbsp;dosyada ilk hedefi oluşturur
- make hedef(leri)  
&nbsp;&nbsp;&nbsp;&nbsp; hedef(leri) oluşturur(builds).
 - diğer seçenekler:  
&nbsp;&nbsp;&nbsp;&nbsp; \-n: komutları çalıştırma, sadece listele  
&nbsp;&nbsp;&nbsp;&nbsp; \-f \<file\>: [Mm]akefile yerine \<file\> 'ı kullan.


### Diğer Makefile Notları ve Son ek(suffix) kuralları

Yorumlar ‘#’ ile başlar  
Bir satırın başına veya yorum olmayan bir satırın sonuna konulabilir.  
Çok uzun olan satırlar, önceki satırın sonuna line \\ koyarak bir sonraki satırda devam edebilir.  

</br>
Son Ek Kuralları:  
her .o dosyasını kaynak dosyadan nasıl oluşturacağını söylemek hala sıkıcı.  
Sonek kuralları bu tür durumları genelleştirmek için kullanılabilir. 

- Varsayılan bir sonek kuralı, komut tarafından çalıştırarak kaynak dosyalarını, .o dosyalarına dönüştürür:  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} ${CFLAGS} -c $<  
- $< , önkoşul anlamına gelir (file.cpp)

### En Basit Makefile Örneği

OBJS = mydb.cpp user.cpp database.cpp  
CC = /usr/bin/g++  

mydb: ${OBJS}  
&nbsp;&nbsp;&nbsp;&nbsp;${CC} -o $@ $?  

### Diğer Faydalı Makefile İpuçları

Ara dosyaları(intermediate) kaldırmanın bir yolunu dahil edin.
- clean:  
&nbsp;&nbsp;&nbsp;&nbsp;rm –f mydb  
&nbsp;&nbsp;&nbsp;&nbsp;rm -f * .o  

çoklu programlar oluşturmak için bir hedef dahil edin.
- all: mydb mycalendar myhomework  


## Bölüm-10 Hata ayıklama (Debugging)

(pek yakında...) 

## Bölüm-11 Süreç Yönetimi (Process Management)
&nbsp;&nbsp;&nbsp;&nbsp;