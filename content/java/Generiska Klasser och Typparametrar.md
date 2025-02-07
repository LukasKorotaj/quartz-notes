---
id: Generiska Klasser och Typparametrar
aliases:
  - typparameter
  - typargument
tags: []
---

# Generiska Klasser
En **generisk klass** är en klass som kan hantera olika typer utan att skriva om koden.  

Generiska klasser gör koden **flexibel**, **återanvändbar** och **typesäker** genom att använda [[#typparametrar]].

Att koden är **flexibel** och **återanvändbar** innebär att vi kan avända koden för olika typer för att slippa skriva om kod. 

Generiska klasser gör koden **typesäker** för att när vi anger en [[#Typparametrar|typparameter]] så kommer koden inte kompileras om vi använder fel typ. Vilket minskar risk för buggar.

## Innuti en Generisk Klass
**==förklara hur man skapar en generisk klass, skriv i princip allt efter "innuti en generisk klass"==**

# Typparametrar
Man kan deklarera en eller flera **typparametrar** när man definerar en klass.
```java
public class ArrayList<E> {...}
```
Typnamnet (`E`) väljer man själv. "E" står för "Element" och "T" står för "Type".

## Typargument
När man använder en [[Generiska Klasser och Typparametrar#generiska klasser|generisk klass]] ska man ange ett **typargument**. Ett **typargument** är den faktiska typen som används när en generisk klass [[Ordlista#instansiera|instansieras]].

```java
ArrayList<Integer> myList = new ArrayList<Integer>();
```

I det här fallet är `<Integer>` ett typargument.

