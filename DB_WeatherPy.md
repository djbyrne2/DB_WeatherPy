
# Observations

## 1) Cities located on latitudes near or along the equator experience higher temperatures
## 2) Temperature differences adhere to an inverted U-Shape curve along latitude
## 3) Wind speeds increase the further cities are located away from the equator 


```python
# import dependencies
from citipy import citipy
import seaborn as sns
from config import api_key
import random
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import requests
import json
```


```python
# Create empty list to hold city info
random_city = []
```


```python
# Set sample size n to 500 for n# of API Calls and Counter to 0

n = 500
counter = 0

# Randomly generate latitude and lonigitude by sampling from a uniform distribution 500 times. 
while (counter) < n:
    counter += 1
    # Randomly Sample from Northernmost, Southernmost, Easternmost, and Westernmost longitudes and latitudes.(Round)
    lat = round(np.random.uniform(low=-90.0, high=90.0))
    lng = round(np.random.uniform(low=-180.0, high=180.0))
    
    # Locate nearest city and append to list.
    city = citipy.nearest_city(lat, lng)
    city_name = city.city_name
    
    random_city.append(city_name)
```


```python
#Build Url and set units

base_url = "http://api.openweathermap.org/data/2.5/weather?"
api_key = api_key
units = "imperial"

query_url = base_url + "appid=" + api_key + "&units=" + units + "&q="
```


