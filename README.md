# RKMp3
import self as self
from random import choice

class Mp3Calar():

    def __init__(self, sarkiListesi=[]):
    
        self.suanCalanSarki = " "
        self.ses = 100
        self.sarkiListesi = sarkiListesi
        self.durum = True

    def sesArttır(self):
        pass

    def sesAzalt(self):
        pass

    def sarkiSec(self):
        pass

    def rastgeleSarkiSec(self):
        pass

    def sarkiEkle(self):
        pass

    def sarkiSil(self):
        pass

    def menuGöster(self):
        print("""
                          RÜVEYDA'NIN MP3 ÇALARINA HOŞGELDİNİZ..!
Şarkı listesi : {}
Suanda çalan şarkı : {}
Ses seviyesi : {}

1-Şarkı Seç
2-Ses Arttır
3-Ses Azalt
4-Rastgele Şarkı Seç
5-Şarkı Ekle 
6-Şarkı Sil
7-Kapa
                                  

                                  """.format(self.sarkiListesi, self.suanCalanSarki, self.ses))

    def secim(self):
        sec = int(input("Menüden bir seçim yapınız:"))
        while sec < 1 or sec > 7:
            sec = int(input("Seçtiğiniz değer yanlış,lütfen bir seçim daha yapınız(1-7): "))
        return sec

    def kapa(self):
        self.durum = False

    def calistir(self):
        self.menuGöster()
        secim = self.secim()
        if secim == 1:
            sayac=1
            for sarki in self.sarkiListesi:
                print("{}-{}".format(sayac,sarki))
                sayac+=1
            secilen=int(input("Seçmek istediğiniz şarkı numarasını giriniz :"))
            while secilen<1 or secilen>7:
                secilen = int(input("Seçmek istediğiniz şarkı numarasını(1-7) tekrar giriniz :"))
            self.suanCalanSarki=self.sarkiListesi[secilen-1]
        if secim == 2:
            if self.ses == 100:
                pass
            else:
                self.ses += 10
            print(self.ses)
        if secim == 3:
            if self.ses == 0:
                pass
            else:
                self.ses -= 10

        if secim == 4:
            rasgleSec=choice(self.sarkiListesi)
            self.suanCalanSarki=rasgleSec


        if secim == 5:
            sanatci = input("Sanatçıyı giriniz : ")
            sarki = input("Şarkıyı giriniz : ")
            self.sarkiListesi.append(sanatci + " /" + sarki)
        if secim == 6:
         sayac = 0
         for i in self.sarkiListesi:
            sayac += 1
            print("{}-{}".format(sayac, i))
         sil = int(input("Silinmek istenen şarkı numarasını seçiniz :"))
         self.sarkiListesi.pop(sil - 1)

        if secim == 7:
         self.kapa()


mp3calar = Mp3Calar()

while mp3calar.durum:
    mp3calar.calistir()

print("Program sonlandı.")
