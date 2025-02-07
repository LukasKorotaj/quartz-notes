---
id: Ordlista
aliases: []
tags: []
---

# Om ordlistan 

Jag kommer inte lägga alla ord eller begrepp i ordlistan. Ordlistan är här så att jag slipper ha en massa notes i EDAA01 directory. Begrepp och ord som inte förtjänar sin egen note kommer att vara här. Alltså alla grejer som kan vara en footnote kommer jag lägga här så att jag kan linka till dem, så allting blir snyggt.
# Abstrakta Klasser
En **abstrakt klass** är en klass som inte kan skapas som ett eget objekt utan är tänkt att ärvas av andra klasser. Den är typ som en mall. Man skapar en abstrakt klass med nyckelordet `abstract`.

```java
abstract class Djur {
    String color;

    Djur(String color) { // Konstruktor
        this.color = color;
    }

    abstract void ljud();  // Abstrakt metod 
    
    void andas() {  // Vanlig metod (har implementation)
        System.out.println("Djuret andas.");
    }
}

class Hund extends Djur {

    Hund(String color) {
        super(color); // Anropar Djurs konstruktor
    }

    void ljud() {  // Implementerar den abstrakta metoden
        System.out.println("Voff voff!");
    }
}
```
^Djurklass

# Abstrakta Metoder
En **abstrakt metod** är en metod utan implementation. Den **måste** finnas i en [[#Abstrakta Klasser|abstrakt klass]] och **måste** implementeras av klasser som ärver den. I [[#^Djurklass|klassen Djur]] är en abstrakt metod `ljud()`. Man skapar en abstrakt metod med nyckelordet `abstract` före typen.

# Abstrakta Datatyper

**==Fill this out. There is a whole lecture about it==**
# Klass
En **klass (konkret klass)** är en mall som beskriver hur [[#objekt]] skapas och fungerar. Klassen definerar **variabler** och **metoder** som objekt av klassen kommer att ha.

# Objekt
En **objekt** är en [[Ordlista#instansiera|instans]] av en [[#klass]]. Till skillnad från en klass kan objekt göra någonting i java, kan användas i ett programm.  

Flera objekt kan skapas ur samma klass.
# Instansiera
Att **instanisera** betyder att skapa [[Ordlista#objekt|objekt]] ur en [[ordlista#klass|klass]]. När man instansierar en klass anropar man dess konstruktor med `new`, vilket skapar en ny **instans** (ett nytt objekt) av klassen i minnet.  

*Anta att vi har en klass `Bil` med en konstruktor `färg`*:


```java
Bil minBil = new Bil("Röd")
```

# Referensvariabel
En **referensvariabel** lagrar en adress till en objekt i minnet, inte själva objektet.

# Konstruktor 
En **konstruktor** är en speciell metod i en [[ordlista#klass|klass]] som används för att initiera [[ordlista#objekt|objektets]] egenskaper.  

En konstruktor har **samma namn som klassen**, har **ingen returtyp** och **körs automatiskt** när `new` används.

Ett exempel på en konstruktor finns is klassen [[Ordlista#^Djurklass|Djur]]

# Superklass
En **superklass** är en [[ordlista#klass|klass]] som innehåller variabler och metoder som kan ärvas av andra klasser.

# Subklass
En **subklass** är en klass som ärver från en [[#superklass]]. Man skapar en subklass med nyckelordet `extends` och `@override` används för att skriva över en metod från superklassen.

# Konstant
En variabel vars värde **inte kan ändras** efter att det har tilldelats.  
Man skapar en konstant med nyckelordet `final`.
```java
public static final double PI = 3.14159;

```

# Statisk Metod
En statisk metod är en metod som tillhör själva [[ordlista#klass|klassen]] och inte en [[ordlista#instansiera|instans]] av klassen. Vad det betyder är att vi kan anropa en statisk metod **utan att skapa en objekt** av klassen. Man skapar en statisk metod med nyckelordet `static`. 

```java
public static int addera(int a, int b) {
    return a + b;
}
```
Anta att addera(a,b) ligger i klassen `Matematik`. Då kan vi anropa metoden med:
```java
...
int summa = Matematik.addera(5, 10);
...
```

# Default-metod
En **default-metod** är en en metod **med implementation** som man lägger i ett interface. Det löste ett problem där om man ville lägga till en metod i ett interface så behövde man uppdatera alla [[ordlista#klass|klasser]] som implementerade den. Med en default-metod så behöver man inte uppdatera klasser men man kan om man vill. Man skapar en default-metod med nyckelordet `default`.  

I interface [[interface#^Interfacedjur|Djur]] så kan man lägga till en default-metod `sleep()` som alla klasser kommer att ha, "by default". 

```java
default void sleep() {
    System.out.println("Djuret sover...");
}
```

