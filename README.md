
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
      - [3.1.3.1. Kardinalitet og strukturelle restriksjoner](#3131-kardinalitet-og-strukturelle-restriksjoner)
  - [3.2. Forekomstdiagram](#32-forekomstdiagram)
  - [3.3. EER-modellering](#33-eer-modellering)
    - [3.3.1. Spesialisering og generalisering](#331-spesialisering-og-generalisering)
    - [3.3.2. Kategorier](#332-kategorier)
- [4. Relasjonsdatabaser](#4-relasjonsdatabaser)
  - [4.1. Mapping fra ER-modell](#41-mapping-fra-er-modell)
  - [4.2. Mapping fra EER-modell](#42-mapping-fra-eer-modell)
- [5. Relasjonsalgebra](#5-relasjonsalgebra)
  - [5.1. Operasjoner](#51-operasjoner)
  - [5.2. Gruppering og aggregering](#52-gruppering-og-aggregering)
- [6. SQL](#6-sql)
  - [6.1. Opprette data](#61-opprette-data)
    - [6.1.1. Fremmednøkkelrestriksjoner](#611-fremmednøkkelrestriksjoner)
  - [6.2. Manipulere data](#62-manipulere-data)
    - [6.2.1. Sette inn data - `INSERT INTO`](#621-sette-inn-data---insert-into)
    - [6.2.2. Oppdatere data - `UPDATE`](#622-oppdatere-data---update)
    - [6.2.3. Slette data - `DELETE`](#623-slette-data---delete)
  - [6.3. Spørringer - `SELECT`](#63-spørringer---select)
    - [6.3.1. Spesifisere krav - `WHERE`](#631-spesifisere-krav---where)
    - [6.3.2. Fjerne duplikater - `DISTINCT`](#632-fjerne-duplikater---distinct)
    - [6.3.3. Sortering - `ORDER BY`](#633-sortering---order-by)
    - [6.3.4. Strengsammenlikning - `LIKE`](#634-strengsammenlikning---like)
    - [6.3.5. Data fra flere tabeller: kartesisk produkt og ulike typer join](#635-data-fra-flere-tabeller-kartesisk-produkt-og-ulike-typer-join)
    - [6.3.6. Aggregering](#636-aggregering)
    - [6.3.7. Gruppering - `GROUP BY`](#637-gruppering---group-by)
      - [6.3.7.1. Betingelse etter gruppering - `HAVING`](#6371-betingelse-etter-gruppering---having)
    - [6.3.8. Nøstede spørringer](#638-nøstede-spørringer)
      - [6.3.8.1. Sammenlikningsoperatorer](#6381-sammenlikningsoperatorer)
      - [6.3.8.2. `ANY`, `ALL`](#6382-any-all)
      - [6.3.8.3. `IN`, `NOT IN`](#6383-in-not-in)
      - [6.3.8.4. `EXISTS`](#6384-exists)
      - [6.3.8.5. Union, snitt og differanse](#6385-union-snitt-og-differanse)
      - [6.3.8.6. Nøstede spørringer i `FROM`-delen](#6386-nøstede-spørringer-i-from-delen)
    - [6.3.9. Virtuelle tabeller - `VIEW`](#639-virtuelle-tabeller---view)
- [7. Normalisering](#7-normalisering)
  - [7.1. Restriksjoner](#71-restriksjoner)
  - [7.2. Funksjonelle avhengigheter](#72-funksjonelle-avhengigheter)
    - [7.2.1. Utledningsregler](#721-utledningsregler)
    - [7.2.2. Full funksjonell avhengighet](#722-full-funksjonell-avhengighet)
    - [7.2.3. Fler-verdi-avhengigheter - MVD](#723-fler-verdi-avhengigheter---mvd)
      - [7.2.3.1. Trivielle fler-verdi-avhengigheter](#7231-trivielle-fler-verdi-avhengigheter)
  - [7.3. Tillukning](#73-tillukning)
  - [7.4. Nøkler](#74-nøkler)
  - [7.5. Normalformer](#75-normalformer)
    - [7.5.1. Første normalform - 1NF](#751-første-normalform---1nf)
    - [7.5.2. Andre normalform - 2NF](#752-andre-normalform---2nf)
    - [7.5.3. Tredje normalform - 3NF](#753-tredje-normalform---3nf)
    - [7.5.4. Boyce-Codd normalform - BCNF](#754-boyce-codd-normalform---bcnf)
    - [7.5.5. Fjerde normalform - 4NF](#755-fjerde-normalform---4nf)
  - [7.6. Dekomponeringskriterier](#76-dekomponeringskriterier)
    - [7.6.1. Regler for tapsløs join](#761-regler-for-tapsløs-join)

# 3. Datamodellering
Begrep | Forklaring
--- | ---
Miniverden | De konseptene fra virkeligheten som skal modelleres.
Datamodell | Et sett begreper for å beskrive struktur (hvilke typer data, sammenheger og restriksjoner) og operasjoner (handlinger på data: innsetting, endring, sletting og spørring)
Konseptuelle modeller | For å forstå og dokumentere. For eksempel ER-modeller.
Implementasjonsmodeller | For å realisere. For eksempel relasjonsdatabasemodeller.
Fysiske modeller | Kontroll på lagring og optimalisering. Disse er produktspesifikke modeller.
Database | En strukturert samling av relaterte data.
Informasjon | Data + tolkning
DBMS | Databasehåndteringssystem. Software som styrer lagring og tilgang på data i databasen.
Databasesystem | DBMS + data
Selvbeskrivende DBMS | Inneholder både data og beskrivelser om dataen (metadata). Dette gjøres generelt i DBMS-katalogen.
Selvbeskrivende datamodeller | Inkluderer databeskrivelser i selve dataen. For eksempel XML og JSON.
Program-data uavhengighet | En egenskap som går ut på at strukturendring i datafil ikke medfører at man må endre programmene som har tilgang til dataen.
Flerbrukersstøtte | Flere brukere kan hente ut og lagre data samtidig uten problemer.
Entitetsintegritet | Alle relasjonsskjemaer skal ha en primærnøkkel. Primærnøkler må være unike og kan ikke være `NULL`.
Referanseintegritet | Hvis en fremmednøkkel ikke er `NULL`, må den referere til en eksisterende rad i den tabellen den peker mot.
Databasetilstand | Database-forekomsten (dataene) på et gitt tidspunkt.
Konsistent databasetilstand | At databasen tilfredsstiller alle integritetsregler og relevante reglene fra miniverdenen.
Transaksjon | En serie operasjoner på en database som sammen bevarer databasens konsistens.

## 3.1. ER-modellering
**Viktig!** ER-notasjon: <a href="/assets/ER_notasjon_2017.pdf">Open PDF</a>.

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
Avledet attributt | Stiplet linje | Kan avledes fra andre attributter, trenger ikke lagres eksplisitt
Nøkkelattributt | Understreket | Identifikator for entiteten

### 3.1.3. Relasjoner og relasjonsklasser
Begrep | Forklaring
--- | ---
Relasjon | Sammenheng mellom to eller flere enititeter. Kan ha attributter på samme måte som entiteter. Relasjonen eksisterer ikke uten de entitetene som deltar.
Relasjonsklasse | Mengden av likeartede relasjoner mellom samme enitetsklasser.
Rekursiv relasjonsklasse | Relasjonsklasser der samme entitetsklasse inngår flere ganger. En entitetsklasse kan da ha flere roller i relasjonsklassen.

#### 3.1.3.1. Kardinalitet og strukturelle restriksjoner
Foreleser i emnet foretrekker strukturelle restriksjoner

Begrep | Forklaring
--- | ---
Kardinalitet | Ved bruk av 1 eller N på hver side av relasjonen antydes om relasjonen er en-til-en, en-til-mange eller mange-til-mange. Noteres på *motsatt side* av relasjonen som den aktuelle entiteten. Enkel strek antyder delvis deltagelse (entitetene må ikke delta i relasjonen), dobbel strek antyder total deltagelse (entitetene må delta i relasjonen minst en gang).
Strukturell restriksjon (*min*, *max*) | Antyder at en entitet opptrer i relasjonen minst *min* ganger og maks *max* ganger. Vanlige restriksjoner er (0, 1), (1, 1), (0, n) og (1, n). Noteres på *samme side* av relasjonen som den aktuelle entiteten.

## 3.2. Forekomstdiagram
 
## 3.3. EER-modellering

### 3.3.1. Spesialisering og generalisering
Begrep | Forklaring
--- | ---
Superklasse-subklasserelasjon | Subklassene *arver* egenskapene (attributter og relasjoner) til superklassen, men kan også ha særegne attributter og relasjoner. En subklasse er en delmengde av den tilhørende superklassen.
Total spesialisering | Alle entiteter i superklassen må delta i minst en subklasse. Noteres med dobbel strek.
Overlappende subklasser | En entitet i superklassen kan delta i flere enn en subklasse. Noteres med O eller mangel på notasjon. 
Disjunkte subklasser | En entitet i superklassen kan *ikke* delta i flere enn en subklasse. Noteres med D. 

En entitet kan delta i | **Disjunkt** | **Overlappende**
--- | --- | ---
**Delvis** | 0-1 subklasser | 0-n subklasser
**Total** | 1 subklasse | 1-n subklasser

###  3.3.2. Kategorier
En kategori representerer en samling av entiteter som er en delmenge av entitetene fra ulike  entitetsklasser (kategorienes superklasser). Blir også kalt en union-type. En kategori kan være delvis eller total. En total kategori vil inneholde alle entitetene i unionen av superklassene og markeres med dobbelt strek mellom kategorien og sirkelen.

# 4. Relasjonsdatabaser
Relasjonersdatabaser er bygd opp av tabeller der kolonner angir attributter og rader angir entiteter eller relasjoner.

## 4.1. Mapping fra ER-modell
Konsept | Hvordan mappe
--- | ---
Regulære entitetsklasser | Entitetsklassen får egen tabell. Attributter blir kolonner. Sammensatte attributter splittes opp. Primærnøkkel fra ER-modell brukes.
Svake entitetstyper | Legger til primærnøkkel (fremmednøkkel) fra identifiserende entitetsklasser, sammen med klassens delvise nøkkel. Ellers likt.
Binære 1:1 relasjoner | Fremmednøkkel kan legges i en av entitetsklassetabellene, eller så kan relasjonen få egen tabell.
Binære 1:N relasjoner | Fremmednøkkel kan legges i entiteten med kardinalitet 1, eller så kan relasjonen få egen tabell.
Binære N:N relasjoner | Relasjonen får egen tabell.
Flerverdiattributter | Får egen tabell med fremmednøkkel mot entitetsklassen.
N-ære relasjonsklasser (N > 2) | Får egen tabell med fremmednøkler mot alle tilhørende entitetsklasser.

## 4.2. Mapping fra EER-modell
Konsept | Hvordan mappe
--- | ---
Spesialisering/generalisering | A) Separate tabeller for superklasse og alle subklasser. Kommentar: Data om en entitet spredt over flere tabeller, må bruke join. B) Separate tabeller for subklasser som inkluderer attributter fra superklassen. Kommentar: Krever total og disjunkt spesialisering. C) En tabell som inkluderer attributter fra superklassen og alle subklasser. Kommentar: Ved disjunkt spesialisering kreves et type-attributt. Ved overlappende spesialisering kreves en boolsk type-vektor (en kolonne per type).
Kategorier | En tabell for kategori-entitetsklassen, med typeattributt. Superklassene har som regel ulike nøkler, i tillegg til en surrogat(fremmed)nøkkel mot kategorien.

# 5. Relasjonsalgebra
I relasjonsalgebra bruker vi operasjoner for å manipulere relasjonsdatabasetabeller. Merk at en rad her er en tuppel og en tabell er en mengde av tuppler. Vi vil altså ikke ha duplikater. Operatorene er lukket over tabeller (både input og output er mengder). 

## 5.1. Operasjoner
Operasjon | Operator | Forklaring
--- | --- | ---
Seleksjon | $\sigma_{\text{Betingelse}}(\text{A})$ | Returnerer radene i A som oppfyller betingelsen.
Projeksjon | $\Pi_{\text{Kolonnenavn...}}(\text{A})$ | Returnerer de oppgitte kolonnene i A.
Union | $\cup(\text{A, B})$ | Returnerer unionen av A og B. Krever like kolonnenavn.
Snitt | $\cap(\text{A, B})$ | Returnerer snittet av A og B. Krever like kolonnenavn.
Differanse | $-(\text{A, B})$ | Returnerer radene i A som ikke er i B. Krever like kolonnenavn.
Kartesisk produkt | $\text{X}(\text{A, B})$ | Kombinerer alle rader i A med alle rader i B.
Indre join | $\Join_{\text{Betingelse}}(\text{A, B})$ | Kombinerer radene i A og B som sammen oppfyller betingelsen.
Naturlig join | $*(\text{A, B})$ | Kombinerer radene i A og B der alle kolonner i A og B med samme navn også har samme verdi.
Venstre ytre join | $=\Join_{\text{Betingelse}}(\text{A, B})$ | Kombinerer radene i A og B som sammen oppfyller betingelsen, men inkluderer også resten av radene i A (med `NULL`-verdier i nye kolonner).
Høyre ytre join | $\Join=_{\text{Betingelse}}(\text{A, B})$ | Kombinerer radene i A og B som sammen oppfyller betingelsen, men inkluderer også resten av radene i B (med `NULL`-verdier i nye kolonner).
Full ytre join | $=\Join=_{\text{Betingelse}}(\text{A, B})$ | Kombinerer radene i A og B som sammen oppfyller betingelsen, men inkluderer også resten av radene i A og B (med `NULL`-verdier i nye kolonner).
Omdøping | $\rho_{Tabellnavn(Attributtnavn..)}(\text{A})$ | Returnerer en ny tabell med nye kolonnenavn.
Sortering | $\uparrow \downarrow_{Attributt..}(A)$ | Returnerer en tabell der radene er sortert etter de oppgitte attributtene. Man kan spesifisere ASC (stigende) eller DESC (synkende) rekkefølge.

## 5.2. Gruppering og aggregering
Gjør utregninger "per gruppe".
$$F_{\text{Grupperingsattributter, Aggregeringsfunksjoner}}(A)$$
Visualisert med graf plasseres grupperingsattributtene på venstre side og aggregeringsfunksjonene på høyre side. Man kan også definere et alias med $\text{AS}$. Eksempel: La $\text{A = Bilde(Fotograf, Motiv)}$ Da vil $F_{\text{Fotograf, COUNT(Motiv) AS AntallMotiver}}(A)$ returnere en tabell $\text{Bilde(Fotograf, AntallMotiver)}$ med antall motiver hver fotograf har avbildet.

Funksjon | Forklaring
--- | ---
$\text{SUM(attributt)}$ | Sum
$\text{AVG(attributt)}$ | Gjennomsnitt
$\text{MIN(attributt)}$ | Minimum
$\text{MAX(attributt)}$ | Maksimum
$\text{COUNT(attributt)}$ | Antall verdier (unntatt NULL)
$\text{COUNT(*)}$ | Antall rader


# 6. SQL
Deklarativt spørrespråk ("hva, ikke hvordan") - vi trenger ikke tenke på optimalisering. Ikke mengdeorientert som relasjonsalgebra, resultattabellene kan ha like rader - må be om at duplikater fjernes.

## 6.1. Opprette data
DDL - Data Definition Language
```sql
CREATE TABLE /* opprette tabell */
ALTER TABLE /* endre tabell */
DROP TABLE /* fjerne tabell */
```
```sql
CREATE TABLE Person (
    Pnr     INTEGER NOT NULL,
    Navn    VARCHAR(30),
    Alder   INTEGER,
    CONSTRAINT Person_PK PRIMARY KEY (Pnr));
```

### 6.1.1. Fremmednøkkelrestriksjoner
```sql
CONSTRAINT RestriksjonsNavn FOREIGN KEY (Attributt) REFERENCES FremmedTabell(FremmedAttributt)
    ON UPDATE <>
    ON DELETE <>);
```
Alternativer for `<>`:
- `NO ACTION` (default) / `RESTRICT`: stopper handlingen
- `SET NULL`: setter `NULL`-verdi
- `CASCADE`: oppdaterer/sletter tilsvarende

## 6.2. Manipulere data
DML - Data Manipulation Language

### 6.2.1. Sette inn data - `INSERT INTO`
```sql
INSERT INTO Person VALUES (1, 'Ola', 24);
INSERT INTO Person VALUES (2, 'Kari', 45);
INSERT INTO Person VALUES (3, 'Per', 14);
```
### 6.2.2. Oppdatere data - `UPDATE`
```sql
UPDATE Person
SET Navn = 'Karianne'
WHERE Pnr = 2
```
### 6.2.3. Slette data - `DELETE`
```sql
DELETE FROM Person
WHERE Navn = 'Ola'
```

## 6.3. Spørringer - `SELECT`
Merk: `SELECT *` angir at vi ønsker alle attributter.
```sql
SELECT attributt, ...
FROM tabell, ...
WHERE betingelse
```
Relasjonsalgebraekvivalent:
$$\Pi_{\text{attributt, ...}}(\sigma_{\text{betingelse}}(\text{tabell}))$$

### 6.3.1. Spesifisere krav - `WHERE`
Følgende operator virker som forventet.
Operator |
--- |
`AND`, `OR` |
`=`, `!=`, `<`, `>`, `<=`, `>=` |

Merk: `<>` er det samme som `!=`
```sql
-- Finner personnummer og navn for personer over 20
SELECT Pnr, Navn
FROM Person
WHERE Alder > 20
```

### 6.3.2. Fjerne duplikater - `DISTINCT`
```sql
SELECT DISTINCT Navn
FROM Person
```

### 6.3.3. Sortering - `ORDER BY`
```sql
SELECT Navn
FROM Person
ORDER BY Alder ASC
```

### 6.3.4. Strengsammenlikning - `LIKE`
`%` angir vilkårlig antall tegn. `_` angir ett tegn.
```sql
-- Finner alle attributter for personer med navn som begynner på P
SELECT *
FROM Person
WHERE Navn LIKE 'P%'
```

### 6.3.5. Data fra flere tabeller: kartesisk produkt og ulike typer join
Plasseres i `FROM`-delen. Gitt tabeller `A` og `B`:
Funksjon | Beskrivelse
--- | ---
`A, B` | Kartesisk produkt
`A CROSS JOIN B` | Kartesisk produkt
`A NATURAL JOIN B` | Natural join
`A (INNER) JOIN B` | Indre join
`A LEFT (OUTER) JOIN B` | Venstre ytre join
`A RIGHT (OUTER) JOIN B` | Høyre ytre join
`A FULL (OUTER) JOIN B` | Full ytre join

Parenteser antyder frivillig spesifisering. Se [relasjonsalgebra](#5-relasjonsalgebra) for nærmere forklaring av funksjonene.

Betingelse | Beskrivelse
--- | ---
`NATURAL` | Natural join
`ON betingelse` | Spesifiserer join-betingelsen
`USING (attributt, ...)` | Spesifiserer hvilke attributter som må være like i de to tabellene

```sql
-- Finner navn på hund og eier for personer over 60 år
SELECT Person.Navn, Hund.Navn
FROM Person INNER JOIN Hund ON Person.Pnr = Hund.EierPnr
WHERE Person.Alder > 60
```

### 6.3.6. Aggregering
Se [aggregering i relasjonsalgebra](#52-gruppering-og-aggregering).
Funksjonene ignorerer `NULL`-verdier. Med `DISTINCT` opererer funksjonene på unike verdier. `AS` definerer et alias.
```sql
-- Finner snittalderen av alle personer
SELECT AVG(Alder) AS SnittAlder
FROM Person
```

### 6.3.7. Gruppering - `GROUP BY`
Definerer grupper (partisjoner) av rader. Må komme etter en eventuell `WHERE`.
```sql
-- Finner snittalderen for hvert navn
SELECT AVG(Alder) AS SnittAlder
FROM Person
GROUP BY Navn
```

#### 6.3.7.1. Betingelse etter gruppering - `HAVING`
Som `WHERE`, men *etter* gruppering.
```sql
-- Finner snittalderen for hvert navn, men kun hvis snittet over 60
SELECT Navn, AVG(Alder) AS SnittAlder
FROM Person
GROUP BY Navn
HAVING SnittAlder > 60
```

### 6.3.8. Nøstede spørringer
I `WHERE`-delen kan vi sammenlikne med resultatet fra en spørring. I `FROM`-delen kan vi gjøre en ny spørring på resultatet av en spørring.

#### 6.3.8.1. Sammenlikningsoperatorer
`=, !=, <, >, <=, >=` virker som forventet.

```sql
-- Finner navnet til den eldste personen
SELECT Navn
FROM Person
WHERE Alder = (SELECT MAX(Alder) FROM Person)
```

#### 6.3.8.2. `ANY`, `ALL`
```sql
-- Finner navnet til den eldste personen (alternativ måte)
SELECT Navn
FROM Person
WHERE Alder >= ALL (SELECT Alder FROM Person)
```

#### 6.3.8.3. `IN`, `NOT IN`
```sql
-- Finner snittalderen til forfattere
SELECT AVG(Alder)
FROM Person
WHERE Navn IN (SELECT Forfatter FROM Bok)
```

#### 6.3.8.4. `EXISTS`
Dette er en korrelert del-spørring, dvs. at den sender inn data. (Om Person-entiteter i dette tilfelle).
```sql
-- Finner navn på personer som ikke jobber med noen andre personer
SELECT Navn 
FROM Person
WHERE NOT EXISTS (
    SELECT *
    FROM JobberMed
    WHERE JobberMed.PnrA = Person.Pnr OR JobberMed.PnrB = Person.Pnr
)
```


#### 6.3.8.5. Union, snitt og differanse
Krever kompatible operandtabeller (like kolonnenavn).

Funksjon | Forklaring
--- | ---
`UNION` | Union
`INTERSECT` | Snitt
`EXCEPT` | Minus
`UNION ALL` | Union (beholder duplikater)
`INTERSECT ALL` | Snitt (beholder duplikater)
`EXCEPT ALL` | Minus (beholder duplikater)

```sql
-- Finner navn som brukes på både personer og hunder
SELECT Navn FROM Person
INTERSECT
SELECT Navn FROM Hund
```

#### 6.3.8.6. Nøstede spørringer i `FROM`-delen
I `FROM`-delen kan vi gjøre en ny spørring på resultatet av en spørring. Lager en midlertidig tabell.
```sql
-- Finner antall arbeidere for ingeniøryrker med under 1000 arbeidere
SELECT Yrke AntallArbeidere
FROM (
  SELECT Yrke, COUNT(Pnr) AS AntallArbeidere
  FROM Person
  GROUP BY Yrke
)
WHERE Yrke LIKE '%ingeniør' AND AntallArbeidere < 1000
```

### 6.3.9. Virtuelle tabeller - `VIEW`
Views er tabeller som er avledet ut fra tabeller som er lagret i databasen. Hvorfor: Spørreforenkling, sikkerhet og ytelse.

```sql
CREATE VIEW Forelder(ForelderPnr, ForelderNavn, BarnPnr, BarnNavn)
AS SELECT F.Pnr, F.Navn, B.Pnr, B.Navn
FROM Person AS F INNER JOIN Person AS B
ON (F.Pnr = B.MorPnr OR F.Pnr = B.FarPnr)
```

# 7. Normalisering
Vi ønsker å unngå redundans (lagring av samme informasjon flere ganger) og innsettings-, oppdaterings- og slettings-anomalier.

## 7.1. Restriksjoner
Begrep | Forklaring
--- | ---
Implisitte restriksjoner | Er en del av datamodellen og håndheves derfor alltid av DBMS.
Eksplisitte restriksjoner | Kan uttrykkes i datamodellen (databaseskjemaet). Håndheves av DBMS. Eksempler: Primærnøkkel, fremmednøkkel, datatyper, verdi-begrensninger, etc.
Applikasjonsbaserte restriksjoner (business rules) | Må håndteres utenfor datamodellen (av applikasjonsprogrammene).

## 7.2. Funksjonelle avhengigheter

Notasjon | Forklaring
--- | ---
$R(A, B, ...)$ | Skjema for tabellen. A, B, ... er attributter.
$X \rightarrow Y$ | $Y$ er funksjonelt avhengig av $X$
$r(R)$ | Tabellforekomsten
$t_i \in r(R)$ | Rad i tabellforekomsten
$t_i[A]$ | Radens verdi for attributtet $A$
$X \subseteq R$ | En delmengde av attributtene i $R$

Forkortes gjerne til FA. 

$X \rightarrow Y$, der $X, Y \subseteq R$ uttrykker en restriksjon på alle lovlige tabellforekomster for $R$ (en funksjonell avhengighet). Alle rader (tuppler), $t_j$ pg $t_i$, i en forekomst $r(R)$ som har samme verdier for attributtene i $X$ (dvs. $t_i[X] = t_j[X]$), *må* ha samme verdier for attributtene i $Y$ (dvs. $t_i[Y] = t_j[Y]$).

Kort sagt: FA-en $\text{PersonNummer} \rightarrow \text{Navn}$ tilsier at alle rader med samme $\text{PersonNummer}$ må ha samme $\text{Navn}$.

### 7.2.1. Utledningsregler
Disse er sjelden nødvendige.
Navn | Regel
--- | ---
IR-1 (reflexive) | ${ Y \subseteq X }$ gir $X \rightarrow Y$
IR-2 (augmentation) | ${ X \rightarrow Y }$ gir $XZ \rightarrow YZ$
IR-3 (transitive) | ${ X \rightarrow Y, \, Y \rightarrow Z }$ gir $X \rightarrow Z$
IR-4 (decomposition) | ${ X \rightarrow YZ }$ gir $X \rightarrow Y$
IR-5 (additive) | ${ X \rightarrow Y, \, X \rightarrow Z }$ gir $X \rightarrow YZ$
IR-6 (pseudotransitive) | ${ X \rightarrow Y, \, WY \rightarrow Z }$ gir $WX \rightarrow Z$
$X, Y, Z, W \subseteq R$ (mengden av alle attributter)

### 7.2.2. Full funksjonell avhengighet
En funksjonell avhengighet $X \rightarrow Y$ er en full funksjonell avhengighet hvis det er umulig å fjerne et attributt, $A \in X$, og ha $(X - {A}) \rightarrow Y$. Kan tenkes på som at $X$ er en [minimal nøkkel](#72-nøkler) for $Y$.

### 7.2.3. Fler-verdi-avhengigheter - MVD
La $X, Y$ være delmengder av $R$. En fler-verdi-avhengighet $X \twoheadrightarrow Y$ betyr at mengden $Y$-verdier som er assosiert med en $X$-verdi bestemmes av $X$ og som er uavhengig av andre attributter. Dette kalles også for en MVD (multi-value dependency).

Eksempel: I en tabell over hvilke hobbyer personer har $\text{Hobbyer(PersonNummer, Hobby)}$ er $\text{PersonNummer} \twoheadrightarrow \text{Hobby}$. Det er en mengde Hobby-verdier som er assosiert med en PersonNummer-verdi og uavhengig av andre attributter.

#### 7.2.3.1. Trivielle fler-verdi-avhengigheter
$X \twoheadrightarrow Y$ er triviell hvis $Y$ er en delmengde av $X$ eller $X \cup Y = R$. Trivielle MVD-er utelates restriksjoner i 4NF.

## 7.3. Tillukning
Anta $F$ er en mengde funksjonelle avhengigheter. Tillukningen til $F$ er mengden av alle funksjonelle avhengigheter som kan utledes av $F$ og er gitt ved følgende
$$F^+ = \{ X \rightarrow Y \,|\, X \rightarrow Y \text{ kan utledes fra FA-ene i F} \}$$

Anta $R$ og $F$, $X \subseteq R$. Tillukningen til $X$ er mengden av alle attributter som er funksjonelt avhengige av $X$ og er gitt ved følgende
$$X^+ = \{ Y \in R \,|\, X \rightarrow Y \in F^+ \}$$

## 7.4. Nøkler

Begrep | Forklaring
--- | ---
Nøkkelattributt | Et attributt som inngår i en eller flere kandidatnøkler
Ikke-nøkkelattributt | Et attributt som ikke inngår i noen kandidatnøkler
Supernøkkel | En mengde attributter som sammen danner en unik identifikator
Nøkkel/kandidatnøkkel | En minimal supernøkkel (inneholder ingen flere attributter enn nødvendig)
Primærnøkkel | Primærnøkkelen velges blant kandidatnøklene
Sekundærnøkkel | En kandidatnøkkel som ikke er primærnøkkel. Her kan vi velge å tillate `NULL`-verdier.

## 7.5. Normalformer
Alle høyere normalformer forutsetter de lavere normalformene.

### 7.5.1. Første normalform - 1NF
En tabell er på 1NF hvis og bare hvis alle attributter har **en enkelt verdi** fra domenet.

### 7.5.2. Andre normalform - 2NF
En tabell er på andre normalform hvis og bare hvis det ikke finnes noen ikke-nøkkelattributter som er delvis avhengig av en kandidatnøkkel.

### 7.5.3. Tredje normalform - 3NF
En tabell er på 3NF hvis og bare hvis det for alle tabellens funksjonelle avhengigheter på formen $X \rightarrow Y$ er slik at enten
- X er en supernøkkel i tabellen, eller 
- Y er et nøkkelattributt i tabellen.

### 7.5.4. Boyce-Codd normalform - BCNF
En tabell er på BCNF hvis og bare hvis det for alle tabellens funksjonelle avhengigheter på formen $X \rightarrow Y$, er slik at $X$ er en supernøkkel i tabellen.

### 7.5.5. Fjerde normalform - 4NF
En tabell er på 4NF hvis og bare hvis det for alle ikke-trivielle MVD-er $X \twoheadrightarrow Y$, er slik at $X$ er en supernøkkel.

## 7.6. Dekomponeringskriterier
Dekomponeringskriterium | Forklaring
--- | ---
Normalform | Ser på hver enkelt projeksjon (tabell), og ønsker så høy normalform som mulig.
Attributtbevaring | Alle attributter i $R$ må finnes i minst en av projeksjonene, slik at den samme dataen kan lagres.
Bevaring av funksjonelle avhengigheter | Alle funksjonelle avhengigheter i $F$ skal finnes i en eller flere $R_i$-er eller kunne utledes fra FA-ene som gjelder i $R_i$-ene.
Tapsløs-join-egenskapen | Må kunne komme tilbake til utgangspunktet, og ikke kunne skape falske data. Kan sikres ved å sjekke hver oppdeling med snittregelen, eller bruke tabellmetoden (algoritme 15.3 i læreboka).

### 7.6.1. Regler for tapsløs join
Begrep | Forklaring
--- | ---
Tabellmetoden | (algoritme 15.3 i læreboka)
Snittregelen | Dekomponeringen har tapsløs-join-egenskapen hvis felles attributter (snittet) i $R_1$ og $R_2$ er en supernøkkel i en eller begge tabellene: $R_1 \cap R_2 \rightarrow R_1$ eller $R_1 \cap R_2 \rightarrow R_2$.
Fagins teorem | La $A, B$ være delmengder av $R$ og la $C = R - AB$. Projeksjonene $AB$ og $AC$ har tapsløs-join-egenskapen hvis og bare hvis $A \twoheadrightarrow B$ eller $A \twoheadrightarrow C$.
