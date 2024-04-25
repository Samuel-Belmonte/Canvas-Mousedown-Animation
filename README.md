const canvas = document.querySelector("#canvas1");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
const particlesArray = [];

window.addEventListener("resize", function () {
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
});

const mouse = {
x: null,
y: null,
};

canvas.addEventListener("click", function (e) {
mouse.x = e.x;
mouse.y = e.y;
});

canvas.addEventListener("mousemove", function (e) {
mouse.x = e.x;
mouse.y = e.y;
});

class Particle {
constructor() {
//this.x = mouse.x;
//this.y = mouse.y;
this.x = Math.random() _ canvas.width;
this.y = Math.random() _ canvas.height;
this.size = Math.random() _ 5 + 1;
this.speedX = Math.random() _ 3 - 1.5;
this.speedY = Math.random() _ 3 - 1.5;
}
update() {
this.x += this.speedX;
this.y += this.speedY;
}
draw() {
ctx.fillStyle = "blue";
ctx.beginPath();
ctx.arc(this.x, this.y, 50, 0, Math.PI _ 2);
ctx.fill();
}
}

init();

function init() {
for (let i = 0; i < 100; i++) {
particlesArray.push(new Particle());
}
}

function handleParticles() {
for (let i = 0; i < particlesArray.length; i++) {
particlesArray[i].update();
particlesArray[i].draw();
}
}

function animate() {
ctx.clearRect(0, 0, canvas.width, canvas.height);
handleParticles();
requestAnimationFrame(animate);
}

animate();
