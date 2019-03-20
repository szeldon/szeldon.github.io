---
title: gra02 - gwiazdki
published: true
date: 2019-03-20 16:35:00
---

1. Trzeba by w końcu zacząć coś zbierać w naszej grze. Będą to gwiazdki. Zapisz ten obrazek gwiazdki w game02/assets pod nazwą star.png![](/assets/kurs-js/game02/star.png)

1. Po drugie w funkcji preload musisz wczytać ten obrazek. Tu pełna wersja funkcji.


	```javascript
	function preload() {

		this.load.image('player', 'assets/player-simple.png');
		this.load.image('sky', 'assets/sky.png');
		this.load.image('platform', 'assets/platform.png');
		this.load.image('star', 'assets/star.png');

	}
	```

1. Teraz trzeba dodać gwiazdki jakoś do gry. Można zrobić to na różne sposoby. Kod dodawaj na końcu funkcji create.<br/>
Użyjemy obiektu starGroup w którym podajemy konfigurację tworzenia wielu gwiazdek. Po pierwsze podajemy nazwę obrazka. Po drugie ile razy ma być powtórzony. Po trzecie od którego miejsca ma się zaczynać ich generowanie i o ile mają być od siebie oddalone. <br/>
Następnie trzeba dodać do silnika gry grupę, której podamy tę konfigurację. <br/>
Opcjonalnie możesz dodać jeszcze funkcję iterate, która dla każdej gwiazdki ustawi to, jak mocno odbija się ona od podłoża. <br/>
No i ostatni element to dodanie zderzacza, żeby gwiazdki nie spadały na dno gry.

	```javascript
	let starGroup = {
		key: 'star',
		repeat: 11,
		setXY: { x: 12, y: 0, stepX: 70 }
	};
	stars = this.physics.add.group(starGroup);
	stars.children.iterate(function (child) {
		child.setBounceY(0.4);
	});
	this.physics.add.collider(stars, platforms);
	```

1. Fajnie by było zbierać te gwiazdki. Musimy dodać do create coś podobnego do collidera. Takie coś, co wykryje, że zderzyły się dwa obiekty. Służy do tego funkcja overlap, której podamy obiekty, których najście na siebie chcemy wykryć. Jak to nastąpi, to chcemy, żeby została wywołana funkcja, której nazwę podamy - w tym przypadku collectStar.

	```javascript
	this.physics.add.overlap(player, stars, collectStar, null, this)
	```

1. Co teraz? Musisz stworzyć tę funkcję gdzieś obok (nie wewnątrz nich) create, update i preload. Do niej automatycznie silnik gry poda obiekty, których zderzenie wykryto.

	```javascript
  function collectStar(player, star) {
    star.disableBody(true, true);
  }
	```

1. Poniżej pełny kod. Powinno już działać zbieranie gwiazdek.


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
	      this.load.image('star', 'assets/star.png');

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

	      let starGroup = {
	        key: 'star',
	        repeat: 11,
	        setXY: { x: 12, y: 0, stepX: 70 }
	      };
	      stars = this.physics.add.group(starGroup);
	      stars.children.iterate(function (child) {
	        child.setBounceY(0.4);
	      });
	      this.physics.add.collider(stars, platforms);
	      this.physics.add.overlap(player, stars, collectStar, null, this)
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

	    function collectStar(player, star) {
	      star.disableBody(true, true);
	    }
	  </script>

	</body>

	</html>
	```
