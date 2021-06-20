# Small!
> **Functions are the first line of organisation in any program**
> (*Funktionen sind die erste Organisationsstufe in jedem Programm*)
\- [Robert C. Martin](https://de.wikipedia.org/wiki/Robert_Cecil_Martin)

Zu [[Listing 3-1]] schreibt Uncle Bob:

- Lang
- Duplizierter Code
- viele merkwürdige Dinge
- seltsame Datentypen
- unübersichtliche Datentypen
- seltsame API
- unübersichtliche API
- zu viele verschiedene Abstraktionsebenen
- doppelt verschachtelte `if`-Anweisungen, gesteuert durch Flags

Dann macht er ein erstes Refactoring [[Listing 3-2]] und fragt wieso es einfacher zu lesen und zu verstehen ist:

- es ist kurz (erste Regel)
- es ist kürzer (zweite Regel)

Dazu sagt er jedoch, dass er 
1) diese Behautpung nicht begründen kann 
2) keine Hinweise geben kann das sehr kleine Funktionenbesser sind
3) aus Erfahrung heraus es besser sei möglichst kurze Funktionen zu haben

#### Wie kurz soll eine Funktion sein?

Er zeigt einen historischen Abriss und schliesset mit einem Programm *Sparkle* (leider ist dieses Programm verschollen) von [Kent Beck](https://de.wikipedia.org/wiki/Kent_Beck) als Beispiel  indem jede Funktion **zwei bis vier Zeilen** lang und gibt dies als Empfehlung aus.

MIt dieser Regel im iInterkopf zeigt Uncle Bob ein letztes refactoring mit [[Listing 3-3]]

## Blöcke und Einrückungen

Er kommt auch zu dem Schluß, dass hier Codeblocks innerhalb `if`, `else` und `while`-statements nur eine Zeile lang sein sollten.

#question: Im [[Listing 3-3]] sind es streng genommen zwei Zeilen. Heist dies, dass `return`nicht gezählt wird? 

Als Ergebis gibt Uncle Bob an, dass damit die umschließende Funktion nun 
1) klein ist
2) die darin in den Blöcken aufgerufenen Funktionen einen bechreibenden Namen tragen können
3) impliziert, dass Funktionen nicht mehr groß genug sind um verschachtelte Strukturen zu haben -> die ein Rückiung somit nicht merh als ein oder zwei Stufen haben

Fazit: In Summe macht dies die Funktionen einfacher les- und verstehbar.
	









