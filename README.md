
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
  - [3.2. Forekomstdiagram](#32-forekomstdiagram)
  - [3.3. EER-modellering](#33-eer-modellering)
    - [3.3.1. Spesialisering og generalisering](#331-spesialisering-og-generalisering)
    - [3.3.2. Kategorier](#332-kategorier)
- [4. Relasjonsdatabaser](#4-relasjonsdatabaser)
  - [4.1. Mapping fra ER-modell](#41-mapping-fra-er-modell)
  - [4.2. Mapping fra EER-modell](#42-mapping-fra-eer-modell)
- [5. Relasjonsalgebra](#5-relasjonsalgebra)
  - [5.10. Gruppering og aggregering](#510-gruppering-og-aggregering)
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

# 3. Datamodellering
Begrep | Forklaring
--- | ---
Miniverden | Domenet. En avgrenset mengde konsepter som skal modelleres.
Database | 
Data |
DBMS |
Database system | DBMS + data

## 3.1. ER-modellering

### 3.1.1. Entiteter og entitetsklasser
Begrep | Forklaring
--- | ---
Entitet | Objekt som eksisterer i miniverdenen. Et element av en entitetsklasse.
Enitetsklasse | Mengden av alle likeartede entiteter som er av samme klasse (type) og har samme egenskaper
Svak entitetsklasse | En entitetsklasse som mangler en naturlig nøkkel, kan av og til identifiseres gjennom en *identifiserende relasjonsklasse* til en annen (identifiserende) entitetsklasse. Dette kalles en *svak entitetsklasse* (siden den mangler en nøkkel). Den må være eksistensavhengig av deltakelse i den identifiserende relasjonsklassen. Den må ha ett eller flere attributt som identifiserer entiteter unikt sammen med nøkkelen til den identifiserende entitetsklassen

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

## 3.2. Forekomstdiagram
 

## 3.3. EER-modellering
### 3.3.1. Spesialisering og generalisering
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

## 5.10. Gruppering og aggregering
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
