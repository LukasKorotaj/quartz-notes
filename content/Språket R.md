---
id: R
aliases:
  - R
  - language
tags: []
---

# Lite om R
Språket R är ett språk som används för att att analysera data och statistisk analys. R är öppen källkod. 
# R basics
R används i terminalen med `R` kommando. Man skriver i R så här:
```R
> 5 + 5
[1] 10
```
Det viktiga att veta är att R är dynamiskt typad[^dynamic].

[^dynamic]: Interpretatorn gissar typen.

Exempel:  
```R
> a <- 1
> b <- "hej"
> a
[1] 1
> b
[1] "hej"
```

Här ser man att `<-` används för att tilldela värde till variabel. `->` och `=` fungerar också.

## Vektorer
Man kan lagra flera värden i en vektor, t ex
```R
> a <- 1:10
> a
[1] 1 2 3 4 5 6 7 8 9 10
> b <- c(a, 2, 3)
> b
[1] 1 2 3 4 5 6 7 8 9 10 2 3
```
Funktionen `c` heter `combine` och används för att kombinera vektorer.

Funktionen `length()` kan användas för att hitta längden för en vektor.
```R
> a <- 1:10
> length(a)
[1] 10
```

Man kan komma åt innehållet i en vektor med `[]`, t.ex.
```R 
> a[7] <- 77
> a
 [1]  1  2  3  4  5  6 77  8  9 10
```
R använder 1-based indexing[^indexing].  

[^indexing]: Index börjar från 1. Så den första elementen är 1.

Vektorerna kan användas i funktioner, t.ex.

```R
> 5*c(2, 4)
[1] 10 20
> nchar(c("hej", "R"))
[1] 3 1
```

`nchar` returnerar antalet tecken i en sträng.

Man kan namnge element med `names()`, t.ex.
```R
> daylength <- c(4222.6 , 2802.0 , 24, 708.7)
> names(daylength) <- c(" Mercury", "Venus", "Earth", "Moon ")
> daylength
Mercury     Venus   Earth   Moon
4222.6      2802.0  24.0    708.7
> names(daylength)
[1] "Mercury" "Venus" "Earth" "Moon"
```

## Grundläggande typer
* `numeric`: Integer och Double.
* `character`: Representerar text i strängar.
* `logical`: Boolean, `TRUE` eller `FALSE`, `T` eller `F`.
* `complex': Används för att representera komplexa tal.

En vektor kan innehålla endast en typ och man kan ta reda på typen med funktionen `mode()`.

# Objekt för att representera data
Några objekt är:  
* [[#Vektorer]]
* [[#Matriser]] - Lagrar data i två dimensioner.
* 'Array' - För att lagra data i mer än två dimensioner. All data måste vara av samma typ.
* [[#Listor]] - Kan lagra data av olika typer och olika sorters objekt.
* [[#Dataramar]] - Lagra data i rader och kolumner. Kolumnerna kan vara av olika typ.
* Faktorer - Har två huvudkomponenter
    * Nivåer: De unika kategorierna eller grupperna som faktorn kan ta. Till exempel, om du har en faktor för kön, kan nivåerna vara "man" och "kvinna".
    * Värden: De observerade värdena i datasetet som hänvisar till någon av nivåerna.

Funktionen `str()` kan användas för att ta reda på typ av objekt man har.

## Matriser
Matriser kan skapas med:  
```R
matrix(data = NA , nrow = 1, ncol = 1, byrow = FALSE ,
dimnames = NULL)
```

Funktionen har fem argument `(data, nrow, ncol, byrow, dimnames)`. Det som står efter `=` är defaultvärden. 
Med `byrow` menas om data fylls in rad för rad eller kolumn för kolumn. Med `dimnames` kan man ange namn för dimensioner.  
```R
> m <- matrix(c("A", "B", "C", "D"), 2, 2)
> m
     [,1] [,2]
[1,] "A"  "C"
[2,] "B"  "D"
```
Man kan komma åt element genom att ange positionen `[raden,kolumnen]`. 
```R
> m[2 ,2]
[1] "D"
> m[,2]
[1] "C" "D"
```

## Listor
Lostor kan skapas med `list(...)`.  

```R
> L <- list ("A", matrix (1:4, 2, 2))
> str(L)
List of 2
    $ : chr "A"
    $ : int [1:2, 1:2] 1 2 3 4
> str(L[1])
List of 1
    $ : chr "A"
