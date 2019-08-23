 # UYUM NOTASYONU
 
 Sistemin alt-sistemleri arasındaki iletişimi (veri alışverişini) daha kolay anlatabilmek için geliştirdiğimiz notasyondur.
 
1- 
   Alt-sistemler: Bir servis modülü, bir JS sayfası, bir Java nesne, bir fonksiyon olabilir. Dolayısı ile şimdilik belli başlı alt-sistemleri birbirinden ayırmak için bâzı işaretler kullanıyoruz.
  
   Bir servis modülü:  başlı başına bir projedir. Küçük harflerle modül ismi yazılır
   
   Örnek: clientreactchat, gateway, persist, notification.
   
   Bir fonksiyon: Mesela, bir servisten dönen veriyi, Redux Action'ına dönüştüren fonsiyon. 
   
   convertUserInformationToAction()
   
   Bir Java nesnesi: Büyük harfle başlar, sonuna herhangi bir uzantı almaz. Örnek: Transaction
   
   Bir JS sayfası: Örnek: Bir chat kanalına girildiğinde içerik listesinin görüntülendiği sayfa. Örnek: ChannelContentList.js
   

2- Alt sistemin içindeki herhangi bir şeyi göstermek için {} kullanırız.
 
   Örnek: clientreactchat modülündeki, ChannelContentList.js sınıfındaki, componentDidMount() fonksiyonu içerisinde çağrılan fetchData() fonksiyonu: 
    
    clientreactchat{
                  ChannelContentList.js {
                         componentDidMount() {
                                       fetchData()
                      }
                  } 
                  }
  
3- Veri aktarma. Bizim bakış açımızdan; modül, sınıf, sayfa, fonksiyon fark etmeksizin hepsi alt-sistem olduğundan ötürü, hepsinde veri aktarımı için aynı notasyonu kullanacağız.
  
  -> : Çağrı işaretidir.
  -(veri)->: Çağrı içerisinde aynı zamanda bir veri taşınıyorsa, veri iletişimi söz konusudur.
  
  Örnek: transaction nesnesinin bir REST servisi ile, bir altsistemden başka bir altsisteme iletilmesi:
  
   altsistem1 -(transaction)-> altsistem2,
 
 Örnek2: clientreactchat modülünden, gateway modülüne transaction JSON objesi aktarılıyor. Gatewayden, persiste Message<Transaction> objesi aktarılıyor. Persistten notificationa gene Message<Transaction> objesi aktarılıyor.
 
  clientreactchat -(transaction)-> 
                       gateway -(message<transaction>)-> 
                                  persist -(message<transaction>))-> notification.
