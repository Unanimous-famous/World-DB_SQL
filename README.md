# SQL Practice: Data Technician Workbook – Week 3

This repository contains SQL scripts and tasks completed as part of Week 3 of the **Data Technician** course. It includes answers to conceptual questions, SQL join exercises, and practical database queries based on the `world` dataset.

## 📁 Contents

- `world_db.sql`: MySQL dump file of the `world` database used for all SQL tasks
- `Data_Technician_Workbook_Week_3 Workbench Use.docx`: Documented exercises, explanations, and results

---

## 🧠 Concepts Covered

### Day 1 – Database Fundamentals

- **Primary vs. Foreign Keys**
- Real-world examples of:
  - One-to-one relationships
  - One-to-many relationships
  - Many-to-many relationships
- **Relational vs. Non-relational Databases**
- When and why to use non-relational models

---

## 🔗 SQL Joins (Day 3)

Explored and demonstrated with examples:

- `INNER JOIN`
- `LEFT JOIN`
- `RIGHT JOIN`
- `FULL JOIN`
- `CROSS JOIN`
- `SELF JOIN`

Includes real-world use cases and sample outputs.

---

## 🧪 SQL Practical Tasks (Day 4)

Using the `world` database, the following tasks were completed with query syntax and outputs:

- ✅ Count cities in the USA
- ✅ Find the country with the highest life expectancy
- ✅ List cities with `'New'` in their name
- ✅ Display the 10 most populous cities
- ✅ Filter cities with population > 2 million
- ✅ Find cities starting with `'Be'`
- ✅ Identify cities with population between 500,000 and 1,000,000

---

## 🛠️ Getting Started

To run the SQL queries:

1. Import `world_db.sql` into MySQL Workbench
2. Use the `world` database:
   ```sql
   USE world;
'''

# 1.	Count Cities in USA

```sql
SELECT COUNT(city.name), country.name
FROM city
INNER JOIN country ON city.CountryCode = country.Code
WHERE country.name = "United States";
```

Result: 274


## 2. Country with Highest Life Expectancy

```sql
SELECT LifeExpectancy, name 
FROM country 
ORDER BY LifeExpectancy DESC 
LIMIT 1;
```

```
Result:
LifeExpectancy: 83.5
Country:        Andorra
```

---

## 3. Cities Containing 'New' in the Name

```sql
SELECT * 
FROM city 
WHERE name LIKE '%new%';
```

```
ID     | Name                     | CountryCode | District                 | Population
------ | ------------------------ | ------------|--------------------------|------------
137    | Newcastle                | AUS         | New South Wales          | 270324
482    | Newcastle upon Tyne      | GBR         | England                  | 189150
502    | Newport                  | GBR         | Wales                    | 139000
734    | Newcastle                | ZAF         | KwaZulu-Natal            | 222993
936    | Kowloon and New Kowloon | HKG         | Kowloon and New Kowl     | 1987996
1106   | New Bombay               | IND         | Maharashtra              | 307297
1109   | New Delhi                | IND         | Delhi                    | 301297
2857   | Khanewal                 | PAK         | Punjab                   | 133000
3793   | New York                 | USA         | New York                 | 8008278
3823   | New Orleans              | USA         | Louisiana                | 484674
3855   | Newark                   | USA         | New Jersey               | 273546
3905   | Newport News             | USA         | Virginia                 | 180150
3971   | New Haven                | USA         | Connecticut              | 123626
4044   | New Bedford              | USA         | Massachusetts            | 94780
```

---

## 4. Top 10 Most Populous Cities

```sql
SELECT name, population 
FROM city 
ORDER BY population DESC 
LIMIT 10;
```

```
Name                | Population
-------------------|------------
Mumbai (Bombay)    | 10500000
São Paulo          | 9968485
Seoul              | 9981619
Shanghai           | 9696300
Jakarta            | 9604900
Karachi            | 9269265
Moscow             | 8389200
Istanbul           | 8787958
Ciudad de México   | 8591309
New York           | 8008278
```


## 5. Cities with Population Larger than 2,000,000

```sql

