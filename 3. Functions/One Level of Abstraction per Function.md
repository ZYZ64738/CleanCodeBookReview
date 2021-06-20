# One Level of Abstraction per Function
Wenn eine Funktion in Sektionen wie beispielsweise *Deklarationen* oder *initilaisierungen* unterteilt ist dann ist das ein Symptom dafür, dass diese Funktion mehr als eine Sache macht.

Das Mischen von Abstraktionsebenen innerhalb einer Funktion ist immer verwirrend. Die Leser können möglicherweise nicht erkennen, ob ein bestimmter Ausdruck ein wesentliches Konzept oder ein Detail ist.Schlimmer noch, sobald Details mit wesentlichen Konzepten gemischt werden, neigen immer mehr Details dazu, sich innerhalb der Funktion anzuhäufen.

### Reading Code from Top to Bottom: *The Stepdown Rule*

> We want the code to read like a top-down narrative.

#question : really?

Hier beschreibt Uncle Bob mit dem "Story-Telling-Ansatz -> TO (Um... zu...)" den Programmablauf über die Abstaktionseben lesbar zu machen. Das erfordert, das eine jede Funktion ebennur eine Abstraktionsebene behandeln darf. Beispiel:

> **Um** eine Seite **zu** rendern, rendern wir einen Header, einen Body und einen Footer.
> **Um** einen Header **zu** rendern, rendern wir eine Headline
> **Um** einen Body **zu** rendern, rendern wir eine Headline und einen Paragraph
> **Um** einen Footer **zu** rendern, rendern wir einen Copyright

