# Do One Thing

> **FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**
> (*FUNKTIONEN SOLLTEN EINE SACHE TUN. SIE SOLLTEN ES GUT MACHEN. SIE SOLLTEN NUR DIES TUN.*)
\- [Robert C. Martin](https://de.wikipedia.org/wiki/Robert_Cecil_Martin)


Was genau ist "eine Sache" ?

Eine Sache ist, etwas das sich in einer Abstraktionsebene zusammenfassen lässt.
Hier beschreibt Uncle Bob im Ansatz eine **Story** mittels "TO" (Um... zu...)um die Funktion zu beschreiben:

**Um zu** *RenderPageWithSetupsAndTeardowns*, prüfen wir ob die Seite eine Testseite ist, und falls ja, inkludieren wir die **setups** (Einrichtung) und **teardowns** (Abriss). In beiden Fällen rendern wir die Seite als HTML.

	(daher hat eine Funktion einen Verb-Charakter: "Render...", "Is...", "Has...")
	
Wenn also eine Funktion nur Schritte enthält die genau eine Abstraktionsebene unter der eignene Abstrakationsebene liegen, dann macht sie "eine Sache".

```php
	# Abstraktionsebene 0
	function renderPage(){
		$content=[];
		$content[] = renderHeader();
		$content[] = renderBody();
		$content[] = renderFooter();		
		return implode(PHP_EOL,$content);
	}
	
	# Abstraktionsebene 1	
	function renderHeader(){
		$content=[];
		$content[] = renderHeadline();		
		return implode(PHP_EOL,$content);		
	}
	
	# Abstraktionsebene 1	
	function renderBody(){
		$content=[];
		$content[] = renderParagraph();				
		return implode(PHP_EOL,$content);			
	}	
	
	# Abstraktionsebene 1	
	function renderFooter(){
		$content=[];
		$content[] = renderCopyright();						
		return implode(PHP_EOL,$content);			
	}		
	
	# Abstraktionsebene 2	
	function renderHeadline(){
		$content=[];
		$content[] = 'Headline';
		return implode(PHP_EOL,$content);			
	}
	
	# Abstraktionsebene 2	
	function renderParagraph(){
		$content=[];
		$content[] = 'Lorem Ipsum ...';		
		return implode(PHP_EOL,$content);			
	}	
	
	# Abstraktionsebene 2	
	function renderCopyright(){
		$content=[];
		$content[] = '&copy; 2021';				
		return implode(PHP_EOL,$content);			
	}	
	
```

Der Grund, warum wir Funktionen schreiben, ist ja, dass wir ein größeres Konzept (mit anderen Worten, der Name der Funktion der oberen Abstraktionsebene ) in eine Reihe von Schritten auf der nächst tieferen Abstraktionsebene zu zerlegen.

#### Wie erkennt man ob eine Funktion mehr als eine Sache macht?

#important
Eine Möglichkeit zu erkennen, dass eine Funktion mehr als "eine Sache" tut, ist, wenn man eine andere Funktion aus ihr extrahieren kann, deren Name nicht nur eine Wiederholung ihrer Implementierung ist.