SELECT name, population 
FROM city 
WHERE population >= 2000000;
```

| Name               | Population |
|--------------------|------------|
| Alger              | 2168000    |
| Luanda             | 2022000    |
| Buenos Aires       | 2982146    |
| Sydney             | 3276207    |
| Melbourne          | 2865329    |
| Dhaka              | 3612850    |
| São Paulo          | 9968485    |
| Rio de Janeiro     | 5598953    |
| Salvador           | 2302832    |
| Belo Horizonte     | 2139125    |
| Fortaleza          | 2097757    |
| London             | 7285000    |
| Santiago de Chile  | 4703954    |
| Guayaquil          | 2070040    |
| Cairo              | 6789479    |
| ...                | ...        |




## 6. Cities Beginning with 'Be' Prefix

```sql
SELECT * 
FROM city 
where name like 'Be%';
```

```
ID	Name	CountryCode	District	Population

| ID    | Name                        | CountryCode | District              | Population |
|-------|-----------------------------|-------------|------------------------|------------|
| 45    | Béjaïa                      | DZA         | Béjaïa                 | 117162     |
| 49    | Béchar                      | DZA         | Béchar                 | 107311     |
| 59    | Benguela                    | AGO         | Benguela               | 128300     |
| 93    | Berazategui                 | ARG         | Buenos Aires           | 276916     |
| 184   | Belize City                 | BLZ         | Belize City            | 55810      |
| 185   | Belmopan                    | BLZ         | Cayo                   | 7105       |
| 209   | Belo Horizonte              | BRA         | Minas Gerais           | 2139125    |
| 216   | Belém                       | BRA         | Pará                   | 1186926    |
| 246   | Belford Roxo                | BRA         | Rio de Janeiro         | 425194     |
| 266   | Betim                       | BRA         | Minas Gerais           | 302108     |
| 453   | Bento Gonçalves             | BRA         | Rio Grande do Sul      | 89254      |
| 469   | Belfast                     | GBR         | North Ireland          | 287500     |
| 724   | Benoni                      | ZAF         | Gauteng                | 365467     |
| 949   | Bekasi                      | IDN         | West Java              | 644300     |
| 980   | Bengkulu                    | IDN         | Bengkulu               | 146439     |
| 1102  | Belgaum                     | IND         | Karnataka              | 326399     |
| 1122  | Bellary                     | IND         | Karnataka              | 245391     |
| 1285  | Berhampore (Baharampur)     | IND         | West Bengali           | 115144     |
| 1315  | Beawar                      | IND         | Rajasthan              | 105363     |
| 1357  | Bettiah                     | IND         | Bihar                  | 92583      |
| 1454  | Beerseba                    | ISR         | Ha Darom               | 163700     |
| 1460  | Bene Beraq                  | ISR         | Tel Aviv               | 133900     |
| 1497  | Bergamo                     | ITA         | Lombardia              | 117837     |
| 1699  | Beppu                       | JPN         | Oita                   | 127486     |
| 1792  | Beograd                     | YUG         | Central Serbia         | 1204000    |
| 1933  | Benxi                       | CHN         | Liaoning               | 770000     |
| 1961  | Bengbu                      | CHN         | Anhui                  | 449245     |
| 2065  | Bei´an                      | CHN         | Heilongjiang           | 204899     |
| 2073  | Beipiao                     | CHN         | Liaoning               | 194301     |
| 2203  | Beihai                      | CHN         | Guangxi                | 112673     |
| 2268  | Bello                       | COL         | Antioquia              | 333470     |
| 2438  | Beirut                      | LBN         | Beirut                 | 1100000    |
| 2442  | Bengasi                     | LBY         | Bengasi                | 804000     |
| 2499  | Beni-Mellal                 | MAR         | Tadla-Azilal           | 140212     |
| 2512  | Beau Bassin-Rose Hill       | MUS         | Plaines Wilhelms       | 100616     |
| 2553  | Benito Juárez               | MEX         | Quintana Roo           | 419276     |
| 2693  | Bender (Tîghina)            | MDA         | Bender (Tîghina)       | 125700     |
| 2700  | Beira                       | MOZ         | Sofala                 | 397368     |
| 2765  | Benin City                  | NGA         | Edo & Delta            | 229400     |
| 2808  | Bergen                      | NOR         | Hordaland              | 230948     |
| 3002  | Besançon                    | FRA         | Franche-Comté          | 117733     |
| 3068  | Berlin                      | DEU         | Berliini               | 3386667    |
| 3144  | Bergisch Gladbach           | DEU         | Nordrhein-Westfalen    | 106150     |
| 3248  | Bern                        | CHE         | Bern                   | 122700     |
| 3462  | Berdjansk                   | UKR         | Zaporizzja             | 130000     |
| 3477  | Berdytšiv                   | UKR         | Zytomyr                | 90000      |
| 3633  | Belgorod                    | RUS         | Belgorod               | 342000     |
| 3680  | Berezniki                   | RUS         | Perm                   | 181900     |
| 3992  | Beaumont                    | USA         | Texas                  | 113866     |
| 4003  | Bellevue                    | USA         | Washington             | 109569     |
| 4024  | Berkeley                    | USA         | California             | 102743     |
```

## 7.	Cities with Population Between 500,000-1,000,000

```sql
SELECT name, population
FROM city
WHERE population
BETWEEN 500000 AND 1000000;
```

```
Name	Population
'Amsterdam'	'731200'
'Rotterdam'	'593321'
'Oran'	'609823'
'Dubai'	'669181'
'Rosario'	'907718'
'Lomas de Zamora'	'622013'
'Quilmes'	'559249'
'Almirante Brown'	'538918'
'La Plata'	'521936'
'Mar del Plata'	'512880'
'Adelaide'	'978100'
'Khulna'	'663340'
'Cotonou'	'536827'
'Santa Cruz de la Sierra'	'935361'
'La Paz'	'758141'
'El Alto'	'534466'
'Campinas'	'950043'
'São Gonçalo'	'869254'
'Nova Iguaçu'	'862225'
'São Luís'	'837588'
'Maceió'	'786288'
'Duque de Caxias'	'746758'
'São Bernardo do Campo'	'723132'
'Teresina'	'691942'
'Natal'	'688955'
'Osasco'	'659604'
'Campo Grande'	'649593'
'Santo André'	'630073'
'João Pessoa'	'584029'
'Jaboatão dos Guararapes'	'558680'
'Contagem'	'520801'
'São José dos Campos'	'515553'
'Glasgow'	'619680'
'Ouagadougou'	'824000'
'Shubra al-Khayma'	'870716'
'Valencia'	'739412'
'Sevilla'	'701927'
'Zaragoza'	'603367'
'Málaga'	'530553'
'Soweto'	'904165'
'Johannesburg'	'756653'
'Port Elizabeth'	'752319'
'Pretoria'	'658630'
'Inanda'	'634065'
'Durban'	'566120'
'Cebu'	'718821'
'Zamboanga'	'601794'
'Pasig'	'505058'
'Ciudad de Guatemala'	'823301'
'Port-au-Prince'	'884472'
'Tegucigalpa'	'813900'
'Malang'	'716862'
'Bandar Lampung'	'680332'
'Bekasi'	'644300'
'Padang'	'534474'
'Surakarta'	'518600'
'Madurai'	'977856'
'Haora (Howrah)'	'950435'
'Varanasi (Benares)'	'929270'
'Patna'	'917243'
'Srinagar'	'892506'
'Agra'	'891790'
'Coimbatore'	'816321'
'Thane (Thana)'	'803389'
'Allahabad'	'792858'
'Meerut'	'753778'
'Vishakhapatnam'	'752037'
'Jabalpur'	'741927'
'Amritsar'	'708835'
'Faridabad'	'703592'
'Vijayawada'	'701827'
'Gwalior'	'690765'
'Jodhpur'	'666279'
'Nashik (Nasik)'	'656925'
'Hubli-Dharwad'	'648298'
'Solapur (Sholapur)'	'604215'
'Ranchi'	'599306'
'Bareilly'	'587211'
'Guwahati (Gauhati)'	'584342'
'Shambajinagar (Aurangabad)'	'573272'
'Cochin (Kochi)'	'564589'
'Rajkot'	'559407'
'Kota'	'537371'
'Thiruvananthapuram (Trivandrum'	'524006'
'Pimpri-Chinchwad'	'517083'
'Jalandhar (Jullundur)'	'509510'
'Gorakhpur'	'505566'
'Chandigarh'	'504094'
'Mosul'	'879000'
'Karaj'	'940968'
'Ahvaz'	'804980'
'Qom'	'777677'
'Kermanshah'	'692986'
'Jerusalem'	'633700'
'Torino'	'903705'
'Palermo'	'683794'
'Genova'	'636104'
'Sendai'	'989975'
'Chiba'	'863930'
'Sakai'	'797735'
'Kumamoto'	'656734'
'Okayama'	'624269'
'Sagamihara'	'586300'
'Hamamatsu'	'568796'
'Kagoshima'	'549977'
'Funabashi'	'545299'
'Higashiosaka'	'517785'
'Hachioji'	'513451'
'Sanaa'	'503600'
'Amman'	'1000000'
'Phnom Penh'	'570155'
'Calgary'	'768082'
'Toronto'	'688275'
'North York'	'622632'
'Winnipeg'	'618477'
'Edmonton'	'616306'
'Mississauga'	'608072'
'Scarborough'	'594501'
'Vancouver'	'514008'
'Bangui'	'524000'
'Baotou'	'980000'
'Shenzhen'	'950500'
'Hohhot'	'916700'
'Handan'	'840000'
'Wuxi'	'830000'
'Xuzhou'	'810000'
'Datong'	'800000'
'Yichun'	'800000'
'Benxi'	'770000'
'Luoyang'	'760000'
'Suzhou'	'710000'
'Xining'	'700200'
'Huainan'	'700000'
'Jixi'	'683885'
'Daqing'	'660000'
'Fuxin'	'640000'
'Amoy [Xiamen]'	'627500'
'Liuzhou'	'610000'
'Shantou'	'580000'
'Jinzhou'	'570000'
'Mudanjiang'	'570000'
'Yinchuan'	'544500'
'Changzhou'	'530000'
'Zhangjiakou'	'530000'
'Dandong'	'520000'
'Hegang'	'520000'
'Kaifeng'	'510000'
'Bishkek'	'589400'
'Cartagena'	'805757'
'Cúcuta'	'606932'
'Bucaramanga'	'515555'
'Brazzaville'	'950000'
'Pointe-Noire'	'500000'
'Lubumbashi'	'851381'
'Mbuji-Mayi'	'806475'
'Hamhung'	'709730'
'Chongjin'	'582480'
'Nampo'	'566200'
'Songnam'	'869094'
'Puchon'	'779412'
'Suwon'	'755550'
'Anyang'	'591106'
'Chonju'	'563153'
'Chongju'	'531376'
'Koyang'	'518282'
'Ansan'	'510314'
'Pohang'	'508899'
'Athenai'	'772072'
'Zagreb'	'706770'
'Vientiane'	'531800'
'Riga'	'764328'
'Monrovia'	'850000'
'Bengasi'	'804000'
'Vilnius'	'577969'
'Antananarivo'	'675669'
'Bamako'	'809552'
'Rabat'	'623457'
'Marrakech'	'621914'
'Fès'	'541162'
'Tanger'	'521735'
'Salé'	'504420'
'Nouakchott'	'667300'
'Naucalpan de Juárez'	'857511'
'Mexicali'	'764902'
'Culiacán'	'744859'
'Acapulco de Juárez'	'721011'
'Tlalnepantla de Baz'	'720755'
'Mérida'	'703324'
'Chihuahua'	'670208'
'San Luis Potosí'	'669353'
'Guadalupe'	'668780'
'Toluca'	'665617'
'Aguascalientes'	'643360'
'Querétaro'	'639839'
'Morelia'	'619958'
'Hermosillo'	'608697'
'Saltillo'	'577352'
'Torreón'	'529093'
'Centro (Villahermosa)'	'519873'
'Chisinau'	'719900'
'Ulan Bator'	'773700'
'Mandalay'	'885300'
'Kathmandu'	'591835'
'Managua'	'959000'
'Ogbomosho'	'730000'
'Kano'	'674100'
'Oslo'	'508726'
'Peshawar'	'988005'
'Quetta'	'560307'
'Islamabad'	'524500'
'Asunción'	'557776'
'Arequipa'	'762000'
'Trujillo'	'652000'
'Chiclayo'	'517000'
'Lisboa'	'563210'
'Lódz'	'800110'
'Kraków'	'738150'
'Wroclaw'	'636765'
'Poznan'	'576899'
'Marseille'	'798430'
'Stockholm'	'750348'
'Köln'	'962507'
'Frankfurt am Main'	'643821'
'Essen'	'599515'
'Dortmund'	'590213'
'Stuttgart'	'582443'
'Düsseldorf'	'568855'
'Bremen'	'540330'
'Duisburg'	'519793'
'Hannover'	'514718'
'Mekka'	'965700'
'Medina'	'608300'
'Pikine'	'855287'
'Dakar'	'785071'
'Freetown'	'850000'
'Mogadishu'	'997000'
'Colombo'	'645000'
'Khartum'	'947483'
'Sharq al-Nil'	'700887'
'Helsinki [Helsingfors]'	'555474'
'Hims'	'507404'
'Dushanbe'	'524000'
'Taichung'	'940589'
'Tainan'	'728060'
'Panchiao'	'523850'
'N´Djaména'	'530965'
'Tunis'	'690600'
'Gaziantep'	'789056'
'Konya'	'628364'
'Mersin (Içel)'	'587212'
'Antalya'	'564914'
'Ashgabat'	'540600'
'Kampala'	'890800'
'Zaporizzja'	'848000'
'Lviv'	'788000'
'Kryvyi Rig'	'703000'
'Mykolajiv'	'508000'
'Barquisimeto'	'877239'
'Valencia'	'794246'
'Ciudad Guayana'	'663713'
'Volgograd'	'993400'
'Voronez'	'907700'
'Krasnojarsk'	'875500'
'Saratov'	'874000'
'Toljatti'	'722900'
'Uljanovsk'	'667400'
'Izevsk'	'652800'
'Krasnodar'	'639000'
'Jaroslavl'	'616700'
'Habarovsk'	'609400'
'Vladivostok'	'606200'
'Irkutsk'	'593700'
'Barnaul'	'580100'
'Novokuznetsk'	'561600'
'Penza'	'532200'
'Rjazan'	'529900'
'Orenburg'	'523600'
'Lipetsk'	'521000'
'Nabereznyje Tšelny'	'514700'
'Tula'	'506100'
'Tjumen'	'503400'
'Haiphong'	'783133'
'Detroit'	'951270'
'San Jose'	'894943'
'Indianapolis'	'791926'
'San Francisco'	'776733'
'Jacksonville'	'735167'
'Columbus'	'711470'
'Austin'	'656562'
'Baltimore'	'651154'
'Memphis'	'650100'
'Milwaukee'	'596974'
'Boston'	'589141'
'Washington'	'572059'
'Nashville-Davidson'	'569891'
'El Paso'	'563662'
'Seattle'	'563374'
'Denver'	'554636'
'Charlotte'	'540828'
'Fort Worth'	'534694'
'Portland'	'529121'
'Oklahoma City'	'506132'
'Bulawayo'	'621742'
```



## 8.	Display Cities Sorted by Name in Ascending Order

```sql
SELECT name AS City
FROM city ORDER BY name;
```

```
City
'[San Cristóbal de] la Laguna'
'´s-Hertogenbosch'
'A Coruña (La Coruña)'
'Aachen'
'Aalborg'
'Aba'
'Abadan'
'Abaetetuba'
'Abakan'
'Abbotsford'
'Abeokuta'
'Aberdeen'
'Abha'
'Abidjan'
'Abiko'
'Abilene'
'Abohar'
'Abottabad'
'Abu Dhabi'
'Abuja'
'Acámbaro'
'Acapulco de Juárez'
      .
      .
      .
