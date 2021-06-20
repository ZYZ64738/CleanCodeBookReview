# Function Arguments
Die ideale Anzahl von Funktionsparameter ist **Null**, dann einstellig , dann zweistellig.
Dreistellige Anzahl der Funktionsparameter sollte vermieden werden. Mehr als drei Funktionsparameter benötigen spezilles Urteilsvermögen und sollten nach Möglichkeit vermieden werden.

#question : wie dann? gekapselt in einem Array, einem Object?

#question: was ist mit Variable Parameterzahl mit  [...](https://www.php.net/manual/de/functions.arguments.php#functions.variable-arg-list) oder [call_user_func_array](https://www.php.net/call_user_func_array) ?

### Gründe:
- schwiereige Testbarkeit mit vielen Parametern
- Parameter "mitschleppen" über mehrere Abstraktionsebene hinaus
- das Argument befindet sich auf einer anderen Abstraktionsebene als der Funktionsname und zwingt Sie, ein Detail zu kennen, das an dieser Stelle vllt. nicht besonders wichtig ist


Unkle Bob behandelt dann output- und input-argumente die es in PHP und Java @Roman? nicht gibt.


#question : output argument, input argument? Ich kenne von PHP `return` und `&$referenz`


### Häufige einstellige Formen
- prüfen auf Existenz (bool): `fileExists($file)`
- transformation des Parameters (hier im Beispiel: Dateiname in Dateiinhalt): `fileOpen($fileName) ... return $fileContent;`

Dabei einen treffenden Namen wählen damit der leser sofort weis was die Funktion tut.

Eine etwas weniger häufige Form: *event*

 In dieser Form gibt es ein Eingangsargument, aber kein Rückgabewert. Das gesamte Programm soll den Funktionsaufruf als Ereignis interpretieren und das Argument verwenden, um den Zustand des Systems zu verändern, zum Beispiel `void passwordAttemptFailedNtimes(int attempts)` . 

### Flag Arguments
Boolsche (Flag-) Argumente zeigen an, dass eine Funktion mehr als nur eine Sache macht.


### Zweistellige Formen
Funktionen mit zwei Parametern sind schwieriger zu verstehen als Funktionen mit nur einem Parameter da sie eine höhere Konzentration derer beim Verständnis erfordern.
Erst muss man verstehen was der erste Parameter bedeutet, dann was der zweite Parameter meint (ohne dabei den ersten Parameter zu vergessen ;-)).

Ausserdem besteht eine mögliche Verwechsungsgefahr in der Reihenfolge  z. B. `assertEqual(expected, actual)`

Wenn die Parameter allerdings Artverwand sind, z. B. ein Punt in einem kartesischen System `function setPoint(x,y)` ist das einfacher.

Solche Funktionen wird man nicht gänzlich vermeiden können. Man muss sich nur der Probleme bewusst sein und überlegen ob man diese umschiffen kann:

Man könnte beim Beispiel `setPoint` ein Array oder [[#Argument Objects]] als einzigen Parameter "Punkt" übergeben.


### Dreistellige Formen
Solche Funktionen sind signifikant schwieriger zu verstehen als solche mit zwei Parametern. Hier lohnt es sich genau zu überlegen ob sich das Problem nicht anders lösen lässt.

### Argument Objects
- `Circle makeCircle(double x, double y, double radius);`
- `Circle makeCircle(Point center, double radius);`

Das zweite Beispiel `Point center` scheint geschummelt, ist es jedoch nicht, da ein Punkt als Objekt zum Konzept des Programmes gehört.

### Argument List
`String.format("%s worked %.2f hours.", name, hours);`
 Eine Liste von Argumenten wie hier kann als **ein einzelner** Prameter vom Typ "Liste" verstanden werden:
 
 - void monad(**Integer... args**);
 - void dyad(String name, **Integer... args**);
 - void triad(String name, int count, **Integer... args**);

### Verbs and Keywords
Bilde treffende Verb/Nomen Paar als Funtionsnamen welche die Aufgabe der Funktion treffend erklären:

**Beispiel**:
`write(name)` ist sehr aussagekräftig. Was auch immer dieses "Name" Ding ist, es wird "geschrieben".
Ein noch besserer Name wäre `writeField(name)`, der uns sagt, dass der "Name" ein "Feld" ist.

Letzteres ist ein Beispiel für die Schlüsselwortform eines Funktionsnamens.

Zum Beispiel:
`assertEquals` könnte besser als
`assertExpectedEqualsActual(expected, actual)` geschrieben werden.
Dies entschärft das Problem, dass man sich die Reihenfolge der Argumente merken muss.