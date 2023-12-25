EDoS

EDoS, uzun adıyla Economic Denial of Sustainability, bulut ortamlarını hedefleyen bir siber güvenlik tehditidir. EDoS saldırıları, hesap iflas edene kadar veya büyük ölçekli hizmetten çekilene kadar bulut kullanıcısının faturasını şişirmek için bulutların esnekliğinden, özellikle de otomatik ölçeklendirme özelliğinden yararlanır.

EDoS saldırıları, uygulamaları, sistemleri ve kurumsal ağları destekleyen bulut hizmetleri ve altyapısının kullanılabilirliğini kesintiye uğratmak veya durdurmak için bulutun ölçek ekonomisinden yararlanır. Genellikle, gizlice sahte talepler gönderen uzaktan kontrol edilen botları içerir. Bu talepler güvenlik kontrollerini atlatırsa, bulut hizmeti otomatik olarak ek kaynak kullanır ve servis alan müşterinin faturasını kabartır.

Geleneksel incident response stratejileri, aşağıdaki nedenlerden dolayı EDoS tehditlerine karşı yeterli donanıma sahip değildir:

EDoS saldırıları genelde IP spoofing saldırıları ile birlikte gerçekleşir ve saldırganlar bilinen kötü IP adreslerini kullanmadığı sürece (SOC Radar gibi yazılımlar ile birlikte tespit edilemediği sürece) mevcut ağ analizi tekniklerini kullanarak tespit edilmesi zordur.
Uygulama ve son kullanıcılar başlangıçta EDoS saldırılarından etkilenmez çünkü zaten bulut kaynakları fazla trafiği kaldırabilmek için otomatik olarak ölçeklenmeye hazırdır. Bu nedenle uygulamalarda performans ölçümleri saldırı tespit etmek için kullanılamaz.
System hardening tehditleri de EDoS’a karşı pek iyi bir koruma sağlamaz çünkü trafik geleneksel anlamda herhangi bir güvenlik açığından faydalanmaz.
Bir EDoS saldırısı tespit edilse bile, olaya müdahale edenler mevcut araçları kullanarak tepki veremezler. Otomatik ölçeklendirme mekanizmalarına kısa devre yaptırabilmek için bulut maliyet yönetim sistemlerine bir arayüz oluşturmaları gerekir.

DoS, DDoS ve EDoS

Şimdi de daha sık bilinen Denial Of Service saldırıları ile EDoS arasındaki farklara bakalım.

DoS
Uzun haliyle Denial Of Service saldırısında saldırganlar, meşru kullanıcıların sisteme erişimini engelleyebilecek, sunucu işlem gücü, bellek ve ağ bant genişliği gibi kaynakları kullanabilecek ve bazı durumlarda hedef sistemi çökertebilecek sahte istekler gönderir.

Genel olarak DoS saldırılarının 2 çeşidi vardır:
Bir Flood DoS saldırısı, çok fazla istek geldiğinde sunucu arabelleklerinin paketleri işleyemediği gerçeğindne yararlanarak hizmetin bozulmasına veya trafiğin reddedilmesine neden olur.
Bir “crash” DoS saldırısı, hedef sistemdeki güvenlik açıklarından faydalanan, çökmesine veya başarısız olmasına neden olan bozuk paketler veya istekler oluşturur.
DDoS
DDoS, yukarıda bahsettiğimiz gibi aslında DoS saldırısının gelişmiş bir versiyonudur. Bu saldırı türü, genellikle saldırganlar tarafından bir sis perdesi olarak kullanılır ve arka planda saldırganlar bir kuruluşun ağına sızarken güvenlik ekiplerini meşgul eder.

DDoS saldırılarını tespit etmek için yukarıda bahsettiğimiz gibi birçok yöntem mevcuttur. EDoS’un doğal mekanizmasından gelen “sınırsız kaynak” konseptinin aksine, DDoS saldırıları sabit bir boyuttaki kaynağa yapıldığı için kaynak tüketimi ve ağ anomalilerinin izlenip tespit edilmesi EDoS’a göre daha kolaydır.

