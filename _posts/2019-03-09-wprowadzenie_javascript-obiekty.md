---
title: javascript - obiekty
published: true
date: 2019-03-09 21:45:00
---

Kontynuujemy podstawy javascript. Obiekty.

1. Po pierwsze znowu potrzebujemy pliku HTML w którym będziemy wpisywać naszą treść. W stworzonym wcześniej katalogu game01 (u mnie to dokładnie e:\\programowanie\kurs-javascript\game01) utwórz plik step03.html i wypełnij go poniższą treścią.


	```html
	<!DOCTYPE html>
	<html>

	<head>
		<meta charset="UTF-8">
		<title>obiekty proste</title>
	</head>

	<body>
		<script type="text/javascript">
		</script>
		ciało HTMLa
	</body>

	</html>
	```

1. Uruchom program mangoose. Mam nadzieję, że skonfigurowałeś go, jak w opisałem na początku kursu i widzisz teraz w przeglądarce katalog game01. Wejdź do niego i wybierz step03.html. Widać stronę z tekstem "ciało HTMLa".

1. Dodajmy zatem kod javascript. Wpisujemy go, jak ostatnio, pomiędzy liniami zaczynającymi się od &lt;script&gt; i &lt;/script&gt;.
	<br/>Utwórz zatem pierwszy obiekt! Co to w zasadzie jest? Jak robimy na przykład zmienną liczbaŻyć, to zachowa ona jedną liczbę. Czasem jednak trzeba w programie zapamiętać coś bardziej skomplikowanego. Przykładem niech będzie osoba. Osoba może mieć imię i wiek. W tym właśnie pomoże nam obiekt. Zaczynamy od let i nazwy, jak przy innych zmiennych. To, czym się różnią, to po = jest { i tu po kolei wymieniamy nazwę jakiejś cechy i jej wartość po :. Innym przykładem mógłby być obiekt auto z cechami marka, pojemność silnika i kolor.

	```html
	<script type="text/javascript">
		let osoba = {
			imie: "jan",
			wiek: 123
		};

	</script>
	```

1. No to fajnie, mamy zmienną osoba, ale jak dowiedzieć się o jej konkretną cechę? Dość łatwo. Wystarczy napisać osoba.nazwa_cechy.

	```html
	<script type="text/javascript">
		let osoba = {
			imie: "jan",
			wiek: 123
		};
		alert(osoba);
		alert(osoba.imie);
		alert(osoba.wiek);

	</script>
	```

1. To teraz połączmy poznane wcześniej funkcje z obiektem. Funkcja obiektu oznacza, że na każdym obiekcie będzie można wywołać tę funkcję. W naszym obiekcie osoba chcemy móc wyświelać imię. We wspomnianym przykładzie auta moglibyśmy na przykład mieć funkcję jedź().
<br/> Dodatkowo warto wiedzieć, że wewnątrz funkcji możemy dostać się do cech obiektu poprzez this.nazwa_cechy.

	```html
	<script type="text/javascript">
		let osoba = {
			imie: "jan",
			wiek: 123,

			pokazImie() {
				alert("moje imie to "+this.imie);
			}
		};

		alert(osoba);
		alert(osoba.imie);
		alert(osoba.wiek);

		osoba.pokazImie();

	</script>
	```

1. Taki obiekt widać w index00.html w game01. config jest obiektem i co więcej, ma w sobie też kolejne obiekty physics i scene. Oczywiście ma też proste cechy, jak width i height.

Wyjaśnimy sobie jeszcze klasę i będziemy mogli zacząć rozbudowywać grę.
