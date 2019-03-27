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
- Unix System Laboratories (http://www.unix.org)
BSD: SunOS 4, Ultrix, BSDI, OS X, NetBSD, FreeBSD, OpenBSD, Linux (GNU)
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
