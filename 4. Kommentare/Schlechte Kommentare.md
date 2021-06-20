# Schlechte Kommentare

## Nuscheln

Ein einfaches spontantes "herausposaunen" als Kommentar sollte durch einen bestmöglichst verfassten Kommentar ersetzt werden. Ansonsten wird ein an sich gut geminter Kommentar eher ein Rätsel denn eine Hilfe sein.

## Redundante Kommentare
Kommentare die länger zu lesen und zu verstehen sind als der Code selbst den diese Kommentare zu Beschreiben versuchen sind Überflüssig. 

Er hat keinen ergänzenden oder erweiterten Informationsgehalt.

## Irreführende Kommentare
Kommentare müssen präzise sein. Ansonsten können diese beim Leser zu falschen Schlüssen führen.


## Unterstellte Kommentare
Eine Regel die besagt das jede Funktion ein javadoc haben müsse oder jede Variable einen Kommentar ist einfach dumm.
Diese art Kommentare führen zu Unordung, Falschaussagen, allgemeine Verwirrung und Desorganisation:

```Java
 /**
  *
  * @param title The title of the CD
  * @param author The author of the CD
  * @param tracks The number of tracks on the CD
  * @param durationInMinutes The duration of the CD in minutes
  */
 public void addCD(String title, String author,
     int tracks, int durationInMinutes) {
     CD cd = new CD();
     cd.title = title;
     cd.author = author;
     cd.tracks = tracks;
     cd.duration = duration;
     cdList.add(cd);
 }
	
```

## Protokoll Kommentare
Damit ist eine Art Changelog gemeint.
Das ist depercated ... niemand macht soetwas mehr -> git

## Rausch Kommentare
Kommentar der etwas offensichtliches beschreibt ohne zusätzliche Information hizuzufügen.

## Unheimliches Gräusch

Diese Kommentare sind zu absolut nichts nütze. Ausserdem ist durch C&P der letze Kommentar auch noch falsch.

```Java
	/** The name. */
	private String name;
	/** The version. */
	private String version;
	/** The licenceName. */
	private String licenceName;
	/** The version. */
	private String info;
```


## Verwende eine Funktion oder eine Variable  anstatt eines Kommentars falls möglich
Betrachten Sie die folgende Codestrecke:
```java
	// Hängt das Modul aus der globalen Liste <mod> von dem
	// Subsystem ab, von dem wir Teil sind?
	if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```
Dies könnte ohne den Kommentar umformuliert werden als
```java
	ArrayList moduleDependees = smodule.getDependSubsystems();
	String ourSubSystem = subSysMod.getSubSystem();
	if (moduleDependees.contains(ourSubSystem))
```
Der Autor des ursprünglichen Codes hat möglicherweise zuerst den Kommentar geschrieben (unwahrscheinlich) und dann dann den Code geschrieben, um den Kommentar zu erfüllen. Allerdings sollte der Autor dann den Code überarbeitet haben, so wie ich es getan habe, so dass der Kommentar entfernt werden konnte.

## Positionmarkierungen
Code in Sektionen zu organisiren mit Positionmarkierungen wie
```java
 // Actions /////////////////
```
 sind nur sehr selten sinnvoll. Sie sollten Grundsätzlich vermieden werden insbesondere wie in diesem Fall die angängten /.
 
 Wenn überhaupt sollten sie spärlihc eingesetzt werden das Sie sonst übersehen werden.
 
## Schliessende Klammer Kommentare
Wurden eingesetzt bei extremer Verschachtelung. Es ist besser Funktionen einzukürzen (siehe [[3. Functions]])

## Zuschreibungen und "By"-Zeilen
```java
	/*Added by Rick and Morty*/
```
Versionierungssysteme zeigen exakt wer welche Zeile Code zu welchem Zeitpunkt bearbeitet hat. Daher sind solche Kommentare unnötig. Sie gammeln Jahre im Code ohne das sie nützlich sind.


## Auskommentierter Code
Wenige Praktiken sind so abscheulich wie das Auskommentieren von Code. **Don't Do This!** 
Andere die diesen Code sehen trauen sich nicht diesen zu löschen weil sie denken er sei (noch)
wichtig. So sammelt sich auskommentierter Code wie wie der Bodensatz einer schlechten Flasche Wein.

Ist er noch wichtig?
Wurde vergessen aufzuräumen?

MIt Versionierungssystemen ist auskommetierter Code Überflüssig.

## HTML Kommentare
HTML in Kommentaren sind ein Gräuel. Sie sind dorch schlechter lesbar wo man sie gut lesen können sollte. 

Wenn Kommentare von einem Werkzeug (wie Javadoc) extrahiert werden, um in einer Webseite zu erscheinen, dann sollte es in der Verantwortung dieses Werkzeugs und nicht des Programmierers liegen, die Kommentare mit entsprechendem HTML zu schmücken.

## Nichtlokale Information
Kommentare sollten möglichst na an dem Code stehen den sie behandeln.

## Zu viel Information
Kommentare sollten präzise und knapp sein. Kein Tutorial um den nachfolgenden Code inkl. historischer Abhandlung.

## Nicht offensichtliche Verbindung zum Code
Die Verbindung von Kommentar und Code muss offensichtlich sein.

## Beschreibung von Funktionen in Funktionskopf
Kurze Funktionen brauchen keinen Kommentar. Ein gut gewähler Funktionsname ist selbstredend. 


## Javadoc/PHPDoc
So nützlich Javadocs für öffentliche APIs auch sind, sie sind ein Fluch für Code, der nicht für die Öffentlichkeit bestimmt ist. Das Erzeugen von javadoc-Seiten für die Klassen und Funktionen innerhalb eines System ist im Allgemeinen nicht sinnvoll, und die zusätzliche Formalität der javadoc-Kommentare ist kaum mehr als Ballast und Ablenkung. 

[Javadoc](https://de.wikipedia.org/wiki/Javadoc)
[PHPDoc](https://de.wikipedia.org/wiki/PHPDoc)
