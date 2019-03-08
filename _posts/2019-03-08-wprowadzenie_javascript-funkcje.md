---
title: javascript - funkcje
published: true
date: 2019-03-08 21:45:00
---

Kontynuujemy podstawy javascript. Funkcje.

1. Po pierwsze znowu potrzebujemy pliku HTML w którym będziemy wpisywać naszą treść. W stworzonym wcześniej katalogu game01 (u mnie to dokładnie e:\\programowanie\kurs-javascript\game01) utwórz plik step02.html i wypełnij go poniższą treścią.


```html
<!DOCTYPE html>
<html>

<head>
	<meta charset="UTF-8">
	<title>funkcje!</title>
</head>

<body>
	<script type="text/javascript">
	</script>
	ciało HTMLa
</body>

</html>
```

1. Uruchom program mangoose. Mam nadzieję, że skonfigurowałeś go, jak w opisałem na początku kursu i widzisz teraz w przeglądarce katalog game01. Wejdź do niego i wybierz step02.html. Widać stronę z tylko tekstem "ciało HTMLa".

1. Dodajmy zatem kod javascript. Wpisujemy go, jak ostatnio, pomiędzy liniami zaczynającymi się od <script> i </script>. Utwórzmy zatem pierwszą funkcję! Co to funkcja? To taki smok. Smok się nazywa. Smok może coś zjadać i może coś wypluwać. Ale niekoniecznie musi coś zjadać albo niekoniecznie coś wypluwać. Tu napiszmy prostą funkcję, która wyświetli nam alert. Jej wywołanie to po prostu podanie jej nazwy i nawiasów. Tak, alert() to funkcja. Jest już wbudowana w javascript.

```html
<script type="text/javascript">
	function pokazCosNaEkranie() {
		alert("AAAAAAAAAAAAAAAAAAAA");
	}

	pokazCosNaEkranie();
	pokazCosNaEkranie();
	pokazCosNaEkranie();
</script>
```

1. Zróbmy w takim razie też funkcję (smoka), który coś zjada. Tu funkcja pokazująca na ekranie kilka podanych zmiennych. Podane są dwie zmienne do zjedzenia. Jedna nazywa się kto, druga tekst. Ich połączenie z tekstem daje komunikat wypisywany na ekranie.

```html
<script type="text/javascript">

	function pokazToCosNaEkranie(kto, tekst) {
		alert(kto + " powiedział: " + tekst);
	}

	pokazToCosNaEkranie("zenek", "bla");
	pokazToCosNaEkranie("ten", "ojoj");
	pokazToCosNaEkranie("tamten", 123);

</script>
```

1. Ostatni rodzaj funkcji, to funkcja, która coś wypluwa. Robi się to poprzez użycia słowa return wewnątrz niej. Dzięki temu to, co jest podane po return, zostanie wyplute z funkcji i będzie tego można użyć w programie po wywołaniu funkcji.

```html
<script type="text/javascript">
	let zwrocone = pokazIZwrocCosNaEkranie("zenek", "bla");
	alert("FUNKCJA ZWRÓCIŁA: "+zwrocone);


	function pokazIZwrocCosNaEkranie(kto, tekst) {
		let do_wyswielenia = kto + " powiedział: " + tekst;
		alert(do_wyswielenia);
		return do_wyswielenia;
	}
</script>
```

1. Zwróć uwagę w pliku game01/index00.html, że mamy tam utworzone różne funkcje. Jest zapis "function create()" i "function preload()". Co więcej, użytych jest dużo funkcji jak setVelocity() czy setBounce(). Kolejny element index00 nam się wyjaśnił.

Na dziś to tyle.