```python
# Create new empty lists to loop through data 
coordinates_data = []
city_list = []

# Set Loop Count to 0 

count = 0

print(f"Initialize Call to OpenWeather API")

for city in random_city:
    count += 1
    print(f"Locating coordinates/weather data  # {count} for the city of: {city}")  
    
    response = requests.get(query_url + city).json()
    random_cityid = response.get("id")
    
    if response.get("id"):
        print(f"Weather data found for city: {city} {random_cityid}")
        coordinates_data.append(response)
        city_list.append(city)
    elif city in city_list:
        pass
        
              
print(f"API Call Complete. Data Generated")
```

    Initialize Call to OpenWeather API
    Locating coordinates/weather data  # 1 for the city of: vaitape
    Weather data found for city: vaitape 4033077
    Locating coordinates/weather data  # 2 for the city of: longyearbyen
    Weather data found for city: longyearbyen 2729907
    Locating coordinates/weather data  # 3 for the city of: sao filipe
    Weather data found for city: sao filipe 3374210
    Locating coordinates/weather data  # 4 for the city of: jamestown
    Weather data found for city: jamestown 2069194
    Locating coordinates/weather data  # 5 for the city of: provideniya
    Weather data found for city: provideniya 4031574
    Locating coordinates/weather data  # 6 for the city of: amderma
    Locating coordinates/weather data  # 7 for the city of: asau
    Locating coordinates/weather data  # 8 for the city of: bathsheba
    Weather data found for city: bathsheba 3374083
    Locating coordinates/weather data  # 9 for the city of: souillac
    Weather data found for city: souillac 3026644
    Locating coordinates/weather data  # 10 for the city of: shingu
    Weather data found for city: shingu 1847947
    Locating coordinates/weather data  # 11 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 12 for the city of: cherskiy
    Weather data found for city: cherskiy 2126199
    Locating coordinates/weather data  # 13 for the city of: vallenar
    Weather data found for city: vallenar 3868633
    Locating coordinates/weather data  # 14 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 15 for the city of: mihijam
    Weather data found for city: mihijam 1265711
    Locating coordinates/weather data  # 16 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 17 for the city of: port blair
    Weather data found for city: port blair 1259385
    Locating coordinates/weather data  # 18 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 19 for the city of: ancud
    Weather data found for city: ancud 3899695
    Locating coordinates/weather data  # 20 for the city of: skalistyy
    Locating coordinates/weather data  # 21 for the city of: east london
    Weather data found for city: east london 1006984
    Locating coordinates/weather data  # 22 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 23 for the city of: estrela
    Weather data found for city: estrela 3459035
    Locating coordinates/weather data  # 24 for the city of: taolanaro
    Locating coordinates/weather data  # 25 for the city of: brewster
    Weather data found for city: brewster 4931273
    Locating coordinates/weather data  # 26 for the city of: bichura
    Weather data found for city: bichura 2026708
    Locating coordinates/weather data  # 27 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 28 for the city of: lompoc
    Weather data found for city: lompoc 5367788
    Locating coordinates/weather data  # 29 for the city of: bijie
    Weather data found for city: bijie 1816373
    Locating coordinates/weather data  # 30 for the city of: anadyr
    Weather data found for city: anadyr 2127202
    Locating coordinates/weather data  # 31 for the city of: cabo san lucas
    Weather data found for city: cabo san lucas 3985710
    Locating coordinates/weather data  # 32 for the city of: airai
    Weather data found for city: airai 1651810
    Locating coordinates/weather data  # 33 for the city of: longyearbyen
    Weather data found for city: longyearbyen 2729907
    Locating coordinates/weather data  # 34 for the city of: nanyuki
    Weather data found for city: nanyuki 184433
    Locating coordinates/weather data  # 35 for the city of: oriximina
    Weather data found for city: oriximina 3393471
    Locating coordinates/weather data  # 36 for the city of: kuche
    Locating coordinates/weather data  # 37 for the city of: belushya guba
    Locating coordinates/weather data  # 38 for the city of: san cristobal
    Weather data found for city: san cristobal 3652462
    Locating coordinates/weather data  # 39 for the city of: samusu
    Locating coordinates/weather data  # 40 for the city of: marrakesh
    Weather data found for city: marrakesh 2542997
    Locating coordinates/weather data  # 41 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 42 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 43 for the city of: avarua
    Weather data found for city: avarua 4035715
    Locating coordinates/weather data  # 44 for the city of: hithadhoo
    Weather data found for city: hithadhoo 1282256
    Locating coordinates/weather data  # 45 for the city of: yunjinghong
    Locating coordinates/weather data  # 46 for the city of: ostrovnoy
    Weather data found for city: ostrovnoy 556268
    Locating coordinates/weather data  # 47 for the city of: lorengau
    Weather data found for city: lorengau 2092164
    Locating coordinates/weather data  # 48 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 49 for the city of: svetlogorsk
    Weather data found for city: svetlogorsk 584051
    Locating coordinates/weather data  # 50 for the city of: amazar
    Weather data found for city: amazar 2027806
    Locating coordinates/weather data  # 51 for the city of: port moresby
    Weather data found for city: port moresby 2088122
    Locating coordinates/weather data  # 52 for the city of: chokurdakh
    Weather data found for city: chokurdakh 2126123
    Locating coordinates/weather data  # 53 for the city of: hambantota
    Weather data found for city: hambantota 1244926
    Locating coordinates/weather data  # 54 for the city of: bambous virieux
    Weather data found for city: bambous virieux 1106677
    Locating coordinates/weather data  # 55 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 56 for the city of: liverpool
    Weather data found for city: liverpool 2644210
    Locating coordinates/weather data  # 57 for the city of: hasaki
    Weather data found for city: hasaki 2112802
    Locating coordinates/weather data  # 58 for the city of: arraial do cabo
    Weather data found for city: arraial do cabo 3471451
    Locating coordinates/weather data  # 59 for the city of: poum
    Weather data found for city: poum 787487
    Locating coordinates/weather data  # 60 for the city of: newport
    Weather data found for city: newport 2641598
    Locating coordinates/weather data  # 61 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 62 for the city of: ryotsu
    Weather data found for city: ryotsu 1853371
    Locating coordinates/weather data  # 63 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 64 for the city of: lolua
    Locating coordinates/weather data  # 65 for the city of: butaritari
    Weather data found for city: butaritari 2110227
    Locating coordinates/weather data  # 66 for the city of: kodiak
    Weather data found for city: kodiak 4407665
    Locating coordinates/weather data  # 67 for the city of: cayenne
    Weather data found for city: cayenne 3382160
    Locating coordinates/weather data  # 68 for the city of: nikolskoye
    Weather data found for city: nikolskoye 546105
    Locating coordinates/weather data  # 69 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 70 for the city of: mys shmidta
    Locating coordinates/weather data  # 71 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 72 for the city of: wagga wagga
    Weather data found for city: wagga wagga 2145110
    Locating coordinates/weather data  # 73 for the city of: nikolskoye
    Weather data found for city: nikolskoye 546105
    Locating coordinates/weather data  # 74 for the city of: talnakh
    Weather data found for city: talnakh 1490256
    Locating coordinates/weather data  # 75 for the city of: yellowknife
    Weather data found for city: yellowknife 6185377
    Locating coordinates/weather data  # 76 for the city of: nikolskoye
    Weather data found for city: nikolskoye 546105
    Locating coordinates/weather data  # 77 for the city of: cherskiy
    Weather data found for city: cherskiy 2126199
    Locating coordinates/weather data  # 78 for the city of: vila do maio
    Weather data found for city: vila do maio 3374120
    Locating coordinates/weather data  # 79 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 80 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 81 for the city of: port lincoln
    Weather data found for city: port lincoln 2063036
    Locating coordinates/weather data  # 82 for the city of: bagdarin
    Weather data found for city: bagdarin 2027244
    Locating coordinates/weather data  # 83 for the city of: hervey bay
    Weather data found for city: hervey bay 2146219
    Locating coordinates/weather data  # 84 for the city of: bluff
    Weather data found for city: bluff 2175403
    Locating coordinates/weather data  # 85 for the city of: hasaki
    Weather data found for city: hasaki 2112802
    Locating coordinates/weather data  # 86 for the city of: igarka
    Weather data found for city: igarka 1505991
    Locating coordinates/weather data  # 87 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 88 for the city of: saint-philippe
    Weather data found for city: saint-philippe 6138908
    Locating coordinates/weather data  # 89 for the city of: katsuura
    Weather data found for city: katsuura 1865309
    Locating coordinates/weather data  # 90 for the city of: taolanaro
    Locating coordinates/weather data  # 91 for the city of: saskylakh
    Weather data found for city: saskylakh 2017155
    Locating coordinates/weather data  # 92 for the city of: narsaq
    Weather data found for city: narsaq 3421719
    Locating coordinates/weather data  # 93 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 94 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 95 for the city of: mudyuga
    Locating coordinates/weather data  # 96 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 97 for the city of: butaritari
    Weather data found for city: butaritari 2110227
    Locating coordinates/weather data  # 98 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 99 for the city of: huilong
    Weather data found for city: huilong 1795424
    Locating coordinates/weather data  # 100 for the city of: terenos
    Weather data found for city: terenos 3446619
    Locating coordinates/weather data  # 101 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 102 for the city of: coahuayana
    Weather data found for city: coahuayana 3981460
    Locating coordinates/weather data  # 103 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 104 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 105 for the city of: mar del plata
    Weather data found for city: mar del plata 3863379
    Locating coordinates/weather data  # 106 for the city of: arraial do cabo
    Weather data found for city: arraial do cabo 3471451
    Locating coordinates/weather data  # 107 for the city of: khatanga
    Weather data found for city: khatanga 2022572
    Locating coordinates/weather data  # 108 for the city of: stadskanaal
    Weather data found for city: stadskanaal 2746860
    Locating coordinates/weather data  # 109 for the city of: elizabeth city
    Weather data found for city: elizabeth city 4465088
    Locating coordinates/weather data  # 110 for the city of: yulara
    Weather data found for city: yulara 6355222
    Locating coordinates/weather data  # 111 for the city of: tura
    Weather data found for city: tura 1254046
    Locating coordinates/weather data  # 112 for the city of: mentougou
    Weather data found for city: mentougou 1800657
    Locating coordinates/weather data  # 113 for the city of: tuktoyaktuk
    Weather data found for city: tuktoyaktuk 6170031
    Locating coordinates/weather data  # 114 for the city of: kamenskoye
    Locating coordinates/weather data  # 115 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 116 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 117 for the city of: new norfolk
    Weather data found for city: new norfolk 2155415
    Locating coordinates/weather data  # 118 for the city of: sokoni
    Weather data found for city: sokoni 901344
    Locating coordinates/weather data  # 119 for the city of: ancud
    Weather data found for city: ancud 3899695
    Locating coordinates/weather data  # 120 for the city of: bethel
    Weather data found for city: bethel 5880568
    Locating coordinates/weather data  # 121 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 122 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 123 for the city of: lavrentiya
    Weather data found for city: lavrentiya 4031637
    Locating coordinates/weather data  # 124 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 125 for the city of: ravne
    Weather data found for city: ravne 3201984
    Locating coordinates/weather data  # 126 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 127 for the city of: mar del plata
    Weather data found for city: mar del plata 3863379
    Locating coordinates/weather data  # 128 for the city of: waipawa
    Weather data found for city: waipawa 2185329
    Locating coordinates/weather data  # 129 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 130 for the city of: taolanaro
    Locating coordinates/weather data  # 131 for the city of: khatanga
    Weather data found for city: khatanga 2022572
    Locating coordinates/weather data  # 132 for the city of: carnarvon
    Weather data found for city: carnarvon 1014034
    Locating coordinates/weather data  # 133 for the city of: barrow
    Weather data found for city: barrow 3833859
    Locating coordinates/weather data  # 134 for the city of: maiduguri
    Weather data found for city: maiduguri 2331447
    Locating coordinates/weather data  # 135 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 136 for the city of: arraial do cabo
    Weather data found for city: arraial do cabo 3471451
    Locating coordinates/weather data  # 137 for the city of: ijaki
    Locating coordinates/weather data  # 138 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 139 for the city of: sao joao da barra
    Weather data found for city: sao joao da barra 3448903
    Locating coordinates/weather data  # 140 for the city of: cape town
    Weather data found for city: cape town 3369157
    Locating coordinates/weather data  # 141 for the city of: saldanha
    Weather data found for city: saldanha 2737599
    Locating coordinates/weather data  # 142 for the city of: east london
    Weather data found for city: east london 1006984
    Locating coordinates/weather data  # 143 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 144 for the city of: ngunguru
    Weather data found for city: ngunguru 2186111
    Locating coordinates/weather data  # 145 for the city of: salalah
    Weather data found for city: salalah 286621
    Locating coordinates/weather data  # 146 for the city of: bisert
    Weather data found for city: bisert 576260
    Locating coordinates/weather data  # 147 for the city of: san francisco
    Weather data found for city: san francisco 5391959
    Locating coordinates/weather data  # 148 for the city of: tres arroyos
    Weather data found for city: tres arroyos 3833859
    Locating coordinates/weather data  # 149 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 150 for the city of: biak
    Weather data found for city: biak 1637001
    Locating coordinates/weather data  # 151 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 152 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 153 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 154 for the city of: qaanaaq
    Weather data found for city: qaanaaq 3831208
    Locating coordinates/weather data  # 155 for the city of: mys shmidta
    Locating coordinates/weather data  # 156 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 157 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 158 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 159 for the city of: hithadhoo
    Weather data found for city: hithadhoo 1282256
    Locating coordinates/weather data  # 160 for the city of: samarai
    Weather data found for city: samarai 2132606
    Locating coordinates/weather data  # 161 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 162 for the city of: nguiu
    Locating coordinates/weather data  # 163 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 164 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 165 for the city of: cape town
    Weather data found for city: cape town 3369157
    Locating coordinates/weather data  # 166 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 167 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 168 for the city of: bluff
    Weather data found for city: bluff 2175403
    Locating coordinates/weather data  # 169 for the city of: porbandar
    Weather data found for city: porbandar 1259395
    Locating coordinates/weather data  # 170 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 171 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 172 for the city of: illoqqortoormiut
    Locating coordinates/weather data  # 173 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 174 for the city of: gizo
    Weather data found for city: gizo 6693679
    Locating coordinates/weather data  # 175 for the city of: arlit
    Weather data found for city: arlit 2447513
    Locating coordinates/weather data  # 176 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 177 for the city of: vendome
    Weather data found for city: vendome 5686153
    Locating coordinates/weather data  # 178 for the city of: severo-kurilsk
    Weather data found for city: severo-kurilsk 2121385
    Locating coordinates/weather data  # 179 for the city of: norman wells
    Weather data found for city: norman wells 6089245
    Locating coordinates/weather data  # 180 for the city of: nelson bay
    Weather data found for city: nelson bay 2155562
    Locating coordinates/weather data  # 181 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 182 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 183 for the city of: yellowknife
    Weather data found for city: yellowknife 6185377
    Locating coordinates/weather data  # 184 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 185 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 186 for the city of: bilma
    Weather data found for city: bilma 2446796
    Locating coordinates/weather data  # 187 for the city of: portland
    Weather data found for city: portland 5746545
    Locating coordinates/weather data  # 188 for the city of: nadym
    Weather data found for city: nadym 1498087
    Locating coordinates/weather data  # 189 for the city of: lushunkou
    Locating coordinates/weather data  # 190 for the city of: salalah
    Weather data found for city: salalah 286621
    Locating coordinates/weather data  # 191 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 192 for the city of: mecca
    Weather data found for city: mecca 104515
    Locating coordinates/weather data  # 193 for the city of: butaritari
    Weather data found for city: butaritari 2110227
    Locating coordinates/weather data  # 194 for the city of: hithadhoo
    Weather data found for city: hithadhoo 1282256
    Locating coordinates/weather data  # 195 for the city of: najran
    Weather data found for city: najran 103630
    Locating coordinates/weather data  # 196 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 197 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 198 for the city of: bluff
    Weather data found for city: bluff 2175403
    Locating coordinates/weather data  # 199 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 200 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 201 for the city of: tabialan
    Locating coordinates/weather data  # 202 for the city of: puerto baquerizo moreno
    Weather data found for city: puerto baquerizo moreno 3652758
    Locating coordinates/weather data  # 203 for the city of: barrow
    Weather data found for city: barrow 3833859
    Locating coordinates/weather data  # 204 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 205 for the city of: alta floresta
    Weather data found for city: alta floresta 6316343
    Locating coordinates/weather data  # 206 for the city of: vila do maio
    Weather data found for city: vila do maio 3374120
    Locating coordinates/weather data  # 207 for the city of: itarema
    Weather data found for city: itarema 3393692
    Locating coordinates/weather data  # 208 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 209 for the city of: tasbuget
    Locating coordinates/weather data  # 210 for the city of: ambanja
    Weather data found for city: ambanja 1083724
    Locating coordinates/weather data  # 211 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 212 for the city of: sinnamary
    Weather data found for city: sinnamary 3380290
    Locating coordinates/weather data  # 213 for the city of: maykor
    Weather data found for city: maykor 528288
    Locating coordinates/weather data  # 214 for the city of: longyearbyen
    Weather data found for city: longyearbyen 2729907
    Locating coordinates/weather data  # 215 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 216 for the city of: aykhal
    Weather data found for city: aykhal 2027296
    Locating coordinates/weather data  # 217 for the city of: ngaoundere
    Weather data found for city: ngaoundere 2224827
    Locating coordinates/weather data  # 218 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 219 for the city of: ziro
    Weather data found for city: ziro 1252668
    Locating coordinates/weather data  # 220 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 221 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 222 for the city of: kaniama
    Weather data found for city: kaniama 214389
    Locating coordinates/weather data  # 223 for the city of: san patricio
    Weather data found for city: san patricio 3437029
    Locating coordinates/weather data  # 224 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 225 for the city of: mysliborz
    Weather data found for city: mysliborz 3091253
    Locating coordinates/weather data  # 226 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 227 for the city of: jalu
    Weather data found for city: jalu 86049
    Locating coordinates/weather data  # 228 for the city of: kavieng
    Weather data found for city: kavieng 2094342
    Locating coordinates/weather data  # 229 for the city of: mortka
    Weather data found for city: mortka 1498402
    Locating coordinates/weather data  # 230 for the city of: nizamabad
    Weather data found for city: nizamabad 1261258
    Locating coordinates/weather data  # 231 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 232 for the city of: sentyabrskiy
    Locating coordinates/weather data  # 233 for the city of: saint-malo
    Weather data found for city: saint-malo 2978640
    Locating coordinates/weather data  # 234 for the city of: tasiilaq
    Weather data found for city: tasiilaq 3424607
    Locating coordinates/weather data  # 235 for the city of: hengshan
    Weather data found for city: hengshan 1799967
    Locating coordinates/weather data  # 236 for the city of: grand river south east
    Locating coordinates/weather data  # 237 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 238 for the city of: olinda
    Weather data found for city: olinda 3650121
    Locating coordinates/weather data  # 239 for the city of: shelburne
    Weather data found for city: shelburne 6145890
    Locating coordinates/weather data  # 240 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 241 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 242 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 243 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 244 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 245 for the city of: mackenzie
    Weather data found for city: mackenzie 6063191
    Locating coordinates/weather data  # 246 for the city of: codrington
    Weather data found for city: codrington 2160063
    Locating coordinates/weather data  # 247 for the city of: fairbanks
    Weather data found for city: fairbanks 5861897
    Locating coordinates/weather data  # 248 for the city of: cabo san lucas
    Weather data found for city: cabo san lucas 3985710
    Locating coordinates/weather data  # 249 for the city of: mar del plata
    Weather data found for city: mar del plata 3863379
    Locating coordinates/weather data  # 250 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 251 for the city of: dalvik
    Weather data found for city: dalvik 2702977
    Locating coordinates/weather data  # 252 for the city of: padang
    Weather data found for city: padang 1633419
    Locating coordinates/weather data  # 253 for the city of: haimen
    Weather data found for city: haimen 1801200
    Locating coordinates/weather data  # 254 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 255 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 256 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 257 for the city of: qaanaaq
    Weather data found for city: qaanaaq 3831208
    Locating coordinates/weather data  # 258 for the city of: isangel
    Weather data found for city: isangel 2136825
    Locating coordinates/weather data  # 259 for the city of: nizhneyansk
    Locating coordinates/weather data  # 260 for the city of: ponta do sol
    Weather data found for city: ponta do sol 3453439
    Locating coordinates/weather data  # 261 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 262 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 263 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 264 for the city of: hit
    Weather data found for city: hit 95788
    Locating coordinates/weather data  # 265 for the city of: toucheng
    Weather data found for city: toucheng 1674199
    Locating coordinates/weather data  # 266 for the city of: pont-a-mousson
    Weather data found for city: pont-a-mousson 2986306
    Locating coordinates/weather data  # 267 for the city of: dunedin
    Weather data found for city: dunedin 2191562
    Locating coordinates/weather data  # 268 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 269 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 270 for the city of: pevek
    Weather data found for city: pevek 2122090
    Locating coordinates/weather data  # 271 for the city of: vestmannaeyjar
    Weather data found for city: vestmannaeyjar 3412093
    Locating coordinates/weather data  # 272 for the city of: owando
    Weather data found for city: owando 2255542
    Locating coordinates/weather data  # 273 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 274 for the city of: port alfred
    Weather data found for city: port alfred 964432
    Locating coordinates/weather data  # 275 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 276 for the city of: kigoma
    Weather data found for city: kigoma 157738
    Locating coordinates/weather data  # 277 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 278 for the city of: wanaka
    Weather data found for city: wanaka 2184707
    Locating coordinates/weather data  # 279 for the city of: port lincoln
    Weather data found for city: port lincoln 2063036
    Locating coordinates/weather data  # 280 for the city of: padang
    Weather data found for city: padang 1633419
    Locating coordinates/weather data  # 281 for the city of: saskylakh
    Weather data found for city: saskylakh 2017155
    Locating coordinates/weather data  # 282 for the city of: louisbourg
    Locating coordinates/weather data  # 283 for the city of: cockburn town
    Weather data found for city: cockburn town 3576994
    Locating coordinates/weather data  # 284 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 285 for the city of: kavaratti
    Weather data found for city: kavaratti 1267390
    Locating coordinates/weather data  # 286 for the city of: shingu
    Weather data found for city: shingu 1847947
    Locating coordinates/weather data  # 287 for the city of: katsuura
    Weather data found for city: katsuura 1865309
    Locating coordinates/weather data  # 288 for the city of: avera
    Weather data found for city: avera 4231997
    Locating coordinates/weather data  # 289 for the city of: chuy
    Weather data found for city: chuy 3443061
    Locating coordinates/weather data  # 290 for the city of: mahebourg
    Weather data found for city: mahebourg 934322
    Locating coordinates/weather data  # 291 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 292 for the city of: seoul
    Weather data found for city: seoul 1835848
    Locating coordinates/weather data  # 293 for the city of: port-gentil
    Weather data found for city: port-gentil 2396518
    Locating coordinates/weather data  # 294 for the city of: neepawa
    Weather data found for city: neepawa 6086673
    Locating coordinates/weather data  # 295 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 296 for the city of: canutama
    Weather data found for city: canutama 3664716
    Locating coordinates/weather data  # 297 for the city of: tsihombe
    Locating coordinates/weather data  # 298 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 299 for the city of: usinsk
    Weather data found for city: usinsk 863061
    Locating coordinates/weather data  # 300 for the city of: san andres
    Weather data found for city: san andres 1690438
    Locating coordinates/weather data  # 301 for the city of: mar del plata
    Weather data found for city: mar del plata 3863379
    Locating coordinates/weather data  # 302 for the city of: caravelas
    Weather data found for city: caravelas 3466980
    Locating coordinates/weather data  # 303 for the city of: victoria
    Weather data found for city: victoria 1733782
    Locating coordinates/weather data  # 304 for the city of: dzaoudzi
    Weather data found for city: dzaoudzi 921900
    Locating coordinates/weather data  # 305 for the city of: nanortalik
    Weather data found for city: nanortalik 3421765
    Locating coordinates/weather data  # 306 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 307 for the city of: new norfolk
    Weather data found for city: new norfolk 2155415
    Locating coordinates/weather data  # 308 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 309 for the city of: hailar
    Weather data found for city: hailar 2037078
    Locating coordinates/weather data  # 310 for the city of: tuktoyaktuk
    Weather data found for city: tuktoyaktuk 6170031
    Locating coordinates/weather data  # 311 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 312 for the city of: north platte
    Weather data found for city: north platte 5697939
    Locating coordinates/weather data  # 313 for the city of: cherskiy
    Weather data found for city: cherskiy 2126199
    Locating coordinates/weather data  # 314 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 315 for the city of: itarema
    Weather data found for city: itarema 3393692
    Locating coordinates/weather data  # 316 for the city of: hofn
    Weather data found for city: hofn 2630299
    Locating coordinates/weather data  # 317 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 318 for the city of: saint-philippe
    Weather data found for city: saint-philippe 6138908
    Locating coordinates/weather data  # 319 for the city of: sainte-suzanne
    Weather data found for city: sainte-suzanne 6429981
    Locating coordinates/weather data  # 320 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 321 for the city of: rockland
    Weather data found for city: rockland 4948924
    Locating coordinates/weather data  # 322 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 323 for the city of: victoria
    Weather data found for city: victoria 1733782
    Locating coordinates/weather data  # 324 for the city of: fatehpur
    Weather data found for city: fatehpur 1179305
    Locating coordinates/weather data  # 325 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 326 for the city of: ribeira grande
    Weather data found for city: ribeira grande 3372707
    Locating coordinates/weather data  # 327 for the city of: vilyuysk
    Weather data found for city: vilyuysk 2013392
    Locating coordinates/weather data  # 328 for the city of: belushya guba
    Locating coordinates/weather data  # 329 for the city of: san quintin
    Weather data found for city: san quintin 1688687
    Locating coordinates/weather data  # 330 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 331 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 332 for the city of: mataura
    Weather data found for city: mataura 6201424
    Locating coordinates/weather data  # 333 for the city of: grand-lahou
    Weather data found for city: grand-lahou 2288105
    Locating coordinates/weather data  # 334 for the city of: carnarvon
    Weather data found for city: carnarvon 1014034
    Locating coordinates/weather data  # 335 for the city of: kahului
    Weather data found for city: kahului 5847411
    Locating coordinates/weather data  # 336 for the city of: tiksi
    Weather data found for city: tiksi 2015306
    Locating coordinates/weather data  # 337 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 338 for the city of: esperance
    Weather data found for city: esperance 3573739
    Locating coordinates/weather data  # 339 for the city of: narsaq
    Weather data found for city: narsaq 3421719
    Locating coordinates/weather data  # 340 for the city of: plouzane
    Weather data found for city: plouzane 2986626
    Locating coordinates/weather data  # 341 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 342 for the city of: najran
    Weather data found for city: najran 103630
    Locating coordinates/weather data  # 343 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 344 for the city of: eenhana
    Weather data found for city: eenhana 3357804
    Locating coordinates/weather data  # 345 for the city of: octeville
    Weather data found for city: octeville 2989755
    Locating coordinates/weather data  # 346 for the city of: cape town
    Weather data found for city: cape town 3369157
    Locating coordinates/weather data  # 347 for the city of: seoul
    Weather data found for city: seoul 1835848
    Locating coordinates/weather data  # 348 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 349 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 350 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 351 for the city of: huilong
    Weather data found for city: huilong 1795424
    Locating coordinates/weather data  # 352 for the city of: yumen
    Weather data found for city: yumen 1528998
    Locating coordinates/weather data  # 353 for the city of: sao jose da coroa grande
    Weather data found for city: sao jose da coroa grande 3388456
    Locating coordinates/weather data  # 354 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 355 for the city of: celestun
    Weather data found for city: celestun 3531368
    Locating coordinates/weather data  # 356 for the city of: springbok
    Weather data found for city: springbok 3361142
    Locating coordinates/weather data  # 357 for the city of: kieta
    Weather data found for city: kieta 2094027
    Locating coordinates/weather data  # 358 for the city of: saleaula
    Locating coordinates/weather data  # 359 for the city of: samarai
    Weather data found for city: samarai 2132606
    Locating coordinates/weather data  # 360 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 361 for the city of: san quintin
    Weather data found for city: san quintin 1688687
    Locating coordinates/weather data  # 362 for the city of: airai
    Weather data found for city: airai 1651810
    Locating coordinates/weather data  # 363 for the city of: taolanaro
    Locating coordinates/weather data  # 364 for the city of: kodiak
    Weather data found for city: kodiak 4407665
    Locating coordinates/weather data  # 365 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 366 for the city of: taltal
    Weather data found for city: taltal 3870243
    Locating coordinates/weather data  # 367 for the city of: sao filipe
    Weather data found for city: sao filipe 3374210
    Locating coordinates/weather data  # 368 for the city of: upernavik
    Weather data found for city: upernavik 3418910
    Locating coordinates/weather data  # 369 for the city of: coquimbo
    Weather data found for city: coquimbo 3893629
    Locating coordinates/weather data  # 370 for the city of: bredasdorp
    Weather data found for city: bredasdorp 1015776
    Locating coordinates/weather data  # 371 for the city of: sikonge
    Weather data found for city: sikonge 149929
    Locating coordinates/weather data  # 372 for the city of: luderitz
    Weather data found for city: luderitz 3355672
    Locating coordinates/weather data  # 373 for the city of: atikokan
    Weather data found for city: atikokan 5888001
    Locating coordinates/weather data  # 374 for the city of: merrill
    Weather data found for city: merrill 5572979
    Locating coordinates/weather data  # 375 for the city of: ancud
    Weather data found for city: ancud 3899695
    Locating coordinates/weather data  # 376 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 377 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 378 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 379 for the city of: mahebourg
    Weather data found for city: mahebourg 934322
    Locating coordinates/weather data  # 380 for the city of: arraial do cabo
    Weather data found for city: arraial do cabo 3471451
    Locating coordinates/weather data  # 381 for the city of: barrow
    Weather data found for city: barrow 3833859
    Locating coordinates/weather data  # 382 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 383 for the city of: barrow
    Weather data found for city: barrow 3833859
    Locating coordinates/weather data  # 384 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 385 for the city of: dondo
    Weather data found for city: dondo 1024696
    Locating coordinates/weather data  # 386 for the city of: bonthe
    Weather data found for city: bonthe 2409914
    Locating coordinates/weather data  # 387 for the city of: arkansas city
    Weather data found for city: arkansas city 4267661
    Locating coordinates/weather data  # 388 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 389 for the city of: mitu
    Weather data found for city: mitu 117392
    Locating coordinates/weather data  # 390 for the city of: nouakchott
    Weather data found for city: nouakchott 2377450
    Locating coordinates/weather data  # 391 for the city of: lebu
    Weather data found for city: lebu 344979
    Locating coordinates/weather data  # 392 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 393 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 394 for the city of: punta arenas
    Weather data found for city: punta arenas 3874787
    Locating coordinates/weather data  # 395 for the city of: richards bay
    Weather data found for city: richards bay 962367
    Locating coordinates/weather data  # 396 for the city of: kodiak
    Weather data found for city: kodiak 4407665
    Locating coordinates/weather data  # 397 for the city of: meulaboh
    Weather data found for city: meulaboh 1214488
    Locating coordinates/weather data  # 398 for the city of: qaanaaq
    Weather data found for city: qaanaaq 3831208
    Locating coordinates/weather data  # 399 for the city of: severo-kurilsk
    Weather data found for city: severo-kurilsk 2121385
    Locating coordinates/weather data  # 400 for the city of: illoqqortoormiut
    Locating coordinates/weather data  # 401 for the city of: atuona
    Weather data found for city: atuona 4020109
    Locating coordinates/weather data  # 402 for the city of: cape town
    Weather data found for city: cape town 3369157
    Locating coordinates/weather data  # 403 for the city of: port elizabeth
    Weather data found for city: port elizabeth 4501427
    Locating coordinates/weather data  # 404 for the city of: satitoa
    Locating coordinates/weather data  # 405 for the city of: novikovo
    Weather data found for city: novikovo 712587
    Locating coordinates/weather data  # 406 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 407 for the city of: calafat
    Weather data found for city: calafat 683034
    Locating coordinates/weather data  # 408 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 409 for the city of: rungata
    Locating coordinates/weather data  # 410 for the city of: jamestown
    Weather data found for city: jamestown 2069194
    Locating coordinates/weather data  # 411 for the city of: solenzo
    Weather data found for city: solenzo 2597250
    Locating coordinates/weather data  # 412 for the city of: kirakira
    Weather data found for city: kirakira 2178753
    Locating coordinates/weather data  # 413 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 414 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 415 for the city of: yellowknife
    Weather data found for city: yellowknife 6185377
    Locating coordinates/weather data  # 416 for the city of: sentyabrskiy
    Locating coordinates/weather data  # 417 for the city of: hofn
    Weather data found for city: hofn 2630299
    Locating coordinates/weather data  # 418 for the city of: bluff
    Weather data found for city: bluff 2175403
    Locating coordinates/weather data  # 419 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 420 for the city of: vaini
    Weather data found for city: vaini 1273574
    Locating coordinates/weather data  # 421 for the city of: lawrenceburg
    Weather data found for city: lawrenceburg 4635849
    Locating coordinates/weather data  # 422 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 423 for the city of: lahad datu
    Weather data found for city: lahad datu 1733953
    Locating coordinates/weather data  # 424 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 425 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 426 for the city of: busselton
    Weather data found for city: busselton 2075265
    Locating coordinates/weather data  # 427 for the city of: kapaa
    Weather data found for city: kapaa 5848280
    Locating coordinates/weather data  # 428 for the city of: puerto ayora
    Weather data found for city: puerto ayora 3652764
    Locating coordinates/weather data  # 429 for the city of: cidreira
    Weather data found for city: cidreira 3466165
    Locating coordinates/weather data  # 430 for the city of: gravatai
    Weather data found for city: gravatai 3462089
    Locating coordinates/weather data  # 431 for the city of: hokitika
    Weather data found for city: hokitika 2206894
    Locating coordinates/weather data  # 432 for the city of: bonavista
    Weather data found for city: bonavista 5905393
    Locating coordinates/weather data  # 433 for the city of: cao bang
    Weather data found for city: cao bang 1586185
    Locating coordinates/weather data  # 434 for the city of: tasiilaq
    Weather data found for city: tasiilaq 3424607
    Locating coordinates/weather data  # 435 for the city of: honningsvag
    Weather data found for city: honningsvag 779554
    Locating coordinates/weather data  # 436 for the city of: chifeng
    Weather data found for city: chifeng 2038067
    Locating coordinates/weather data  # 437 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 438 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 439 for the city of: illoqqortoormiut
    Locating coordinates/weather data  # 440 for the city of: cabo san lucas
    Weather data found for city: cabo san lucas 3985710
    Locating coordinates/weather data  # 441 for the city of: hermanus
    Weather data found for city: hermanus 3366880
    Locating coordinates/weather data  # 442 for the city of: aranos
    Weather data found for city: aranos 3358666
    Locating coordinates/weather data  # 443 for the city of: asau
    Locating coordinates/weather data  # 444 for the city of: sisimiut
    Weather data found for city: sisimiut 3419842
    Locating coordinates/weather data  # 445 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 446 for the city of: lokosovo
    Weather data found for city: lokosovo 1500399
    Locating coordinates/weather data  # 447 for the city of: naze
    Weather data found for city: naze 2337542
    Locating coordinates/weather data  # 448 for the city of: port alfred
    Weather data found for city: port alfred 964432
    Locating coordinates/weather data  # 449 for the city of: puerto ayora
    Weather data found for city: puerto ayora 3652764
    Locating coordinates/weather data  # 450 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 451 for the city of: bambous virieux
    Weather data found for city: bambous virieux 1106677
    Locating coordinates/weather data  # 452 for the city of: hilo
    Weather data found for city: hilo 5855927
    Locating coordinates/weather data  # 453 for the city of: talnakh
    Weather data found for city: talnakh 1490256
    Locating coordinates/weather data  # 454 for the city of: hirara
    Weather data found for city: hirara 1862505
    Locating coordinates/weather data  # 455 for the city of: castro
    Weather data found for city: castro 3896218
    Locating coordinates/weather data  # 456 for the city of: mkushi
    Weather data found for city: mkushi 906221
    Locating coordinates/weather data  # 457 for the city of: saint-philippe
    Weather data found for city: saint-philippe 6138908
    Locating coordinates/weather data  # 458 for the city of: port alfred
    Weather data found for city: port alfred 964432
    Locating coordinates/weather data  # 459 for the city of: tazovskiy
    Weather data found for city: tazovskiy 1489853
    Locating coordinates/weather data  # 460 for the city of: olutanga
    Weather data found for city: olutanga 1697155
    Locating coordinates/weather data  # 461 for the city of: poli
    Weather data found for city: poli 2222539
    Locating coordinates/weather data  # 462 for the city of: ponta do sol
    Weather data found for city: ponta do sol 3453439
    Locating coordinates/weather data  # 463 for the city of: carnarvon
    Weather data found for city: carnarvon 1014034
    Locating coordinates/weather data  # 464 for the city of: puerto ayora
    Weather data found for city: puerto ayora 3652764
    Locating coordinates/weather data  # 465 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 466 for the city of: bambous virieux
    Weather data found for city: bambous virieux 1106677
    Locating coordinates/weather data  # 467 for the city of: karamay
    Locating coordinates/weather data  # 468 for the city of: meulaboh
    Weather data found for city: meulaboh 1214488
    Locating coordinates/weather data  # 469 for the city of: russell
    Weather data found for city: russell 3844421
    Locating coordinates/weather data  # 470 for the city of: kodiak
    Weather data found for city: kodiak 4407665
    Locating coordinates/weather data  # 471 for the city of: chokurdakh
    Weather data found for city: chokurdakh 2126123
    Locating coordinates/weather data  # 472 for the city of: cape town
    Weather data found for city: cape town 3369157
    Locating coordinates/weather data  # 473 for the city of: kodiak
    Weather data found for city: kodiak 4407665
    Locating coordinates/weather data  # 474 for the city of: ushuaia
    Weather data found for city: ushuaia 3833367
    Locating coordinates/weather data  # 475 for the city of: san felipe
    Weather data found for city: san felipe 3872255
    Locating coordinates/weather data  # 476 for the city of: hithadhoo
    Weather data found for city: hithadhoo 1282256
    Locating coordinates/weather data  # 477 for the city of: chokurdakh
    Weather data found for city: chokurdakh 2126123
    Locating coordinates/weather data  # 478 for the city of: dikson
    Weather data found for city: dikson 1507390
    Locating coordinates/weather data  # 479 for the city of: port alfred
    Weather data found for city: port alfred 964432
    Locating coordinates/weather data  # 480 for the city of: avera
    Weather data found for city: avera 4231997
    Locating coordinates/weather data  # 481 for the city of: antofagasta
    Weather data found for city: antofagasta 3899539
    Locating coordinates/weather data  # 482 for the city of: tumannyy
    Locating coordinates/weather data  # 483 for the city of: the valley
    Weather data found for city: the valley 3573374
    Locating coordinates/weather data  # 484 for the city of: taolanaro
    Locating coordinates/weather data  # 485 for the city of: arraial do cabo
    Weather data found for city: arraial do cabo 3471451
    Locating coordinates/weather data  # 486 for the city of: santa margherita ligure
    Weather data found for city: santa margherita ligure 3167595
    Locating coordinates/weather data  # 487 for the city of: saleaula
    Locating coordinates/weather data  # 488 for the city of: rikitea
    Weather data found for city: rikitea 4030556
    Locating coordinates/weather data  # 489 for the city of: albany
    Weather data found for city: albany 5106834
    Locating coordinates/weather data  # 490 for the city of: merauke
    Weather data found for city: merauke 2082539
    Locating coordinates/weather data  # 491 for the city of: sola
    Weather data found for city: sola 643453
    Locating coordinates/weather data  # 492 for the city of: hobart
    Weather data found for city: hobart 2163355
    Locating coordinates/weather data  # 493 for the city of: elban
    Weather data found for city: elban 2024449
    Locating coordinates/weather data  # 494 for the city of: cacequi
    Weather data found for city: cacequi 3468553
    Locating coordinates/weather data  # 495 for the city of: port elizabeth
    Weather data found for city: port elizabeth 4501427
    Locating coordinates/weather data  # 496 for the city of: lebu
    Weather data found for city: lebu 344979
    Locating coordinates/weather data  # 497 for the city of: herat
    Weather data found for city: herat 1140026
    Locating coordinates/weather data  # 498 for the city of: mys shmidta
    Locating coordinates/weather data  # 499 for the city of: illoqqortoormiut
    Locating coordinates/weather data  # 500 for the city of: mamallapuram
    Weather data found for city: mamallapuram 1263997
    API Call Complete. Data Generated



