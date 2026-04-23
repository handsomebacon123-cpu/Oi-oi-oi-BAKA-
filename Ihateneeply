// 1. SCREEN SETUP
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

// 2. THE CHARACTERS
let player = { x: 200, y: 200, size: 40, speed: 4 };
let nextbot = { x: 50, y: 50, size: 60, speed: 2.5 };
let touchX = 200;
let touchY = 200;

// 3. THE INPUT (iPad Touch)
window.addEventListener("touchmove", (e) => {
    touchX = e.touches[0].clientX;
    touchY = e.touches[0].clientY;
    e.preventDefault(); 
}, { passive: false });

// 4. THE BRAIN (Logic)
function update() {
    // Player follows finger
    player.x += (touchX - player.x) * 0.1;
    player.y += (touchY - player.y) * 0.1;

    // Nextbot chases player
    if (nextbot.x < player.x) nextbot.x += nextbot.speed;
    if (nextbot.x > player.x) nextbot.x -= nextbot.speed;
    if (nextbot.y < player.y) nextbot.y += nextbot.speed;
    if (nextbot.y > player.y) nextbot.y -= nextbot.speed;

    // Hitbox Check
    let dist = Math.sqrt((player.x - nextbot.x)**2 + (player.y - nextbot.y)**2);
    if (dist < 40) {
        alert("THE NEXTBOT CAUGHT YOU!");
        location.reload();
    }
}

// 5. THE EYES (Graphics)
function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    
    ctx.fillStyle = "blue"; // Player
    ctx.fillRect(player.x, player.y, player.size, player.size);

    ctx.fillStyle = "white"; // Nextbot
    ctx.fillRect(nextbot.x, nextbot.y, nextbot.size, nextbot.size);
}

// 6. THE HEARTBEAT (Loop)
function gameLoop() {
    update();
    draw();
    requestAnimationFrame(gameLoop);
}

// 7. START ENGINE
gameLoop();