EDoS
EDoS saldırılarında ise asıl amaç, sistemi çökertmekten çok kurbanı ekonomik olarak iflas ettirmektir. Bunun için de bahsettiğimiz gibi bulut servislerinin otomatik ölçeklendirme özelliğinden yararlanır.

Saldırganlar öncelikle Infrastructure As A Service (IaaS) çözümlerini hedef alır. Bunun için de aslında DDoS saldırılarındaki gibi botnetler kullanılabilir. Sahte API istekleri, HTTP Flood, TCP SYN gibi saldırılar ile etkili bir EDoS saldırısı gerçekleştirilebilir.

EDoS Saldırılarından Nasıl Korunabiliriz?
EDoS saldıırlarından korunmak için aslında 3 temel yaklaşım kullanılır. EDoS saldırıları genelde anomalilere yol açtığı için machine learning tabanlı yaklaşımlar daha ön plandadır.
Support Vector Makineleri (SVM) ve Self Organizing Maps (SOM): Bu makine öğrenimi modelleri EDoS saldırı tespitinde etkili bir yöntemdir ancak genelde yavaşlardır. Bu nedenle gerçek zamanlı trafikte büyük saldırıları işleme konusunda zayıftırlar.
Fully Connected Neural Network (FCNN): Bu deep learning metodu ise Machine Learning algoritmalarından daha iyi performans gösterir çünkü birden fazla nöral katman kullanarak özellikleri daha verimli bir şekilde çıkarabilir. Ancak ne yazık ki FCNN’in bir hafıza kapasitesi olmadığı için ve EDoS saldırıları gerçek zamanlı bir şekilde zaman metriği analizine ihtiyaç duyduğu için doğruluk oranı o kadar da iyi değildi (FCNN’in her event ya da veri paketini ayrı olarak analiz etmesi gerekir).
Recurrent Neural Network (RNN) ve Long Short Term Memory (LSTM): RNN bir dizi event’i analiz edebildiği için EDoS saldırılarını tespit etme konusunda daha başarılıdır. Hatta son olayların hafızasını yakalayabilen ve mevcut bir olayı analiz ederken bunu dikkate alabilen LSTM hücreleri ile donatıldığında daha doğru sonuçlar verir. Ancak ne yazık ki bu yöntem de gerçek zamanlı trafiğe uyarlandığında o kadar da etkili değildir.

Yukarıdaki yöntemler tek başına etkili olmasa da Vinh Quoc Ta ve Minho Park tarafından yapılan son çalışmalarda aşağıdaki gibi bir framework önerilmektedir:
Bir saldırı trafiği dizisindeki bir birimin diğer birimlerle ne kadar güçlü bir korelasyona sahip olduğunu belirleyerek bir birimi tahmin etmek için LSTM attention hücrelerinden yararlanabiliriz.
Yaygın olarak kullanılan Transformer Encoder-Decoder modelinden yararlanarak attention puanı hesaplanılabilir. Ancak EDoS algılama modeli, girişleri paralel olarak hesaplamak için yalnızca bir encoder modül kullanır. Bu, önceki LSTM modellerinin doğruluğunu korurken performansını da önemli ölçüde artırır.
Bir flowdaki diğerlerine kıyasla bir ağ paketinin göreceli (relative) puanlarını göz önünde bulundurabiliriz. Bu yöntem, modelin dizideki önceki birimlerin geçmiş özellikleri hatırlamasına yardımcı olur.
Hesaplama verimliliğini artırmak amacıyla birden fazla özellik için tek puan kullanabiliriz. Başka bir deyişle, model bir paketi analiz ederken işlem süresini kısaltmak için ilgili tüm paketlerdeki puanı kullanır.