```python
#Use List comprehensions to extract relevant data from API calls
country =[weather_data.get("sys").get("country") for weather_data in coordinates_data]
lat = [weather_data.get("coord").get("lat") for weather_data in coordinates_data]
lng = [weather_data.get("coord").get("lon") for weather_data in coordinates_data]
temp = [weather_data.get("main").get("temp") for weather_data in coordinates_data]
humidity = [weather_data.get("main").get("humidity") for weather_data in coordinates_data]
cloudiness =[weather_data.get("clouds").get("all") for weather_data in coordinates_data]
wind = [weather_data.get("wind").get("speed") for weather_data in coordinates_data]


# Create Data Frame with Open Weather API data
weather_df = pd.DataFrame({"City":city_list,
                            "Country":country,
                            "Latitude":lat,
                            "Longitude":lng,
                            "Temperature":temp,
                            "Humidity %":humidity,
                            "Cloudiness %":cloudiness,
                            "Wind Speed (mph)":wind})

# Rearrange Column Order
weather_df = weather_df[["Country","City","Latitude","Longitude","Temperature","Humidity %","Cloudiness %","Wind Speed (mph)"]]
weather_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Country</th>
      <th>City</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Temperature</th>
      <th>Humidity %</th>
      <th>Cloudiness %</th>
      <th>Wind Speed (mph)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NO</td>
      <td>longyearbyen</td>
      <td>78.22</td>
      <td>15.63</td>
      <td>37.40</td>
      <td>93</td>
      <td>90</td>
      <td>8.05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AR</td>
      <td>ushuaia</td>
      <td>-54.81</td>
      <td>-68.31</td>
      <td>47.41</td>
      <td>61</td>
      <td>75</td>
      <td>24.16</td>
    </tr>
    <tr>
      <th>2</th>
      <td>FR</td>
      <td>veraval</td>
      <td>49.65</td>
      <td>0.71</td>
      <td>60.19</td>
      <td>77</td>
      <td>75</td>
      <td>6.93</td>
    </tr>
    <tr>
      <th>3</th>
      <td>RU</td>
      <td>ola</td>
      <td>59.58</td>
      <td>151.30</td>
      <td>28.40</td>
      <td>92</td>
      <td>56</td>
      <td>1.83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ZA</td>
      <td>bredasdorp</td>
      <td>-34.53</td>
      <td>20.04</td>
      <td>50.00</td>
      <td>71</td>
      <td>88</td>
      <td>3.36</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Save the DataFrame as a csv
weather_df.to_csv("DB_WeatherPy.csv", encoding="utf-8", index=False)
```


