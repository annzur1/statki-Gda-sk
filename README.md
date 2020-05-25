#### próba rozwiązania kodu do statków na podstawie klas i list####
import random
import os

class statek:
    ile_masztow = 0
    pola_masztow = []
    pola_styczne = [] #### pola styczne do okrętów, tak żeby nie można było stawiac okrętów stycznie do siebie ####
    zycia = 0
    def ilomasztowiec(self):
        self.ile_masztow = int(input("podaj ilomasztowy okręt stawiasz: "))
    def wyznaczanie_pol (self, kukuryku):
        self.pola_masztow = []
        for i in range(1,self.ile_masztow+1):
            while True:
                pojedyncze_pole =[]
                for i in range(1,3):
                    pojedyncze_pole.append(int(input("podaj współrzędną pola")))
                if pojedyncze_pole in kukuryku:
                    True
                    print("podałeś już nieaktywne pole!")
                else:
                    break
            self.pola_masztow.append(pojedyncze_pole)
            #### tutaj dodajemy przyciski z planszy 10x10 pól w GUI, tak żeby jedna współrzędna była x a druga y ####
    def zycia_statku(self):
        self.zycia = self.ile_masztow
    def wyz_pola_styczne(self):
        self.pola_styczne = self.pola_masztow
        #### dodajmy po każdej współrzędnej nieaktywne pola na których nie można już umieścić statków ####
        pola = self.pola_masztow
        ciag_pol = []
        ciag_pol2 = []
        ####
        k = 0
        if pola[0][0] == pola [1][0]:
            #### sprawdzamy czy statek jest w układzie wertykalnym czy horyzontalnym ####
            for i in pola:
                ciag_pol.append(pola[k][1])
                k+=1
            malo = min(ciag_pol)
            duzo = max(ciag_pol)
            for i in range(pola[0][0] - 1, pola[0][0]+2):
                dodatek = []
                for j in range(malo-1, duzo+2):
                    dodatek.append([i,j])
                ciag_pol2.extend(dodatek)
        elif pola[0][1] == pola[1][1]:
            #### sprawdzamy czy statek jest w układzie wertykalnym czy horyzontalnym ####
            for i in pola:
                ciag_pol.append(pola[k][0])
                k+=1
            malo = min(ciag_pol)
            duzo = max(ciag_pol)
            for i in range(pola[0][1] - 1, pola[0][1]+2):
                dodatek = []
                for j in range(malo-1, duzo+2):
                    dodatek.append([j,i])
                ciag_pol2.extend(dodatek)
        self.pola_styczne = ciag_pol2

#### definiowanie listy dla pól zapełnionych####
kukuryku = []

#### usaewiamy 5 statków: 1 x 5masztów, 1 x 4 maszty, 2 x 3 maszty, 2 x 2 maszty #####
moj_statek5 = statek()
moj_statek4 = statek()
moj_statek3 = statek()
moj_statek3_1 = statek()
moj_statek2 = statek()
moj_statek2_1 = statek()

moj_statek5.ilomasztowiec()
moj_statek5.wyznaczanie_pol(kukuryku)
moj_statek5.wyz_pola_styczne()
kukuryku.extend(moj_statek5.pola_styczne)

moj_statek4.ilomasztowiec()
moj_statek4.wyznaczanie_pol(kukuryku)
moj_statek4.wyz_pola_styczne()
kukuryku.extend(moj_statek4.pola_styczne)

moj_statek3.ilomasztowiec()
moj_statek3.wyznaczanie_pol(kukuryku)
moj_statek3.wyz_pola_styczne()
kukuryku.extend(moj_statek3.pola_styczne)

moj_statek3_1.ilomasztowiec()
moj_statek3_1.wyznaczanie_pol(kukuryku)
moj_statek3_1.wyz_pola_styczne()
kukuryku.extend(moj_statek3_1.pola_styczne)

moj_statek2.ilomasztowiec()
moj_statek2.wyznaczanie_pol(kukuryku)
moj_statek2.wyz_pola_styczne()
kukuryku.extend(moj_statek2.pola_styczne)

moj_statek2_1.ilomasztowiec()
moj_statek2_1.wyznaczanie_pol(kukuryku)
moj_statek2_1.wyz_pola_styczne()
kukuryku.extend(moj_statek2_1.pola_styczne)


#### pokazuje pola statku ####
print(moj_statek5.pola_masztow)
print(moj_statek4.pola_masztow)
print(moj_statek3.pola_masztow)
print(moj_statek3_1.pola_masztow)
print(moj_statek2.pola_masztow)
print(moj_statek2_1.pola_masztow)

##### pokazuje pozcje pól nieaktywnych #####
print(kukuryku)
