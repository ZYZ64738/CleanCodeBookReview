# Switch Statements
>  By their nature, switch statements always do N things. Unfortunately we can’t always avoid switch statements, but we can make sure that each switch statement is buried in a low-level class and is never repeated. We do this, of course, with **#polymorphism**.

Hier wird erstmals #Polymorphismus (Vielgestaltigkeit) erwähnt und in diesem Zusammenhang auch #SRP

Beispiel eines problematischen Switch-Statements [[Listing 3-4]]

Die Funktion ...

1) ... ist Umnfangreich und wächst mit jedem neuen employee-Typ
2) ... macht mehr als eine Sache
3) ... hat mehr als einen Grund es zu Ändern daher verletzt es #SRP 
4) ... verletzt #OCP weil mit jedem neuen employee-Typ die Funktion geändert werden muss

Ausserdem: es ist möglich, dass es mehrere andere Funktionen gibt die einen employee behandeln und diese demnach ebenso die selbe schädliche Struktur mit den Problem-Punkten eins bis vier aufweisen. Beispiele:

- `isPayday(Employee e, Date data)`
- `deliverPay(Employee e)`

## Lösung

Das Switch-Statement in eine **Abstract Factory** auslagern.

Diese Factory [[Listing 3-5]] verwendet das Switch-Statement zur Erzeugung entsprechender Instanzen der Ableitung von Employee.

Die verschiedenen Funktionen, wie `calculatePay`, `isPayday` und `deliverPay`, werden polymorph über die Employee-Schnittstelle abgewickelt.

Eine generelle Empfehlung:

#important
Switch-Statements können toleriert werden, wenn sie 
- nur einmal vorkommen
- zur Erzeugung polymorpher Objekte verwendet werden
- hinter einer Vererbungsbeziehung versteckt sind, so dass der Rest des Systems sie nicht sehen kann.






