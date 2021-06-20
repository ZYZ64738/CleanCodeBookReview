# Have No Side Effects
Seiteneffekte vermeiden.

Seiteneffekte sind Lügen. Die Funktion verspricht nur eine Sache zu tun - tatsächlich tut sie versteckt weitere Dinge - Seiteneffekte:

Ein scheibar harmloses Beispiel:

```java
public class UserValidator {
  private Cryptographer cryptographer;
  public boolean checkPassword(String userName, String password) {
    User user = UserGateway.findByName(userName);
    if (user != User.NULL) {
      String codedPhrase = user.getPhraseEncodedByPassword();
      String phrase = cryptographer.decrypt(codedPhrase, password);
      if ("Valid Password".equals(phrase)) {
        Session.initialize();
        return true;
      }
    }
    return false;
  }
}
```

Der Seiteneffekt ist hier der Aufruf `Session.initialize()`. Es wird nicht nur das Passwort geprüft sondern in einem bestimmten Fall **zusätzlich** etwas initialisiert!

Die Funktion macht also in bestimmten Fällen zwei Dinge - hier eine temporäre Kopplung.

Ist dieser Fall unvermeidbar sollte die Funktion hier im Beispiel umbenannt wrden in `checkPasswordAndInitializeSession` obschon die Regel "Do One Thing" verletzt wird.

