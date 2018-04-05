

```python
#Dependencies and getting today's date( will be used with plotting graphs)
from citipy import citipy
from random import randint
import openweathermapy.core as owm
from config import api_key
import matplotlib as plt
import datetime
now = datetime.datetime.now()
date1 = str(now)[:10]

print (date1)
```

    2018-04-04
    


```python
#Generating random set of latitide and longitude sets

def newpoint():
   return randint(-180,180), randint(-90, 90)

coordinates =[]

points = (newpoint() for x in range(650))
for point in points:
   #print (point)
   coordinates.append(point)

```


```python
#Getting city information from citypy

cities = []
for coordinate_pair in coordinates:
    lat, lon = coordinate_pair
    cities.append(citipy.nearest_city(lat, lon))

city_names = []

for city in cities:
    country_code = city.country_code
    name = city.city_name
    city_names.append(name)

```


```python
#Getting weather information for each city from weathermapy wrapper

settings = {"units": "Imperial","APPID" : api_key}

counter = 0
citypy_list = []
for a in city_names:
    try:
        data = owm.get_current(a, **settings)
        citypy_list.append(data)
        print (f"Data for {data['name']} is being processed and its City ID is {data['id']}")
    except:
        counter += 1 #Using exception error to pass the cities that were not found in weathermap api wrapper

print (counter)
```

    Data for Dikson is being processed and its City ID is 1507390
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Kharan is being processed and its City ID is 1174062
    Data for Albany is being processed and its City ID is 5106834
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Aswan is being processed and its City ID is 359792
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Codrington is being processed and its City ID is 2160063
    Data for Singarayakonda is being processed and its City ID is 1256176
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Ikwiriri is being processed and its City ID is 159242
    Data for Dalbandin is being processed and its City ID is 1180729
    Data for Olinda is being processed and its City ID is 3650121
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for East London is being processed and its City ID is 1006984
    Data for Hofn is being processed and its City ID is 2630299
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Dikson is being processed and its City ID is 1507390
    Data for Buraydah is being processed and its City ID is 107304
    Data for Luau is being processed and its City ID is 876177
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Ostrovnoy is being processed and its City ID is 556268
    Data for Ati is being processed and its City ID is 2436400
    Data for Natal is being processed and its City ID is 3394023
    Data for Cabedelo is being processed and its City ID is 3404558
    Data for Albany is being processed and its City ID is 5106834
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Amboasary is being processed and its City ID is 1081790
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Amarante do Maranhao is being processed and its City ID is 3407755
    Data for Albany is being processed and its City ID is 5106834
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Albany is being processed and its City ID is 5106834
    Data for Temir is being processed and its City ID is 608036
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Aguimes is being processed and its City ID is 2522325
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Busselton is being processed and its City ID is 2075265
    Data for Albany is being processed and its City ID is 5106834
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Manica is being processed and its City ID is 882955
    Data for Busselton is being processed and its City ID is 2075265
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Kindu is being processed and its City ID is 212902
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Saint-Pierre is being processed and its City ID is 2995603
    Data for Guia de Isora is being processed and its City ID is 2516860
    Data for East London is being processed and its City ID is 1006984
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Dikson is being processed and its City ID is 1507390
    Data for Sao Filipe is being processed and its City ID is 3374210
    Data for Dikson is being processed and its City ID is 1507390
    Data for Scarborough is being processed and its City ID is 2638419
    Data for Busselton is being processed and its City ID is 2075265
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Busselton is being processed and its City ID is 2075265
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Iskateley is being processed and its City ID is 866062
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Albany is being processed and its City ID is 5106834
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Sao Joao da Barra is being processed and its City ID is 3448903
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Saint Anthony is being processed and its City ID is 5606187
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Vila Velha is being processed and its City ID is 6320062
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Potosi is being processed and its City ID is 3907584
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Caribou is being processed and its City ID is 4960140
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ribeira Grande is being processed and its City ID is 3372707
    Data for Dikson is being processed and its City ID is 1507390
    Data for Narsaq is being processed and its City ID is 3421719
    Data for Guarapari is being processed and its City ID is 3461888
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Busselton is being processed and its City ID is 2075265
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Bubaque is being processed and its City ID is 2374583
    Data for Busselton is being processed and its City ID is 2075265
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Maceio is being processed and its City ID is 3395981
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Albany is being processed and its City ID is 5106834
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Mar del Plata is being processed and its City ID is 3863379
    Data for Souillac is being processed and its City ID is 3026644
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Husavik is being processed and its City ID is 5961417
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ilo is being processed and its City ID is 3938415
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Pitimbu is being processed and its City ID is 3391889
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Lokosovo is being processed and its City ID is 1500399
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Cape Town is being processed and its City ID is 3369157
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ribeira Grande is being processed and its City ID is 3372707
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Albany is being processed and its City ID is 5106834
    Data for Busselton is being processed and its City ID is 2075265
    Data for Itarema is being processed and its City ID is 3393692
    Data for Clyde River is being processed and its City ID is 5924351
    Data for Marrakesh is being processed and its City ID is 2542997
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Narsaq is being processed and its City ID is 3421719
    Data for Ostrovnoy is being processed and its City ID is 556268
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Iqaluit is being processed and its City ID is 5983720
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for East London is being processed and its City ID is 1006984
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for East London is being processed and its City ID is 1006984
    Data for Dikson is being processed and its City ID is 1507390
    Data for Indi is being processed and its City ID is 1269751
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Pisco is being processed and its City ID is 3932145
    Data for Sault Sainte Marie is being processed and its City ID is 5009004
    Data for Jablanica is being processed and its City ID is 3344411
    Data for Cape Town is being processed and its City ID is 3369157
    Data for Dikson is being processed and its City ID is 1507390
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Vardo is being processed and its City ID is 4372777
    Data for Volchansk is being processed and its City ID is 1486984
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Dikson is being processed and its City ID is 1507390
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Albany is being processed and its City ID is 5106834
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Aquiraz is being processed and its City ID is 3407407
    Data for Ballangen is being processed and its City ID is 3162108
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Belmonte is being processed and its City ID is 8010472
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Klaksvik is being processed and its City ID is 2618795
    Data for Albany is being processed and its City ID is 5106834
    Data for Dzilam Gonzalez is being processed and its City ID is 3529654
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Klaksvik is being processed and its City ID is 2618795
    Data for Marsa Matruh is being processed and its City ID is 352733
    Data for Cockburn Town is being processed and its City ID is 3576994
    Data for Albany is being processed and its City ID is 5106834
    Data for Dikson is being processed and its City ID is 1507390
    Data for Coihueco is being processed and its City ID is 3894406
    Data for Imbituba is being processed and its City ID is 3461370
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Morant Bay is being processed and its City ID is 3489440
    Data for Sao Jose da Coroa Grande is being processed and its City ID is 3388456
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Taoudenni is being processed and its City ID is 2450173
    Data for Saint George is being processed and its City ID is 262462
    Data for Kruisfontein is being processed and its City ID is 986717
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Benguela is being processed and its City ID is 3351663
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Narsaq is being processed and its City ID is 3421719
    Data for Pangnirtung is being processed and its City ID is 6096551
    Data for Susurluk is being processed and its City ID is 300058
    Data for Ponta do Sol is being processed and its City ID is 3453439
    Data for Arraial do Cabo is being processed and its City ID is 3471451
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Mar del Plata is being processed and its City ID is 3863379
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Salalah is being processed and its City ID is 286621
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ponta do Sol is being processed and its City ID is 3453439
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Adrar is being processed and its City ID is 2508813
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Reconquista is being processed and its City ID is 3429594
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Macapa is being processed and its City ID is 3396016
    Data for Nuuk is being processed and its City ID is 3421319
    Data for Albany is being processed and its City ID is 5106834
    Data for Garowe is being processed and its City ID is 58933
    Data for Pangnirtung is being processed and its City ID is 6096551
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Dikson is being processed and its City ID is 1507390
    Data for Albany is being processed and its City ID is 5106834
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Forio is being processed and its City ID is 3176748
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Hamilton is being processed and its City ID is 3573197
    Data for Rahon is being processed and its City ID is 3034535
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Bathsheba is being processed and its City ID is 3374083
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Punta Arenas is being processed and its City ID is 3874787
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Georgetown is being processed and its City ID is 3378644
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Leh is being processed and its City ID is 1264976
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Uba is being processed and its City ID is 2321057
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Georgetown is being processed and its City ID is 3378644
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Angoche is being processed and its City ID is 1052944
    Data for Albany is being processed and its City ID is 5106834
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Cape Town is being processed and its City ID is 3369157
    Data for Tazovskiy is being processed and its City ID is 1489853
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Souillac is being processed and its City ID is 3026644
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Saint George is being processed and its City ID is 262462
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Punta Arenas is being processed and its City ID is 3874787
    Data for Busselton is being processed and its City ID is 2075265
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Souillac is being processed and its City ID is 3026644
    Data for Victoria is being processed and its City ID is 1733782
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Albany is being processed and its City ID is 5106834
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Arlit is being processed and its City ID is 2447513
    Data for Atar is being processed and its City ID is 2381334
    Data for Luderitz is being processed and its City ID is 3355672
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Havoysund is being processed and its City ID is 779622
    Data for East London is being processed and its City ID is 1006984
    Data for Albany is being processed and its City ID is 5106834
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Albany is being processed and its City ID is 5106834
    Data for Cherepovets is being processed and its City ID is 569223
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Taybad is being processed and its City ID is 1159384
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Henties Bay is being processed and its City ID is 3356832
    Data for Busselton is being processed and its City ID is 2075265
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ponta do Sol is being processed and its City ID is 3453439
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Necochea is being processed and its City ID is 3430443
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Kumluca is being processed and its City ID is 305681
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Bud is being processed and its City ID is 7626370
    Data for Mecca is being processed and its City ID is 104515
    Data for Carnarvon is being processed and its City ID is 1014034
    Data for Pouso Alegre is being processed and its City ID is 3452525
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Harper is being processed and its City ID is 4696310
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Bambous Virieux is being processed and its City ID is 1106677
    Data for Jamestown is being processed and its City ID is 2069194
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Georgetown is being processed and its City ID is 3378644
    Data for Aasiaat is being processed and its City ID is 3424901
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Albany is being processed and its City ID is 5106834
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Marovoay is being processed and its City ID is 1059507
    Data for Maniitsoq is being processed and its City ID is 3421982
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for East London is being processed and its City ID is 1006984
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Placido de Castro is being processed and its City ID is 3924895
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Dikson is being processed and its City ID is 1507390
    Data for Ilulissat is being processed and its City ID is 3423146
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Srem is being processed and its City ID is 731670
    Data for Luderitz is being processed and its City ID is 3355672
    Data for Shakawe is being processed and its City ID is 933077
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Cullman is being processed and its City ID is 4057835
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Gazanjyk is being processed and its City ID is 161974
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Kyshtovka is being processed and its City ID is 1501000
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Georgetown is being processed and its City ID is 3378644
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Izhmorskiy is being processed and its City ID is 1505228
    Data for Ilulissat is being processed and its City ID is 3423146
    Data for Praia is being processed and its City ID is 3460954
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Albany is being processed and its City ID is 5106834
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Conchas is being processed and its City ID is 3465729
    Data for Victoria is being processed and its City ID is 1733782
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Agadez is being processed and its City ID is 2448085
    Data for Praia da Vitoria is being processed and its City ID is 3372760
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Kachiry is being processed and its City ID is 1523662
    Data for Cape Town is being processed and its City ID is 3369157
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Mar del Plata is being processed and its City ID is 3863379
    Data for Ilhabela is being processed and its City ID is 3461425
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Sao Joao da Barra is being processed and its City ID is 3448903
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Sorland is being processed and its City ID is 3137469
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Narsaq is being processed and its City ID is 3421719
    Data for Hofn is being processed and its City ID is 2630299
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Souillac is being processed and its City ID is 3026644
    Data for Mar del Plata is being processed and its City ID is 3863379
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Sao Joao da Barra is being processed and its City ID is 3448903
    Data for Klaksvik is being processed and its City ID is 2618795
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Lagoa is being processed and its City ID is 2267254
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Klaksvik is being processed and its City ID is 2618795
    Data for La Rioja is being processed and its City ID is 3848950
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Minab is being processed and its City ID is 123941
    Data for Coquimbo is being processed and its City ID is 3893629
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Punta Arenas is being processed and its City ID is 3874787
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Albany is being processed and its City ID is 5106834
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Dikson is being processed and its City ID is 1507390
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ciudad Real is being processed and its City ID is 2519402
    Data for Mana is being processed and its City ID is 789988
    Data for Springfield is being processed and its City ID is 4409896
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Saint Andrews is being processed and its City ID is 2181133
    Data for Zapadnaya Dvina is being processed and its City ID is 464891
    Data for Bhanpuri is being processed and its City ID is 1276151
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Ceres is being processed and its City ID is 3862100
    Data for San Giorgio del Sannio is being processed and its City ID is 3168305
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Saldanha is being processed and its City ID is 2737599
    Data for Busselton is being processed and its City ID is 2075265
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Verkhnyaya Inta is being processed and its City ID is 1487332
    Data for Maceio is being processed and its City ID is 3395981
    Data for Clyde River is being processed and its City ID is 5924351
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Upernavik is being processed and its City ID is 3418910
    Data for Albany is being processed and its City ID is 5106834
    Data for Albany is being processed and its City ID is 5106834
    Data for Ponta do Sol is being processed and its City ID is 3453439
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Punta Arenas is being processed and its City ID is 3874787
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Turmalina is being processed and its City ID is 3445912
    Data for Salalah is being processed and its City ID is 286621
    Data for Novobelokatay is being processed and its City ID is 519027
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Adrar is being processed and its City ID is 2508813
    Data for Dikson is being processed and its City ID is 1507390
    Data for Darnah is being processed and its City ID is 87205
    Data for Dikson is being processed and its City ID is 1507390
    Data for Betanzos is being processed and its City ID is 3128071
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Adrar is being processed and its City ID is 2508813
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Dikson is being processed and its City ID is 1507390
    Data for Kruisfontein is being processed and its City ID is 986717
    Data for Dikson is being processed and its City ID is 1507390
    Data for Torbay is being processed and its City ID is 6167817
    Data for Weligama is being processed and its City ID is 1223738
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Vangaindrano is being processed and its City ID is 1054329
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Lerwick is being processed and its City ID is 2644605
    Data for Tessalit is being processed and its City ID is 2449893
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Jiblah is being processed and its City ID is 74185
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Bredasdorp is being processed and its City ID is 1015776
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Ushuaia is being processed and its City ID is 3833367
    Data for Mandera is being processed and its City ID is 187896
    Data for Port Elizabeth is being processed and its City ID is 4501427
    Data for Geraldton is being processed and its City ID is 5960603
    Data for Ballina is being processed and its City ID is 2966778
    Data for Sao Jose da Coroa Grande is being processed and its City ID is 3388456
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Tasiilaq is being processed and its City ID is 3424607
    Data for Dikson is being processed and its City ID is 1507390
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Mar del Plata is being processed and its City ID is 3863379
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Farafangana is being processed and its City ID is 1065158
    Data for Gravdal is being processed and its City ID is 3147822
    Data for Port Alfred is being processed and its City ID is 964432
    Data for Dikson is being processed and its City ID is 1507390
    Data for Hermanus is being processed and its City ID is 3366880
    Data for Qaanaaq is being processed and its City ID is 3831208
    Data for Hithadhoo is being processed and its City ID is 1282256
    Data for Dikson is being processed and its City ID is 1507390
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Sulmona is being processed and its City ID is 3166034
    Data for Ponta Delgada is being processed and its City ID is 3372783
    Data for Dhangadhi is being processed and its City ID is 1283467
    Data for Dikson is being processed and its City ID is 1507390
    Data for Vestmannaeyjar is being processed and its City ID is 3412093
    Data for La Asuncion is being processed and its City ID is 3652350
    Data for Saint-Philippe is being processed and its City ID is 6138908
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Dikson is being processed and its City ID is 1507390
    Data for Longyearbyen is being processed and its City ID is 2729907
    Data for Albany is being processed and its City ID is 5106834
    105
    