> str(L[[1]])
chr "A"
```

Men `[1]` tar man ut första elementen i listan och med `[[1]]` tar man ut den verkliga första elementen.  

Man kan också namnge elementen i en lista. Och komma åt element med `$namn`. 
```R
> L2 <- list(Cities = c(" Lund", "Malmo "), Populations = c (87000 , 280000))
> L2$Cities
[1] "Lund" "Malmo"
```
Man behöver inte använda namn, men det är enklare att hålla reda på namnen än index.  

Man kan ändra namn med funktionen `names()`.
```R
> names(L2)
[1] "Cities" "Populations"
> names(L2) <- c(" stader", "invanare ")
> L2
    $stader
    [1] "Lund" "Malmo"
    $invanare
    [1] 87000 280000
```

## Dataramar

Lagrar och behandlar data. Man skapar en ny dataram med funktionen `data.frame()`:
```R
> name <- c(" Paul", "Bodil", "Karla", "Diana ")
> age <- c(25, 30, 22, 22)
> persons
<- data.frame(name , age)
> persons
    name    age
1   Paul    25
2   Bodil   30
3   Karla   22
4   Diana   22
```
Nu kan vi till exempel räkna ut medelvärde med `mean(persons$age)`. En användbar funktion för dataramar är `summary()`:
```R
> summary(persons)
     name                age
 Length:4           Min.   :22.00
 Class :character   1st Qu.:22.00
 Mode  :character   Median :23.50
                    Mean   :24.75
                    3rd Qu.:26.25
                    Max.   :30.00
```
I en dataram kan man indexera som i en matris:

```R
> persons[3,] # third row
   name age
3 Karla  22
> persons[,1] # first column
[1] "Paul"   "Bodil"  "Karla"  "Diana "
> persons[-c(2,3),] # alla rader förutom den andra och den tredje
    name age
1   Paul  25
4 Diana   22
> persons[, "age"] # using column name as index
[1] 25 30 22 22
> persons[1]
    name
1   Paul
2  Bodil
3  Karla
4 Diana
> persons$name # first column
[1] "Paul"   "Bodil"  "Karla"  "Diana "
```
`#` är kommentarstecknet. `-` betyder alla utom.  

Man kan omvandla t.ex matriser och listor till dataramar med `as.data.frame()`.
# Urval av data
Det finns flear sätt att välja vilken data man vill se. Exempel:
```R
> a <- 2*(1:10) # skapar en vektor a
> a[4] # visa element 4
> a[c(2,3)] # visa element 2 och 3
> a[-5] # visa allting forutom element 5
> a[c(T,T,T,F...)] # man kan använda true och false.
> a[a<10] # alla element mindre än 10
```
# Operationer och vanliga funktioner
```R
$ @  # Komponent, @*
[ [[ # Indexering
^    # Exponent
+-   # Unära plus och minus
:: ::: # Åtkomst av variabler i 'namespace' *
:   # Sekvens
%any%# Special-operator
*/   # Multiplikation, division
+ -  # Binära addition och subtraktion
< > <= >= == != # Jämfringar
!    # Negation
& && # Och
| || # Eller
~    # För att beskriva modeller
-> ->> # Tilldelning, tilldelning i 'enclosing environment'
<- <<- # Tilldelning, tilldelning i 'enclosing environment'
=    # Tilldelning (motsvarar '<-')
?    # Hjälp
```
^tabell101

```R
sum(..., na.rm = FALSE)    # Sum function
prod(..., na.rm = FALSE)   # Product function
cumsum(x), cumprod(x)      # Cumulative sum and product
mean(x, trim = 0, na.rm = FALSE, ...)  # Mean value
median(x, na.rm = FALSE)   # Median
var(x, na.rm = FALSE)      # Variance
sd(x, na.rm = FALSE)       # Standard deviation
exp(x)                     # Exponential function
log(x, base = exp(1)), log10(x), log2(x)  # Logarithms (natural, base 10, base 2)
max(..., na.rm = FALSE)    # Maximum value
min(..., na.rm = FALSE)    # Minimum value
range(..., na.rm = FALSE)  # Range (min and max)
which.max(x), which.min(x)  # Which value is max/min
sqrt(x), abs(x)            # Square root and absolute value
sin(x), cos(x), tan(x)     # Sine, cosine, tangent functions (radians)
round(x, digits = 0)        # Rounding (digits decimal places)
floor(x), ceiling(x)       # Rounding down/up
factorial(x), choose(n, k)  # Factorial and combination function (n! / ((n −k)!k!))
```
^tabell102
