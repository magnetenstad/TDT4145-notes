
# 1. TDT4145 - Datamodellering og databasesystemer
Følgende notater dekker første halvdel av faget.

# 2. Innholdsfortegnelse
- [1. TDT4145 - Datamodellering og databasesystemer](#1-tdt4145---datamodellering-og-databasesystemer)
- [2. Innholdsfortegnelse](#2-innholdsfortegnelse)
- [3. Datamodellering](#3-datamodellering)
  - [3.1. ER-modellering](#31-er-modellering)
    - [3.1.1. Entiteter og entitetsklasser](#311-entiteter-og-entitetsklasser)
    - [3.1.2. Attributter](#312-attributter)
    - [3.1.3. Relasjoner og relasjonsklasser](#313-relasjoner-og-relasjonsklasser)
      - [3.1.3.1. Kardinalitet](#3131-kardinalitet)
  - [3.2. Forekomstdiagram](#32-forekomstdiagram)
  - [3.3. EER-modellering](#33-eer-modellering)
    - [3.3.1. Spesialisering og generalisering](#331-spesialisering-og-generalisering)
    - [3.3.2. Kategorier](#332-kategorier)
- [4. Relasjonsdatabaser](#4-relasjonsdatabaser)
  - [4.1. Mapping fra ER-modell](#41-mapping-fra-er-modell)
  - [4.2. Mapping fra EER-modell](#42-mapping-fra-eer-modell)
- [5. Relasjonsalgebra](#5-relasjonsalgebra)
  - [5.1. Gruppering og aggregering](#51-gruppering-og-aggregering)
- [6. SQL](#6-sql)
  - [6.1. Opprette data](#61-opprette-data)
  - [6.2. Endre data](#62-endre-data)
  - [6.3. Spørringer](#63-spørringer)
    - [6.3.1. Spesifisere krav - `WHERE`](#631-spesifisere-krav---where)
    - [6.3.2. Fjerne duplikater - `DISTINCT`](#632-fjerne-duplikater---distinct)
    - [6.3.3. Sortering `ORDER BY`](#633-sortering-order-by)
    - [6.3.4. Strengsammenlikning - `LIKE`](#634-strengsammenlikning---like)
    - [6.3.5. Kartesisk produkt](#635-kartesisk-produkt)
    - [6.3.6. Ulike typer join](#636-ulike-typer-join)
    - [6.3.7. Aggregering](#637-aggregering)
    - [6.3.8. Gruppering](#638-gruppering)
    - [6.3.9. Betingelse etter gruppering - `HAVING`](#639-betingelse-etter-gruppering---having)
    - [6.3.10. Nøstede spørringer](#6310-nøstede-spørringer)
      - [6.3.10.1. Sammenlikningsoperatorer](#63101-sammenlikningsoperatorer)
      - [6.3.10.2. `ANY`, `ALL`](#63102-any-all)
      - [6.3.10.3. `IN`, `NOT IN`](#63103-in-not-in)
      - [6.3.10.4. `EXISTS`](#63104-exists)
      - [6.3.10.5. Union, snitt og differanse](#63105-union-snitt-og-differanse)
      - [6.3.10.6. Nøstede spørringer i `FROM`-delen](#63106-nøstede-spørringer-i-from-delen)
    - [6.3.11. Virtuelle tabeller - `VIEW`](#6311-virtuelle-tabeller---view)
- [7. Normalisering](#7-normalisering)
  - [Tillukning](#tillukning)
    - [Tillukningen til en mengde FA-er: F^+^](#tillukningen-til-en-mengde-fa-er-f)
    - [Tillukningen til en mengde attributter: X^+^](#tillukningen-til-en-mengde-attributter-x)
  - [Nøkler](#nøkler)
  - [Normalformer](#normalformer)
  - [Dekomponering](#dekomponering)

# 3. Datamodellering
Begrep | Forklaring
--- | ---
Miniverden | Domenet. En avgrenset mengde konsepter som skal modelleres.
Datamodell | Et sett begreper for å beskrive struktur (hvilke typer data, sammenheger og restriksjoner) og operasjoner (handlinger på data: innsetting, endring, sletting og spørring)
Konseptuelle modeller | For å forstå og dokumentere. For eksempel ER-modell.
Implementasjonsmodeller | For å realisere. For eksempel Relasjonsdatabasemodell.
Fysiske modeller | Kontroll på lagring og optimalisering. Disse er produktspesifikke modeller.
Database | Et sett av relaterte data.
Data |
Informasjon | Data + tolkning
DBMS | Databasehåndteringssystem. Software som styrer lagring og tilgang på data i databasen.
Databasesystem | DBMS + data
Selvbeskrivende DBMS | Vil si at den inneholder både data og beskrivelser om dataen (metadata). Dette gjøres generelt i DBMS-katalogen.
Selvbeskrivende datamodeller | Inkluderer databeskrivelser i selve dataen. For eksempel XML og JSON.
Program-data uavhengighet | En egenskap som går ut på at strukturendring i datafil ikke medfører at man må endre programmene som har tilgang til dataen.
Flerbrukersstøtte | Flere brukere kan hente ut og lagre data samtidig uten at det er problem.
Transaksjoner |


## 3.1. ER-modellering

### 3.1.1. Entiteter og entitetsklasser
Begrep | Forklaring
--- | ---
Entitet | Objekt som eksisterer i miniverdenen. Et element av en entitetsklasse.
Enitetsklasse | Mengden av alle likeartede entiteter som er av samme klasse (type) og har samme egenskaper
Svak entitetsklasse | En entitetsklasse der nøkkelen (delvis nøkkel) bygger på nøkkelen fra en annen *identifiserende entitetsklasse*, gjennom en *identifiserende relasjonsklasse*. Den må være eksistensavhengig av deltakelse i den identifiserende relasjonsklassen.

### 3.1.2. Attributter
Attributter beskriver entiteter. Hvert attributt henter sine mulige verdier fra et domene (datatype).

Type attributt | Notasjon | Forklaring
--- | --- | ---
Enkel attributt (Standard) | Ingen | Attributt
Flerverdiattributt | Dobbel linje | Kan holde flere verdier
Sammensatt attributt | Har egne subattributter | Har egne subattributter
Avledet attributt | Stiplet linje | Attributtet kan avledes, og trenger ikke lagres eksplisitt
Nøkkelattributt | Understreket | Entydig identifikator for entiteten

### 3.1.3. Relasjoner og relasjonsklasser
Begrep | Forklaring
--- | ---
Relasjon | Sammenheng mellom to eller flere enititeter. Kan ha attributter på samme måte som entiteter. Relasjonen eksisterer ikke uten de entitetene som deltar.
Relasjonsklasse | Mengden av likeartede relasjoner mellom samme enitetsklasser.
Rekursiv relasjonsklasse | Relasjonsklasser der samme entitetsklasse inngår flere ganger. En entitetsklasse kan da ha flere roller i relasjonsklassen.

#### 3.1.3.1. Kardinalitet


## 3.2. Forekomstdiagram
 

## 3.3. EER-modellering
### 3.3.1. Spesialisering og generalisering
En entitet kan delta i | **Disjunkt** | **Overlappende**
--- | --- | ---
**Delvis** | 0-1 subklasser | 0-n subklasser
**Total** | 1 subklasse | 1-n subklasser

###  3.3.2. Kategorier
# 4. Relasjonsdatabaser
## 4.1. Mapping fra ER-modell
## 4.2. Mapping fra EER-modell
# 5. Relasjonsalgebra
Operasjon | Operator | Forklaring
--- | --- | ---
Projeksjon | $\sigma$
Seleksjon | $\Pi$
Union | $\cup$
Snitt | $\cap$
Differanse | $-$
Kartesisk produkt | $\text{X}$
Indre join | $\Join$
Naturlig join | $*$
Ytre join | TODO
Omdøping | $\rho$
Sortering | $\uparrow \downarrow$

## 5.1. Gruppering og aggregering
Funksjon | Forklaring
--- | ---
SUM(attributt) | Sum
AVG(attributt) | Gjennomsnitt
MIN(attributt) | Minimum
MAX(attributt) | Maksimum
COUNT(attributt) | Antall verdier (unntatt NULL)
COUNT(DISTINCT attributt) | Antall unike verdier (unntatt NULL)
COUNT(*) | Antall rader


# 6. SQL
## 6.1. Opprette data
## 6.2. Endre data
## 6.3. Spørringer
### 6.3.1. Spesifisere krav - `WHERE`
### 6.3.2. Fjerne duplikater - `DISTINCT`
### 6.3.3. Sortering `ORDER BY`
### 6.3.4. Strengsammenlikning - `LIKE`
### 6.3.5. Kartesisk produkt
### 6.3.6. Ulike typer join

Funksjon | Beskrivelse
`(INNER) JOIN` | Returns records that have matching values in both tables
`LEFT (OUTER) JOIN` | Returns all records from the left table, and the matched records from the right table
`RIGHT (OUTER) JOIN` | Returns all records from the right table, and the matched records from the left table
`FULL (OUTER) JOIN` | Returns all records when there is a match in either left or right table

### 6.3.7. Aggregering
### 6.3.8. Gruppering
### 6.3.9. Betingelse etter gruppering - `HAVING`
### 6.3.10. Nøstede spørringer
#### 6.3.10.1. Sammenlikningsoperatorer
#### 6.3.10.2. `ANY`, `ALL`
#### 6.3.10.3. `IN`, `NOT IN`
#### 6.3.10.4. `EXISTS`
#### 6.3.10.5. Union, snitt og differanse
#### 6.3.10.6. Nøstede spørringer i `FROM`-delen
### 6.3.11. Virtuelle tabeller - `VIEW`
# 7. Normalisering

## Tillukning

### Tillukningen til en mengde FA-er: F^+^
Anta $F$ er en mengde funksjonelle avhengigheter. Da er 
$F^+ = \{ X \rightarrow Y | X \rightarrow Y \text{ kan utledes fra FA-ene i F} \}$

### Tillukningen til en mengde attributter: X^+^
Anta $R$ og $F$, $X \subseteq R$. Da er $ X^+ = \{ Y \in R | X \rightarrow Y \in F^+ \}$ Dette er mengden av alle attributter som er funksjonelt avhengige av $X$.

## Nøkler

Type nøkkel | Forklaring
--- | ---
Nøkkelattributt | Et attributt som er med i en eller flere supernøkler
Supernøkkel | Mengde attributter som sammen er en identifikator
Kandidatnøkkel | En minimal supernøkkel
Nøkkel | 

## Normalformer
FØRSTE NORMALFORM

Atomiske verdier

ANDRE NORMALFORM

En tabell er på 2NF hvis ingen ikke-nøkkel-attributter er delvis avhengig av en (kandidat-)nøkkel.

TREDJE NORMALFORM

En tabell er på 3NF hvis det for alle ikke-trivielle funksjonelle avhengigheter X -> A som gjelder for tabellen, er slik at 
(a) X er en supernøkkel i tabellen eller 
(b) A er et nøkkelattributt i tabellen.

BOYCE-CODD NORMALFORM

En tabell er på BCNF hvis det for alle ikke-trivielle funksjonelle avhengigheter X -> Y som gjelder for tabellen, er slik at X er en supernøkkel i tabellen.

## Dekomponering