```python
# Create a Scatter Plot Latitude vs. Temperature
sns.set_style('ticks')
sns.set(style="darkgrid")
fig, ax = plt.subplots()
p = sns.regplot(x="Latitude", y="Temperature", data=weather_df, fit_reg=False).set_title('Temperature (F) by Latitude 06/01/2018')

# Save the figure
plt.savefig("Latitude_v_Temperature.png")

# Show plot
plt.show()
```


![png](output_8_0.png)



```python
# Create a Scatter Plot Latitude vs. Humidity
sns.set_style('ticks')
sns.set(style="darkgrid")
fig, ax = plt.subplots()
p = sns.regplot(x="Latitude", y="Humidity %", data= weather_df, fit_reg=False).set_title('Humidity (%) by Latitude 06/01/2018')

# Save the figure
plt.savefig("Latitude_v_Humidity.png")

# Show plot
plt.show()
```


![png](output_9_0.png)



```python
# Create a Scatter Plot Latitude vs. Wind Speed
sns.set_style('ticks')
sns.set(style="darkgrid")
fig,ax = plt.subplots()
p = sns.regplot(x="Latitude", y="Wind Speed (mph)", data= weather_df, fit_reg=False).set_title('Wind Speed (mph) by Latitude 06/01/2018')

# Save the figure
plt.savefig("Latitude_v_WindSpeed.png")

# Show plot
plt.show()
```


![png](output_10_0.png)



```python
# Create a Scatter Plot Latitude vs. Cloudiness
sns.set_style('ticks')
sns.set(style="darkgrid")
fig,ax = plt.subplots()
p = sns.regplot(x="Latitude", y="Cloudiness %", data= weather_df, fit_reg=False).set_title('Percent Cloudiness by Latitude 06/01/2018')

# Save the figure
plt.savefig("Latitude_v_Cloudiness.png")

# Show plot
plt.show()
```


![png](output_11_0.png)

