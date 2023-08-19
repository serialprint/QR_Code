import qrcode
import os
import tkinter as tk
from tkinter import filedialog
from tkinter import ttk

class QRCodeUygulamasi:
    def __init__(self, ana_pencere):
        self.ana_pencere = ana_pencere
        self.ana_pencere.title("QR Kodu Oluşturucu")
        self.ana_pencere.geometry("300x250")  # Uygulama boyutunu ayarla
        self.kayit_dizini = os.path.expanduser("~/Masaüstü")
        
# İkon dosyasının yolunu belirleyin ve ana pencereye atayın
        icon_yolu = "C:/Users/Recep UYSAL/Desktop/Yeni klasör/icon.ico"
        self.icon = tk.PhotoImage(file=icon_yolu)
        self.ana_pencere.iconphoto(True, self.icon)


        self.arayuz_olustur()

    def arayuz_olustur(self):
        self.etiket_metin = ttk.Label(self.ana_pencere, text="Metin:")
        self.etiket_metin.pack(anchor=tk.CENTER)  # Metin etiketini ortala

        self.metin_girisi = ttk.Entry(self.ana_pencere)
        self.metin_girisi.pack()

        self.etiket_boyut = ttk.Label(self.ana_pencere, text="Boyut:")
        self.etiket_boyut.pack(anchor=tk.CENTER)  # Boyut etiketini ortala

        self.boyut_secenekleri = tk.StringVar()
        self.boyut_secenekleri.set("normal")
        
        self.boyut_radio_dusuk = ttk.Radiobutton(self.ana_pencere, text="Düşük Kalite", variable=self.boyut_secenekleri, value="dusuk")
        self.boyut_radio_normal = ttk.Radiobutton(self.ana_pencere, text="Normal Kalite", variable=self.boyut_secenekleri, value="normal")
        self.boyut_radio_yuksek = ttk.Radiobutton(self.ana_pencere, text="Yüksek Kalite", variable=self.boyut_secenekleri, value="yuksek")
        
        self.boyut_radio_dusuk.pack(anchor=tk.CENTER)  # Radyo düğmelerini ortala
        self.boyut_radio_normal.pack(anchor=tk.CENTER)
        self.boyut_radio_yuksek.pack(anchor=tk.CENTER)

        self.etiket_kayit_dizini = ttk.Label(self.ana_pencere, text=f"Kayıt Dizini: {self.kayit_dizini}")
        self.etiket_kayit_dizini.pack(anchor=tk.CENTER)  # Kayıt dizini etiketini ortala

        self.kayit_dizini_sec_butonu = ttk.Button(self.ana_pencere, text="Kayıt Dizini Seç", command=self.kayit_dizini_sec)
        self.kayit_dizini_sec_butonu.pack(anchor=tk.CENTER)  # Düğmeyi ortala

        self.kaydet_butonu = ttk.Button(self.ana_pencere, text="QR Kodu Oluştur ve Kaydet", command=self.kaydet)
        self.kaydet_butonu.pack(anchor=tk.CENTER)  # Düğmeyi ortala

        self.bilgi_etiketi = ttk.Label(self.ana_pencere, text="")
        self.bilgi_etiketi.pack(anchor=tk.CENTER)  # Bilgi etiketini ortala

    def kayit_dizini_sec(self):
        self.kayit_dizini = filedialog.askdirectory()
        self.etiket_kayit_dizini.config(text=f"Kayıt Dizini: {self.kayit_dizini}")

    def kaydet(self):
        metin = self.metin_girisi.get()
        boyut_secenekleri = self.boyut_secenekleri.get()

        if boyut_secenekleri == "dusuk":
            boyut = 150
        elif boyut_secenekleri == "normal":
            boyut = 300
        elif boyut_secenekleri == "yuksek":
            boyut = 600

        qr = qrcode.QRCode(
            version=1,
            error_correction=qrcode.constants.ERROR_CORRECT_L,
            box_size=10,  # Boyutu piksel cinsinden ayarla
            border=4,
        )
        qr.add_data(metin)
        qr.make(fit=True)

        qr_goruntu = qr.make_image(fill_color="black", back_color="white")
        
        kayit_yolu = os.path.join(self.kayit_dizini, "qrcode.png")
        qr_goruntu = qr_goruntu.resize((boyut, boyut))  # Boyutu ayarla
        qr_goruntu.save(kayit_yolu)
        
        self.bilgi_etiketi.config(text=f"QR kodu oluşturuldu ve kaydedildi:\n{kayit_yolu}")

if __name__ == "__main__":
    ana_pencere = tk.Tk()
    uygulama = QRCodeUygulamasi(ana_pencere)
    ana_pencere.mainloop()
