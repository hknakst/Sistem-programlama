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

### Unix Dosyası Hiyerarşisi
 (foto)
 
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

Çalışma dizinini değiştirmek için kullanılır. cd <dizin yolu> şeklinde kullanılır. Absolute veya relative yollar kullanılabilir. </br>
Herhangi bir argüman verilmezse cd ~ komutu verilmiş varsayılır ve home dizinine gidilir.Eğer .. parametresi verilirse bir üst dizin . parametresi verilirse de mevcut çalışma dizinine gidilir. </br> 
cd /home/user1
cd ../../user1

### Dosya bilgisi (ls -al) </br>

(foto)

### Dosya türleri 

Plain (düz) (-): çoğu dosya bu türdedir, ikili veya metin dosyaları. </br>
Directory (dizin) (d): bir dosya kümesini gösterir </br>
Symbolic (sembolik) link (l): Başka bir dosya veya dizine işaretçi(pointer).</br>
Özel dosyalar </br>
      Karakter cihazı (c): klavye, yazıcı, joystick.</br>
      Block cihazı (b): disk, CD-ROM.</br>
İletişim dosyaları</br>
      FIFO (p): geçici bir depolama cihazı (sıra).</br>
      Soket (ler): soket dosyaları </br>

- ls -F komutu

ls -F komutu bir dosyanın türünün ne olduğunu gösterir ve dosyanın adının sonuna özel bir karakter yazdırılır.</br>

(boş): Normal dosya</br>
*: Yürütülebilir program veya komut dosyası</br>
/: Dizin </br>
@ : Sembolik bağlantı </br>
| : FIFO (named pipe)
=: Soket </br>

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

(foto)

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
 
 (foto)

chmod komutu dosya sahibini(owner) değiştirmede kullanılır.Genellikle sadece root bu komutu kullanabilir.Yukarıda görüldüğü gibi chmod komutu iki farklı şekilde kullanılır; </br>
Daha çok kullanılan sayılar kullanılarak verilen izinlerdir sayılar belirli bir düzene göre verilebilir;
- r=4	w=2	x=1

chmod 200 a.txt 	yazarsak a dosyasında kullanıcıya sadece yazma hakkı verilir, grup ve diğer(herkese) herhangi bir yetki verilmez.</br>
chmod 635 a.txt		yazarsak kullanıcıya okuma ve yazma, gruplara yazma ve calıstırma, herkese okuma ve calıstırma izni vermiş oluruz.</br>
ikinci kullanım şeklinde grup için g,kullanıcı için u, digerleri icin o harfleri kullanılır.</br>
chmod g-r a.txt 	yazarsak gruplardan okuma yetkisini alır veya benzer şekilde g+rw yazarsak gruplara okuma yazma yetkisi veririz.</br>

- chgrp komutu

chgrp asd a.txt		yazarak a.txt dosyasının grubunu değiştirerek asd grubuna alabiliriz.

-chown komutu 

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

