---
title: gra02 - dodanie platform
published: true
date: 2019-03-13 21:25:00
---

1. Ludek i tło są fajni, ale jednak przyda się nam coś więcej. Niech gracz będzie miał po czym skakać. Zapisz ten zielony obrazek w game02/assets pod nazwą platform.png![](/assets/kurs-js/game02/platform.png)

1. Czas w takim razie rozbudować funkcję preload o ładowanie tego obrazka platformy do pamięci. Obrazek teraz w pamięci jest dostępny pod nazwą platform.


	```javascript
	function preload() {
		this.load.image('sky', 'assets/sky.png');
		this.load.image('player', 'assets/player-simple.png');
		this.load.image('platform', 'assets/platform.png');
	}
	```

1. Platforma w odróżnieniu od gracza jest nieruchoma, czyli statyczna. Platform będzie kilka, więc możemy je dodać jako grupę. Potem do grupy dodamy kolejne platformy w podanych miejscach. Ostatnia z nich jest powiększona dwukrotnie (po powiększeniu konieczne jest odświeżenie, czyli refreshBody).

	```javascript
	function create() {

		 this.add.image(400, 300, 'sky');

		 let player = this.physics.add.image(400, 100, 'player');
		 player.setVelocity(100, 200);
		 player.setBounce(1, 1);
		 player.setCollideWorldBounds(true);

		 let platforms = this.physics.add.staticGroup();
		 platforms.create(600, 400, 'platform');
		 platforms.create(50, 250, 'platform');
		 platforms.create(750, 220, 'platform');
		 platforms.create(400, 568, 'platform').setScale(2).refreshBody();

	 }
	```

1. No dobra, fajnie, ale nie ma zderzeń z tymi platformami. Czas zatem na końcu funkcji create dodać zderzacz obiektów. Tu chcemy zderzać gracza i platformy.

```javascript
function create() {

	 this.add.image(400, 300, 'sky');

	 let player = this.physics.add.image(400, 100, 'player');
	 player.setVelocity(100, 200);
	 player.setBounce(1, 1);
	 player.setCollideWorldBounds(true);

	 let platforms = this.physics.add.staticGroup();
	 platforms.create(600, 400, 'platform');
	 platforms.create(50, 250, 'platform');
	 platforms.create(750, 220, 'platform');
	 platforms.create(400, 568, 'platform').setScale(2).refreshBody();

	 this.physics.add.collider(player, platforms);
 }
```

Uuu, mamy platformy. Niezbyt one są efektowne, bo gracz na razie przez nie przelatuje.
