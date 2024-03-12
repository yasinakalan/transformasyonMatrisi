import numpy as np

# -------------------------------------------------------------------------------------------------------
# FONKSİYONLAR:

def noktaEkle():
    vektor = np.ones((4, 1))
    for i in range(3):
        nokta = float(input(f"Eklemek istediğiniz noktanın {i+1}. koordinatını giriniz: "))
        vektor[i][0] = nokta
    vektor[-1][0] = 1.0  # Homojen koordinatı ekleme
    return vektor

def olceklemeMatrisi():

    sx = float(input("x ekseni yönündeki ölçekleme değerini giriniz: "))
    sy = float(input("y ekseni yönündeki ölçekleme değerini giriniz: "))
    sz = float(input("z ekseni yönündeki ölçekleme değerini giriniz: "))

    olcekleme = np.array([[sx, 0, 0, 0],
                          [0, sy, 0, 0],
                          [0, 0, sz, 0],
                          [0, 0, 0, 1]])
    return olcekleme

def otelemeMatrisi():
    dx = float(input("x ekseni yönündeki öteleme miktarını giriniz: "))
    dy = float(input("y ekseni yönündeki öteleme miktarını giriniz: "))
    dz = float(input("z ekseni yönündeki öteleme miktarını giriniz: "))

    oteleme = np.array([[1, 0, 0, dx],
                        [0, 1, 0, dy],
                        [0, 0, 1, dz],
                        [0, 0, 0, 1]])
    return oteleme

def rotasyonMatrisi_x():
    alpha = float(input("x ekseni etrafındaki döndürme açısını giriniz: "))
    alpha_radyan = np.radians(alpha)

    rotasyon_x = np.array([[1, 0, 0, 0],
                           [0, np.cos(alpha_radyan), -np.sin(alpha_radyan), 0],
                           [0, np.sin(alpha_radyan), np.cos(alpha_radyan), 0],
                           [0, 0, 0, 1]])
    return rotasyon_x
    
def rotasyonMatrisi_y():
    beta = float(input("y ekseni etrafındaki döndürme açısını giriniz: "))
    beta_radyan = np.radians(beta)

    rotasyon_y = np.array([[np.cos(beta_radyan), 0, np.sin(beta_radyan), 0],
                           [0, 1, 0, 0],
                           [-np.sin(beta_radyan), 0, np.cos(beta_radyan), 0],
                           [0, 0, 0, 1]])
    return rotasyon_y

def rotasyonMatrisi_z():
    tetha = float(input("z ekseni etrafındaki döndürme açısını giriniz: "))
    tetha_radyan = np.radians(tetha)

    rotasyon_z = np.array([[np.cos(tetha_radyan), -np.sin(tetha_radyan), 0, 0],
                           [np.sin(tetha_radyan), np.cos(tetha_radyan), 0, 0],
                           [0, 0, 1, 0],
                           [0, 0, 0, 1]])
    return rotasyon_z

def matrisCarpim(A, B):
    return np.dot(A, B)


# -------------------------------------------------------------------------------------------------------
# İŞLEMLER:

noktaSayisi = int(input("Nokta sayısını giriniz: "))
noktalarKumesi = [noktaEkle() for _ in range(noktaSayisi)]

print("Oluşturulan noktalar kümesi:")
for i, nokta in enumerate(noktalarKumesi, start=1):
    print(f"Nokta {i}:\n{np.array(nokta[:-1]).flatten()}")

print("Oluşturulan noktalar kümesi:", noktalarKumesi)



while True:
    print("""\n
          0-Çıkış
          1-Ölçekleme
          2-Öteleme
          3-x ekseni etrafında döndürme
          4-y ekseni etrafında döndürme
          5-z ekseni etrafında döndürme
          """)
    secim = input("Noktalar Kümesine uygulamak istediğiniz transformasyon tipini seçiniz:")

    if secim == "0":
        print("\nSONUÇ MATRİSİ:")
        for i, nokta in enumerate(noktalarKumesi, start=1):
            print(f"Nokta {i}:\n{np.array(nokta[:-1]).flatten()}")
        break
    elif secim in ["1", "2", "3", "4", "5"]:
        if secim == "1":
            transformasyon = olceklemeMatrisi()
        elif secim == "2":
            transformasyon = otelemeMatrisi()
        elif secim == "3":
            transformasyon = rotasyonMatrisi_x()
        elif secim == "4":
            transformasyon = rotasyonMatrisi_y()
        elif secim == "5":
            transformasyon = rotasyonMatrisi_z()

        print(f"{secim}. transformasyon uygulanıyor...")
        for i, nokta in enumerate(noktalarKumesi):
            noktalarKumesi[i] = matrisCarpim(transformasyon, nokta)

        print("Sonuç:")
        for i, nokta in enumerate(noktalarKumesi, start=1):
            print(f"Nokta {i}:\n{np.array(nokta[:-1]).flatten()}")
    else:
        print("Geçersiz seçim! Lütfen geçerli bir seçim yapın.")