```


## 9.	Most Populated City

```sql
SELECT name, population
FROM city
ORDER BY population DESC
LIMIT 100;
```

```
Name 	Population
'Mumbai (Bombay)'	'10500000'
'Seoul'	'9981619'
'São Paulo'	'9968485'
'Shanghai'	'9696300'
'Jakarta'	'9604900'
'Karachi'	'9269265'
'Istanbul'	'8787958'
'Ciudad de México'	'8591309'
'Moscow'	'8389200'
'New York'	'8008278'
'Tokyo'	'7980230'
'Peking'	'7472000'
'London'	'7285000'
'Delhi'	'7206704'
'Cairo'	'6789479'
'Teheran'	'6758845'
      .
      .
      .
```


## 10.	City Name Frequency Analysis: Supporting Geography Education 

 group by name order by count(name) desc;

```sql
SELECT DISTINCT name, COUNT(name)
FROM city
GROUP BY name
ORDER BY COUNT(name) DESC;
```

```
Name	Frequency
'San José'	'4'
'Córdoba'	'3'
'San Miguel'	'3'
'San Fernando'	'3'
'Hamilton'	'3'
'La Paz'	'3'
'Toledo'	'3'
'Cambridge'	'3'
'Valencia'	'3'
'León'	'3'
'Victoria'	'3'
'Richmond'	'3'
'Springfield'	'3'
'Ede'	'2'
'Saint John´s'	'2'
```

## 11.	City with the Lowest Population

```sql
SELECT name,population
FROM city
WHERE population in (SEELCT MIN(population) FROM city)
```

```
name 			      Population
'Adamstown'	  	    '42'
```



## 12.	Country with Largest Population

```sql
SELECT name,population
FROM country
WHERE population in (SEELCT MAX(population) FROM country)
```

```
name			   population
'China'			'1277558000'
```

## 13.	Capital of Spain

```sql
SELECT city.name, country.name FROM city 
 	INNER JOIN country ON city.CountryCode = country.code
	WHERE country.name = 'Spain' AND 
	id IN (SELECT capital FROM country WHERE name = 'Spain');
