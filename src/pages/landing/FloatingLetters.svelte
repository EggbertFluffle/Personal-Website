<script>
	import P5 from "p5-svelte";

	const width = window.innerWidth;
	const height = window.innerHeight;
	
	const sketch = (p5) => {		
		class Letter{
		  constructor(_letter, tx, ty){
		    this.letter = _letter;
		    this.target = p5.createVector(tx, ty);
		    this.rotation = p5.random(-180, 180);
		    this.position = p5.createVector(
		      this.target.x + p5.random(-250, 250),
		      this.target.y + p5.random(0, 250)
		    );
				this.move = () => {
			    this.position.lerp(this.target, 0.07);
			    this.rotation *= 0.92;
			  };
				this.display = () => {
					p5.translate(this.position.x, this.position.y);
			    p5.rotate(this.rotation);
			    p5.text(this.letter, 0, 0);
				}
		  }
		}

		const fontSize = 98;
		const kerning = 125;
		const word = "EGGBERT";
		
		let letters = word.split("");
		
		p5.setup = () => {
			p5.createCanvas(width, height);
			p5.textFont("Courier");
			p5.textAlign(p5.CENTER, p5.CENTER);
			p5.angleMode(p5.DEGREES);
			p5.textStyle(p5.BOLD);
			p5.textSize(98);
			p5.fill(255);

			for(let i = 0; i < letters.length; i++) {
		    letters[i] = new Letter(letters[i], (i * kerning) + 100, height / 3);
		  }
		}

		p5.draw = () => {
			p5.background(0, 0, 0, 115);

			letters.forEach((l) => {
				p5.resetMatrix();
				l.move();
				l.display();
			});
		}
	}

	
</script>

<main>
	<P5 {sketch} />
</main>

<style>
	
</style>