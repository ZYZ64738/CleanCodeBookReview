# Gute Kommentare

## Rechtliche Kommentare
Kommentare die aus der Firmenpolicy heraus gefordert sind (Copyright).
Diese sollten möglichst kurz sein und auf l,ängere Gesetzestexte/Lizenzbedingungen verweisen statt im Kommentar selbst aufzuführen.

## Informative Kommentare

Beispiele
- Erklärung eines Rückgabewertes im Methodenkopf einer abstrakten Methode
- Bescreibungeines RegEx Patterns zum besseren Verständniss
- weiteres Beipiel?

## Erläuterung der Absicht
Erläuterung einer Absicht hniter einer Code-Entscheidung in der Umsetzung

## Klärung
Aufklären über den Sinn  obskurer Argumente oder Rückgabewerte.
Beispiel:
```java
public void testCompareTo() throws Exception {
    WikiPagePath a = PathParser.parse("PageA");
    WikiPagePath ab = PathParser.parse("PageA.PageB");
    WikiPagePath b = PathParser.parse("PageB");
    WikiPagePath aa = PathParser.parse("PageA.PageA");
    WikiPagePath bb = PathParser.parse("PageB.PageB");
    WikiPagePath ba = PathParser.parse("PageB.PageA");
    assertTrue(a.compareTo(a) == 0); // a == a 
    assertTrue(a.compareTo(b) != 0); // a != b 
    assertTrue(ab.compareTo(ab) == 0); // ab == ab 
    assertTrue(a.compareTo(b) == -1); // a < b 
    assertTrue(aa.compareTo(ab) == -1); // aa < ab 
    assertTrue(ba.compareTo(bb) == -1); // ba < bb 
    assertTrue(b.compareTo(a) == 1); // b > a 
    assertTrue(ab.compareTo(aa) == 1); // ab > aa 
    assertTrue(bb.compareTo(ba) == 1); // bb > ba 
}
```

Wenn dies nicht anders als so gezeigt geht dann ist besondere Genauigkeit und Sorgfältigkeit bei den KOmmentaren gefordert.


## Warnung vor Konsequenzen
```Java
// Don't run unless you
// have some time to kill.
public void _testWithReallyBigFile() {
    writeLinesToFile(10000000);
    response.setBody(testFile);
    response.readyToSend(this);
    String responseString = output.toString();
    assertSubString("Content-Length: 1000000000", responseString);
    assertTrue(bytesSent > 1000000000);
}
```

## TODO Kommentare

TODOs sind Task die der Programmierer meint noch zu tun zu müssen die er im Moment nicht umsetzen kann. Z. B: zeitlich, Kompetenz, als Erinnerungsnotiz etwas zu löschen, prüfen etc ...
 
 Es ist jedocj **keine** Entschuldigung dafür schlechten Code zu hinterlassen. Moderne IDEs listen TODO-Kommentare auf. Also sollten diese regelmäßig gesichtet und die Tasks umgesetzt werden.
 
 ## Verstärkung
 
 Zeigen weshalb eine bestimmte getroffene Maßnahme besonders wichtig ist:
 
 ```Java
 String listItemContent = match.group(3).trim();
// the trim is real important. It removes the starting 
// spaces that could cause the item to be recognized 
// as another list. 
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
 ```
 
 
## Javadocs/PHPDocs in öffentlichen APIs
Eine Beschreibung einer API-Schnitstelle mit guten beschreibenden Kommentaren ist sehr hilfreich. Jedoch sollten auch diese Kommentare mit besonderer Sorgfalt erfolgen.