```python
#Confirming the number of cities in citypy that are available in weathermapy

print (len(citypy_list))
```

    545
    


```python
#Printing date for one of the extracted cities

import pprint
pprint.pprint (citypy_list[2])
```

    {'base': 'stations',
     'clouds': {'all': 40},
     'cod': 200,
     'coord': {'lat': -54.81, 'lon': -68.31},
     'dt': 1522882800,
     'id': 3833367,
     'main': {'humidity': 81,
              'pressure': 986,
              'temp': 42.8,
              'temp_max': 42.8,
              'temp_min': 42.8},
     'name': 'Ushuaia',
     'sys': {'country': 'AR',
             'id': 4754,
             'message': 0.0045,
             'sunrise': 1522926312,
             'sunset': 1522965932,
             'type': 1},
     'visibility': 10000,
     'weather': [{'description': 'scattered clouds',
                  'icon': '03n',
                  'id': 802,
                  'main': 'Clouds'}],
     'wind': {'deg': 100.002, 'speed': 6.73}}
    


```python
#Constructing the dataframe with all the required parameters

import pandas as pd

latitude = []
humidity = []
wind_speed = []
temperature = []
City_name = []
City_Country = []
Cloudiness = []
City_id = []
date = []

for a in citypy_list:
    latitude.append(a['coord']['lat'])
    humidity.append(a['main']['humidity'])
    wind_speed.append(a['wind']['speed'])
    temperature.append(a['main']['temp'])
    City_name.append(a['name'])
    City_Country.append(a['sys']['country'])
    Cloudiness.append(a['clouds']['all'])
    City_id.append(a['id'])
    date.append(a['dt'])
    
b = {'Latitude' : latitude, 'City_Country' : City_Country, 'Humidity (%)' : humidity, 'Temperature' : temperature, 
     'City_name' : City_name, 'Cloudiness(%)' : Cloudiness, 'Wind_Speed' : wind_speed, 'City_id' :City_id, "Date" : date}
#df.columns = ['City_id','latitude', 'humidity', 'wind_speed', 'temperature']

City_data_df = pd.DataFrame(b)

City_data_df.head()
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
      <th>City_Country</th>
      <th>City_id</th>
      <th>City_name</th>
      <th>Cloudiness(%)</th>
      <th>Date</th>
      <th>Humidity (%)</th>
      <th>Latitude</th>
      <th>Temperature</th>
      <th>Wind_Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>RU</td>
      <td>1507390</td>
      <td>Dikson</td>
      <td>0</td>
      <td>1522886464</td>
      <td>70</td>
      <td>73.51</td>
      <td>-9.98</td>
      <td>16.13</td>
    </tr>
    <tr>
      <th>1</th>
      <td>RU</td>
      <td>1507390</td>
      <td>Dikson</td>
      <td>0</td>
      <td>1522886464</td>
      <td>70</td>
      <td>73.51</td>
      <td>-9.98</td>
      <td>16.13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>AR</td>
      <td>3833367</td>
      <td>Ushuaia</td>
      <td>40</td>
      <td>1522882800</td>
      <td>81</td>
      <td>-54.81</td>
      <td>42.80</td>
      <td>6.73</td>
    </tr>
    <tr>
      <th>3</th>
      <td>RU</td>
      <td>1507390</td>
      <td>Dikson</td>
      <td>0</td>
      <td>1522886464</td>
      <td>70</td>
      <td>73.51</td>
      <td>-9.98</td>
      <td>16.13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>MV</td>
      <td>1282256</td>
      <td>Hithadhoo</td>
      <td>0</td>
      <td>1522886466</td>
      <td>100</td>
      <td>-0.60</td>
      <td>84.12</td>
      <td>6.73</td>
    </tr>
  </tbody>
</table>
</div>




```python
City_data_df.shape
```




    (545, 9)




```python
#importing the dataframe to a csv

