<script>
	import P5 from "p5-svelte";

	export let width;
	export let height;
	export let text;
	export let textSize;
	
	const sketch = (p5) => {
		p5.Vector.zero = p5.createVector(0, 0);
		
		class Letter{
		  constructor(_letter, tx, ty){
		    this.letter = _letter;
		    this.target = p5.createVector(tx, ty);
		    this.pos = p5.createVector(
		      p5.random(-200, width + 200),
		      p5.random(height + fontSize, 2 * height)
		    );
				this.vel = p5.Vector.random2D();
				this.acc = p5.createVector();
				this.maxSpeed = 15;
				this.maxForce = 1;

				this.rotVel = 0;
				this.rotAcc = 0;
				this.rot = p5.random(-15, 15);
				
				this.behaviors = () => {
					let arrive = this.arrive(this.target);
					let mouse = p5.createVector(p5.mouseX, p5.mouseY);
					if(p5.pmouseX != p5.mouseX || p5.pmouseY != p5.mouseY){
						let flee = this.flee(mouse);
						flee.mult(5);
						this.applyForce(flee);
					}
					arrive.mult(2);
					this.applyForce(arrive);
				};
				
				this.applyForce = (force) => {
					this.acc.add(force);
				}

				this.applyRotForce = (force) => {
					this.rotAcc += force;
				}
				
				this.update = () => {
			    this.pos.add(this.vel);
					this.vel.add(this.acc);
					this.acc.mult(0, 0);

					this.rot += this.rotVel;
					this.rotVel += this.rotAcc;
					this.rotAcc = 0;
					this.rot = this.rot % 360;
					this.rotVel *= 0.97;
			  };
				
				this.display = () => {
					p5.translate(this.pos.x, this.pos.y);
			    p5.rotate(this.rot);
			    p5.text(this.letter, 0, 0);
				};
				
				this.flee = (target) => {
			    var desired = p5.Vector.sub(target, this.pos);
			    var d = desired.mag();
			    if (d <  fontSize) {
			      desired.setMag(this.maxSpeed);
			      desired.mult(-1);
			      var steer = p5.Vector.sub(desired, this.vel);
			      steer.limit(this.maxForce);

						let rotDir = target.x < this.pos.x ? -1 : 1;
						this.applyRotForce(2 * rotDir);
						
						
			      return steer;
			    } else {
			      return p5.Vector.zero;
			    }
			  }

				this.arrive = (target) => {
			    var desired = p5.Vector.sub(target, this.pos);
			    var d = desired.mag();
			    var speed = this.maxSpeed;
			    if (d < 4 * fontSize) {
			      speed = p5.map(d, 0, 100, 0, this.maxSpeed);
			    }
			    desired.setMag(speed);
			    var steer = p5.Vector.sub(desired, this.vel);
			    steer.limit(this.maxForce);
					
			    return steer;
			  }
				
				this.isFinished = () => {
					return Math.abs(this.target.x - this.pos.x) < 0.1 && 
						Math.abs(this.target.y - this.pos.y) < 0.1 && 
						Math.abs(this.rot) < 0.01;
				};
		  }
		}

		const word = text || "Hello!";
		
		let letters = word.split("");

		const fontSize = textSize;
		const kearning = fontSize * 0.8;
		
		p5.setup = () => {
			p5.createCanvas(width, height);
			p5.textFont("Courier New");
			p5.textAlign(p5.CENTER, p5.CENTER);
			p5.angleMode(p5.DEGREES);
			p5.textStyle(p5.BOLD);
			p5.textSize(fontSize);
			p5.fill(255);

			for(let i = 0; i < letters.length; i++) {
		    letters[i] = new Letter(letters[i], (i * kearning) + fontSize, height * 0.35);
		  }
			letters[0].rot = 0;
			letters[0].applyRotForce(412);
		}

		p5.draw = () => {
			p5.background(0, 0, 0);

			p5.fill(255);
			letters.forEach(l => {
				p5.resetMatrix();
				l.behaviors();
				l.update();
				l.display();
			});
		}
	}
</script>

<main>
	<P5 {sketch} />
</main>

<style>
	main {
		padding: 0px;
		margin: 0px;
	}
</style>