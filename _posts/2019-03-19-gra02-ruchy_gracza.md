---
title: gra02 - ruchy gracza
published: true
date: 2019-03-19 21:25:00
---

1. Czas w takim razie zacząć sterować naszym graczem. Potrzebujemy do tego kilku zmian.

1. Po pierwsze potrzebujesz powiedzieć, jak nazywa się funkcja, która będzie wywoływana co klatkę animacji. Wpisujemy to wewnątrz obiektu config - u mnie to funkcja update.


	```javascript
	let config = {
		type: Phaser.AUTO,
		width: 800,
		height: 600,
		physics: {
			default: 'arcade',
			arcade: {
				gravity: {
					y: 200
				}
			}
		},
		scene: {
			preload: preload,
			create: create,
			update: update
		}
	};
	```

1. Po drugie trzeba stworzyć tę funkcję. Ja dodałem swoją zaraz za create.

	```javascript
	function update() {

	}
	```

1. Dodatkowo na przykład przed linią z tworzeniem obiektu gry (let game = new Phaser.Game(config)), trzeba stworzyć kilka zmiennych. Czemu? Po to, żeby do tych samych rzeczy miały dostęp funkcje create i update. Jak stworzymy gracza w create, to chcemy móc potem zmienić jego pozycję, co klatkę animacji, czyli w funkcji update.

	```javascript
	let player;
	let platforms;
	let cursors;

	let game = new Phaser.Game(config);
	```

1. Co teraz? Teraz trzeba trochę przerobić create. Po pierwsze wewnątrz create wywal "let player" i zastąp samym "player". Tak samo "let platforms" zamień na "platforms". Czemu tak? Bo chcemy przypisać do zmiennej zadeklarowanej przed chwilą obok game.<br/>
Co jeszcze? Trzeba utworzyć obiekt, który da nam możliwość dowiadywania się o wciskanie klawiatury. Poniżej pełen kod create.<br/>
A, no i bez sensu mając kontrolę nad ruchem gracza nadal nadawać mu ruch początkowy. Wywalić zatem trzeba linię "player.setVelocity()".

	```javascript
	function create() {

		this.add.image(400, 300, 'sky');

		player = this.physics.add.image(400, 100, 'player');
		player.setBounce(1, 1);
		player.setCollideWorldBounds(true);

		platforms = this.physics.add.staticGroup();
		platforms.create(600, 400, 'platform');
		platforms.create(50, 250, 'platform');
		platforms.create(750, 220, 'platform');
		platforms.create(400, 568, 'platform').setScale(2).refreshBody();

		this.physics.add.collider(player, platforms);

		cursors = this.input.keyboard.createCursorKeys();
	}
	```

1. Dobra, dobra, fajnie, fajnie, ale jak teraz sprawdzić, czy coś zostało wciśnięte? No i kiedy? <br/>
Kiedy? Co klatkę animacji trzeba sprawdzić wciśnięcie klawisza. Czyli w funkcji update.<br/>
Jak? Pomoże obiekt cursors stworzony w create. Dla przycisków możemy dowiedzieć się czy zostały wciśnięte poprzez isDown. Jeśli lewy wciśnięty, to zmień prędkość na trochę w lewo. Jeśli prawy, to trochę w prawo. Jeśli nic, to nie ruszaj się na boki.


	```javascript
	function update() {
		if (cursors.left.isDown) {
			player.setVelocityX(-100);
		} else if (cursors.right.isDown) {
			player.setVelocityX(100);
		} else {
			player.setVelocityX(0);
		}
	}
	```

1. Nieźle, nie? To może jeszcze niech gracz podskoczy, jak wciśniemy przycisk w górę podczas gdy gracz stoi na czymś? No to też trzeba by użyć cursors co klatkę, czyli dodajmy do update.

	```javascript
	function update() {
		if (cursors.left.isDown) {
			player.setVelocityX(-100);
		} else if (cursors.right.isDown) {
			player.setVelocityX(100);
		} else {
			player.setVelocityX(0);
		}

		if (cursors.up.isDown && player.body.touching.down) {
			player.setVelocityY(-330);
		}
	}
	```

1. Proponuję też zmniejszyć odbijanie się gracza od podłoża po spadnięciu na nie. W metodzie create trzeba zmienić 1,1 na 0.2.

	```javascript
      player.setBounce(0.2);
	```

1. Poniżej pełny kod na tę chwilę.

	```html
	<!DOCTYPE html>
	<html>
	<head>
	  <script src="../phaser.js"></script>
	</head>

	<body>

	  <script>

	    let config = {
	      type: Phaser.AUTO,
	      width: 800,
	      height: 600,
	      physics: {
	        default: 'arcade',
	        arcade: {
	          gravity: {
	            y: 200
	          }
	        }
	      },
	      scene: {
	        preload: preload,
	        create: create,
	        update: update
	      }
	    };

	    let player;
	    let platforms;
	    let cursors;

	    let game = new Phaser.Game(config);

	    function preload() {

	      this.load.image('player', 'assets/player-simple.png');
	      this.load.image('sky', 'assets/sky.png');
	      this.load.image('platform', 'assets/platform.png');

	    }

	    function create() {

	      this.add.image(400, 300, 'sky');

	      player = this.physics.add.image(400, 100, 'player');
      	player.setBounce(0.2);
	      player.setCollideWorldBounds(true);

	      platforms = this.physics.add.staticGroup();
	      platforms.create(600, 400, 'platform');
	      platforms.create(50, 250, 'platform');
	      platforms.create(750, 220, 'platform');
	      platforms.create(400, 568, 'platform').setScale(2).refreshBody();

	      this.physics.add.collider(player, platforms);

	      cursors = this.input.keyboard.createCursorKeys();
	    }

	    function update() {
	      if (cursors.left.isDown) {
	        player.setVelocityX(-100);
	      } else if (cursors.right.isDown) {
	        player.setVelocityX(100);
	      } else {
	        player.setVelocityX(0);
	      }

				if (cursors.up.isDown && player.body.touching.down) {
					player.setVelocityY(-330);
				}
	    }
	  </script>

	</body>

	</html>

	```