```

```
'Madrid','Spain'
```

## 14.	Cities in Europe:

```sql
SELECT city.name, country.name, country.continent
FROM city
INNER JOIN country
ON city.CountryCode = country.code
WHERE country.continent = 'Europe';  
```

- 10 Randomly selected results: 

```sql
SELECT city.name, country.name, country.continent
FROM city
INNER JOIN country
ON city.CountryCode = country.code
WHERE country.continent = 'Europe';
ORDER BY RAND()
LIMIT 10;  
```


```
	European Cities 	
City	Country	Continent
'Elektrostal'	'Russian Federation'	'Europe'
'Bydgoszcz'	'Poland'	'Europe'
'Rybinsk'	'Russian Federation'	'Europe'
'Haarlemmermeer'	'Netherlands'	'Europe'
'Alkmaar'	'Netherlands'	'Europe'
'Rimini'	'Italy'	'Europe'
'Espoo'	'Finland'	'Europe'
'Volzski'	'Russian Federation'	'Europe'
'Peristerion'	'Greece'	'Europe'
'Douglas'	'United Kingdom'	'Europe'

```

## 15.	Average City Population by Country

```sql
SELECT country.name, AVG(city.population) AS avg_city_population
FROM city
INNER JOIN country
ON city.CountryCode = country.code
GROUP BY country.name;
```

```
Average City Population	Country
'29034.0000'	'Aruba'
'583025.0000'	'Afghanistan'
'512320.0000'	'Angola'
'778.0000'	'Anguilla'
'270000.0000'	'Albania'
'21189.0000'	'Andorra'
'2345.0000'	'Netherlands Antilles'
'345667.2000'	'United Arab Emirates'
'350816.8947'	'Argentina'
'544366.6667'	'Armenia'
'3761.5000'	'American Samoa'
'24000.0000'	'Antigua and Barbuda'
'808119.0000'	'Australia'
'397378.8333'	'Austria'
'616000.0000'	'Azerbaijan'
'300000.0000'	'Burundi'
'178813.5556'	'Belgium'
'242125.7500'	'Benin'
'409666.6667'	'Burkina Faso'
'357079.4167'	'Bangladesh'
'269691.5000'	'Bulgaria'
'148000.0000'	'Bahrain'
'172000.0000'	'Bahamas'
        .
        .
        .