City_data_df.to_csv("City_data_output.csv")
```


```python
#confirming the base url used

print (owm.BASE_URL)
```

    http://api.openweathermap.org/data/2.5/
    

Plotting of Charts


```python
import matplotlib.pyplot as plt
plt.scatter(latitude, temperature, c="green")
plt.title( "Latitude vs Temperature(F) " + str(date1)  )
plt.xlabel("Latitude")
plt.ylabel("Temperature (F)")
plt.grid()

plt.savefig("Latitide vs Temperature.png")

plt.show()
```


![png](output_11_0.png)



```python
plt.scatter(latitude, humidity)
plt.title( "Latitude vs Humidity(%) " + str(date1) )
plt.xlabel("Latitude")
plt.ylabel("Humidity (%)")
plt.grid()
plt.show()
plt.savefig("Latitide vs Humidity(%).png")
```


![png](output_12_0.png)



    <matplotlib.figure.Figure at 0x1d1bd7fd588>



```python
plt.scatter(latitude, wind_speed)
plt.title( "Latitude vs Wind Speed " + str(date1) )
plt.xlabel("Latitude")
plt.ylabel("Wind Speed (mph)")
plt.grid()
plt.show()
plt.savefig("Latitide vs Wind Speed.png")
```


![png](output_13_0.png)



    <matplotlib.figure.Figure at 0x1d1bd826710>



```python
plt.scatter(latitude, Cloudiness)
plt.title( "Latitude vs Cloudiness (%) " + str(date1) )
plt.xlabel("Latitude")
plt.ylabel("Cloudiness (%)")
plt.grid()
plt.show()
plt.savefig("Latitide vs Cloudiness.png")
```


![png](output_14_0.png)



    <matplotlib.figure.Figure at 0x1d1bd8d2cc0>


Observations:
    a) Temperatures are highest in the latitude range of -20 to 20 degrees
    b) Wind speeds are independent of the latitude
    c) Humidity is also independent of the latitude
