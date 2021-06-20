# Prefer Exceptions to Returning Error Codes

Die Rückgabe von Fehlercodes aus Befehlsfunktionen ist eine subtile Verletzung der Befehlsabfrage trennung. Sie fördert die Verwendung von Befehlen als Ausdrücke in den Prädikaten von if-Anweisungen.


```php
callerFunction(){
	// ... Do ONE thing
	
	$error = checkStates($states);
	// now the callerFunction has to deal with the $error and does ANOTHER thing!

}

checkStates($states){
	if($states['one'] === E_OK){
		log("one okay!")	
		if($states['two'] === E_OK){
			log("one and two okay!")
		}	
		else{
			log ("two failed");
		}		
	}
	else{
		log ("one failed");
		return E_ERROR;
	}
}

```


### Extract Try/Catch Blocks
It is better to extract the bodies of the `try` and `catch` blocks out into functions of their own.

```php
callerFunction(){
	// ...
	checkStates($states);
}

checkStates($states){
	try{
		checkOne($states['one']);
		checkTwo($states['two']);		
	} catch (Exception $e){
		log($e->getMessage())
	}
}

checkOne($state){
	if($state !== E_OK){
		throw new Exception("one failed");
	}
}

checkTwo($state){
	if($state !== E_OK){
		throw new Exception("two failed");
	}
}

```


### Error Handling Is One Thing
Funktionen sollten eine Sache tun. Fehlerübergabe ist eine Sache.

### The Error.java Dependency Magnet
Returning error codes usually implies that there is some class or enum in which all the error codes are defined.

```java
public enum Error {
  OK,
  INVALID,
  NO\_SUCH,
  LOCKED,
  OUT\_OF\_RESOURCES,
  WAITING\_FOR\_EVENT;
}
```

Classes like this are a dependency magnet; many other classes must import and use them.

#question **enum** kommt mit php 8.1 ?