```

## 16.	Capital Cities Population Comparison

- This gives all:
```sql
SELECT city.name, city.population, country.name
FROM city
INNER JOIN country
ON city.CountryCode = country.code
WHERE city.id
IN (SELECT capital FROM country);
```

- This gives 10 random of all results:

```sql
SELECT city.name, city.population, country.name
FROM city
INNER JOIN country
ON city.CountryCode = country.code
WHERE city.id IN (SELECT capital FROM country)
ORDER BY RAND()
LIMIT 10;
```

```
Capital	Population	Country
'Ankara'	'3038159'	'Turkey'
'Ciudad de Panamá'	'471373'	'Panama'
'Tórshavn'	'14542'	'Faroe Islands'
'Ashgabat'	'540600'	'Turkmenistan'
'Stockholm'	'750348'	'Sweden'
'Honiara'	'50100'	'Solomon Islands'
'Monaco-Ville'	'1234'	'Monaco'
'Montevideo'	'1236000'	'Uruguay'
'Nairobi'	'2290000'	'Kenya'
'Kingston'	'800'	'Norfolk Island'
```

- This gives the ten most populated:
  
```sql
SELECT city.name, city.population, country.name
FROM city INNER JOIN country
ON city.CountryCode = country.code
WHERE city.id IN (SELECT capital FROM country)
ORDER BY city.population DESC
LIMIT 10;
```
```
Capital	Population	Country
'Seoul'	'9981619'	'South Korea'
'Jakarta'	'9604900'	'Indonesia'
'Ciudad de México'	'8591309'	'Mexico'
'Moscow'	'8389200'	'Russian Federation'
'Tokyo'	'7980230'	'Japan'
'Peking'	'7472000'	'China'
'London'	'7285000'	'United Kingdom'
'Cairo'	'6789479'	'Egypt'
'Teheran'	'6758845'	'Iran'
'Lima'	'6464693'	'Peru'
```

## 17.	Countries with Low Population Density

```sql
SELECT name, population/surfacearea AS Capitaperarea
FROM country
ORDER BY Capitaperarea
LIMIT 30;
```

```
Country	Population
'Bouvet Island'	'0.0000'
'South Georgia and the South Sandwich Islands'	'0.0000'
'Heard Island and McDonald Islands'	'0.0000'
'United States Minor Outlying Islands'	'0.0000'
'Antarctica'	'0.0000'
'French Southern territories'	'0.0000'
'British Indian Ocean Territory'	'0.0000'
'Greenland'	'0.0259'
'Svalbard and Jan Mayen'	'0.0513'
'Falkland Islands'	'0.1643'
'Pitcairn'	'1.0204'
'Western Sahara'	'1.1015'
'Mongolia'	'1.6993'
'French Guiana'	'2.0111'
'Namibia'	'2.0939'
'Australia'	'2.4397'
'Suriname'	'2.5541'
'Mauritania'	'2.6036'
'Iceland'	'2.7087'
'Botswana'	'2.7882'
'Canada'	'3.1239'
'Libyan Arab Jamahiriya'	'3.1855'
'Guyana'	'4.0052'
'Gabon'	'4.5803'
'Central African Republic'	'5.8027'
'Kazakstan'	'5.9536'
'Chad'	'5.9587'
'Bolivia'	'7.5816'
'Niue'	'7.6923'
'Oman'	'8.2132'
```


## 18.	Cities with High GNP per Capita


```sql
SELECT name, GNP, Population, GNP/population
FROM country
HAVING GNP >= (SELECT AVG(gnp/population) FROM country)
ORDER BY GNP/population DESC;
```

```
name	GNP	Population	GNP/population
Luxembourg	16321.00	435700	0.037459
Switzerland	264478.00	7160400	0.036936
Bermuda	2328.00	65000	0.035815
Brunei	11705.00	328000	0.035686
Liechtenstein	1119.00	32300	0.034644
Cayman Islands	1263.00	38000	0.033237
Denmark	174099.00	5330000	0.032664
Norway	145895.00	4478500	0.032577
United States	8510700.00	278357000	0.030575
Japan	3787042.00	126714000	0.029887
Iceland	8255.00	279000	0.029588
Virgin Islands, British	612.00	21000	0.029143
Austria	211860.00	8091800	0.026182
Germany	2133367.00	82164700	0.025965
Sweden	226492.00	8861400	0.025559
Hong Kong	166448.00	6782000	0.024543
Belgium	249704.00	10239000	0.024388
Singapore	86503.00	3567000	0.024251
France	1424285.00	59225700	0.024048
Finland	121914.00	5171300	0.023575
Netherlands	371362.00	15864000	0.023409
United Kingdom	1378330.00	59623400	0.023117
Monaco	776.00	34000	0.022824
Andorra	1630.00	78000	0.020897
Italy	1161755.00	57680000	0.020141
Ireland	75921.00	3775100	0.020111
Canada	598862.00	31147000	0.019227
```

## 19.	Display Columns with Limit (Rows 31-40)

```sql
SELECT name, population 
FROM city 
ORDER BY population DESC 
LIMIT 10 
OFFSET 30;
```

```
City	Population
'Shenyang'	'4265200'
'Kanton [Guangzhou]'	'4256300'
'Singapore'	'4017733'
'Ho Chi Minh City'	'3980000'
'Chennai (Madras)'	'3841396'
'Pusan'	'3804522'
'Los Angeles'	'3694820'
'Dhaka'	'3612850'
'Berlin'	'3386667'
'Rangoon (Yangon)'	'3361700'
```


> 🔹 Note: The table has been truncated for brevity. See the SQL output for the full list.

---

### 🧠 Conclusion & Final Section 


---

## 🎓 Summary

Throughout this project, I practiced querying real-world datasets using MySQL. From basic selection and filtering to complex joins, aggregations, and text-based searches, each task was designed to reinforce practical SQL skills and build fluency in interacting with relational databases.

By completing these tasks, I gained:

- A better understanding of normalized database structures
- Proficiency in SQL querying patterns
- Practical knowledge in handling datasets, applying logic, and generating useful insights

This project reflects my learning journey as part of the Data Technician training and can serve as a foundation for more advanced SQL applications in analytics, reporting, and backend development.

---

## 📈 What I Learned

- Crafting precise SQL statements
- Using `JOIN`s to connect relational tables
- Aggregating and filtering with `WHERE`, `GROUP BY`, and `HAVING`
- Understanding common database patterns and best practices
- Handling real datasets with real constraints

---

## ☕ Want to Collaborate?

If you're working on a data-related project or need someone who knows their way around SQL, feel free to reach out or fork this repository!

---

