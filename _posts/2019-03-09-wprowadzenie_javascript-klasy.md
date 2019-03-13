---
title: javascript - obiekty
published: true
date: 2019-03-09 21:45:00
---

Kontynuujemy podstawy javascript. Klasy.

1. Po pierwsze znowu potrzebujemy pliku HTML w którym będziemy wpisywać naszą treść. W stworzonym wcześniej katalogu game01 (u mnie to dokładnie e:\\programowanie\kurs-javascript\game01) utwórz plik step04.html i wypełnij go poniższą treścią.


	```html
	<!DOCTYPE html>
	<html>

	<head>
		<meta charset="UTF-8">
		<title>klasa</title>
	</head>

	<body>
		<script type="text/javascript">

		</script>
		ciało HTMLa
	</body>

	</html>
	```

1. Uruchom program mangoose. Mam nadzieję, że skonfigurowałeś go, jak w opisałem na początku kursu i widzisz teraz w przeglądarce katalog game01. Wejdź do niego i wybierz step04.html. Widać stronę z tekstem "ciało HTMLa".

1. Dodajmy zatem kod javascript. Wpisujemy go, jak ostatnio, pomiędzy liniami zaczynającymi się od &lt;script&gt; i &lt;/script&gt;.
	<br/>Utwórz zatem pierwszą klasę! Co to w zasadzie jest? To taki trochę obiekt, jak w poprzednim zadaniu. To, czym się jednak różni to to, że możesz go wielokrotnie tworzyć w różnych miejscach i ma on swój typ.
	<br/>Przykładem niech będzie znowu osoba. Osoba może mieć imię i wiek. Zaczynamy od class i naszej nazwy (czyli Osoba) a potem następują nawiasy {}, które określają początek i koniec ciała klasy.

	```html
	<script type="text/javascript">
		class Osoba {
		}

	</script>
	```

1. Fajnie, mamy klasę, ale na razie nie za wiele ona może i nie za bardzo wiadomo, jak utworzyć jej obiekty. Co? Obiekty klasy? Tak, klasa to taki prototyp tego czym może być Osoba. Jak utworzymy sobie konkretną jedną osobę, to mamy wtedy obiekt klasy Osoba. Z czasem stanie się to jaśniejsze, obiecuję!
<br/>W każdym razie, żeby tworzyć obiekty klasy potrzebujemy tzw. konstruktora. Co to? To taki smok o imieniu Bob Budowniczy, który tworzy obiekty danej klasy. Konstruktor wpisujemy w ciele klasy. Poniżej kod rozbudowany o konstruktor. Ten konstruktor przyjmuje dwie rzeczy do zjedzenia - imię i wiek. Zapis "this.imie" i "this.wiek" oznacza, że Osoba ma cechę imię i cechę wiek.

	```html
	<script type="text/javascript">
	class Osoba {
		constructor(imie, wiek) {
			this.imie = imie;
			this.wiek = wiek;
		}
	}
	</script>
	```

1. No i ekstra. To teraz utwórzmy obiekt klasy osoba. Robimy to przez użycie słówka new. Łatwo. Następnie trzeba wpisać takie dane, jak napisaliśmy w konstruktorze - czyli tutaj imię i wiek. Wyciąganie konkretnej cechy obiektu poprzez użycie kropki.

	```html
	<script type="text/javascript">
	class Osoba {
		constructor(imie, wiek) {
			this.imie = imie;
			this.wiek = wiek;
		}
	}

	let jakas_osoba = new Osoba("maciek", 66);
	alert(jakas_osoba.imie);
	</script>
	```

1. To teraz połączmy poznane wcześniej funkcje z klasą! Wygląda to w zasadzie identycznie, jak w poprzednim wpisie o obiektach. Funkcja klasy oznacza, że na każdym obiekcie tej klasy będzie można wywołać tę funkcję. W naszej klasie Osoba chcemy móc wyświelać imię.
<br/> Dodatkowo warto wiedzieć, że wewnątrz funkcji możemy dostać się do cech obiektu klasy poprzez this.nazwa_cechy.

	```html
	<script type="text/javascript">
		class Osoba {
			constructor(imie, wiek) {
				this.imie = imie;
				this.wiek = wiek;
			}
			wyswietlOsobe() {
				alert('ej, ty, '+this.imie);
			}
		}

		let jakas_osoba = new Osoba("maciek", 66);
		alert(jakas_osoba.imie);
		jakas_osoba.wyswietlOsobe();
	</script>
	```

1. Taki obiekt klasy i jego tworzenie widać w index00.html w game01. Jest tam zapis "new Phaser.Game(config)", który tworzy obiekt gry stworzony w tym narzędziu, którego będziemy używać do pisania gry.

No to przejdźmy do pisania gry!
