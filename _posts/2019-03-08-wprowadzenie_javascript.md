---
title: javascript - zmienne
published: true
date: 2019-03-08 21:20:00
---

Trochę podstaw javascript na dziś. Zmienne.

1. Po pierwsze potrzebujemy pliku HTML w którym będziemy wpisywać naszą treść. W stworzonym wcześniej katalogu game01 (u mnie to dokładnie e:\\programowanie\kurs-javascript\game01) utwórz plik step01.html i wypełnij go poniższą treścią.


```html
<!DOCTYPE html>
<html>

<head>
	<meta charset="UTF-8">
	<title>zmienne!</title>
</head>

<body>
	<script type="text/javascript">
	</script>
	ciało HTMLa
</body>

</html>
```

1. Uruchom program mangoose. Mam nadzieję, że skonfigurowałeś go, jak w poprzednim poście i widzisz teraz w przeglądarce katalog game01. Wejdź do niego i wybierz step01.html. Widać stronę z tylko tekstem "ciało HTMLa".

1. Dodajmy wreszcie jakiś kod javascript. Wpisujemy go pomiędzy liniami zaczynającymi się od <script> i </script>. Utwórzmy zatem zmienną tekstową. Zmienne tworzymy poleceniem let. Co to zmienna? Pudełko, które ma nazwę i coś w nim siedzi. Przykładem może być zmienna liczbaŻyć w grach. Potem wyświetlmy ją funkcją (możesz jeszcze nie rozumieć, ale to nieważne!) alert().

```html
<script type="text/javascript">
  alert(wiadomosc);
  let inna_wiadomosc = "inny tekst";
  alert(inna_wiadomosc);
</script>
```

1. Zmienne nietekstowe tworzymy identycznie. Ba, możemy nawet łączyć ze sobą różne zmienne, jak poniżej.

```html
<script type="text/javascript">
  alert(wiadomosc);
  let inna_wiadomosc = "inny tekst";
  alert(inna_wiadomosc);

  let liczba = 123;
  alert(liczba);
  let wiadomosc_i_liczba = wiadomosc + liczba;
  alert(wiadomosc_i_liczba);
</script>
```

1. Jeszcze lepiej, zobaczcie, że do zmiennej można przypisać inną zmienną i wtedy zmienna będzie już wskazywać na to samo, co druga zmienna.

```html
<script type="text/javascript">
  alert(wiadomosc);
  let inna_wiadomosc = "inny tekst";
  alert(inna_wiadomosc);

  let liczba = 123;
  alert(liczba);
  let wiadomosc_i_liczba = wiadomosc + liczba;
  alert(wiadomosc_i_liczba);

  inna_wiadomosc = wiadomosc;
  alert(inna_wiadomosc);
  alert(wiadomosc + inna_wiadomosc);
  alert(wiadomosc + 123);
</script>
```

1. Zwróć uwagę w pliku game01/index00.html, że mamy tam różne zmienne. Jest zapis "let config", "let player". Powoli zaczniemy rozumieć każdą linijkę.

Na dziś to tyle.
