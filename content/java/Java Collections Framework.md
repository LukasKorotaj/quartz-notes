---
id: Java Collections Framework
aliases:
  - JCF
tags: []
---
# Java Collections Framework
**Java Collections Framework** (JCF) är ett system i Java som  hjälper till att hantera grupper av objekt, som listor och tabeller. Det består av tre delar: **[[interface]]**, som bestämmer hur olika samlingar ska fungera; **[[Ordlista#abstrakta klasser|abstrakta Klasser]]**,  som ger en grund att bygga vidare på; och **[[Ordlista#klass|konkreta klasser]]**, som ArrayList och HashMap, som kan användas direkt. Med JCF kan man enkelt lägga till, ta bort och söka efter element i olika typer av samlingar.

Den finns i paketet `java.util.`

Dokumentationen finns på [javas webbsida](https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/util/package-summary.html)

Ett exempel på en ett interface i hierarkin är `Collection`

```java
public interface Collection<E> {
    boolean add(E x);
    boolean contains(Object x);
    boolean remove(Object x);
    ...
}
```


