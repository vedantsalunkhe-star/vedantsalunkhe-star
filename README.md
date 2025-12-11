# 👋 Hi, I'm Vedant

Aspiring Cyber Security learner | Information Technology Learner

---

## 🔥 About Me
Driven by a passion for digital safety and ethical hacking. Keen on building, automating, and analyzing security tools to make the internet safer for everyone.

- 💡 Constantly learning new skills in cyber security.
- 🛡️ Exploring vulnerability assessment, ethical hacking, and infosec automation.
- 🌱 Open to collaboration and community learning.

---

## 🛠️ Skills & Tools
- Penetration Testing (Kali Linux, Metasploit)
- Network Security (Wireshark, Nmap)
- Python & Bash Scripting
- Security Automation
- Basic Malware Analysis

---

## 🔒 Featured Projects
- **Vulnerability Scanner**: Custom script to scan for outdated services and open ports.
- **Recon Tool**: Information gathering tool for ethical hacking exercises.
- **Log Analyzer**: Python automation for security event parsing.

---

## 📫 Connect With Me
- Email: vedantsalunkhe820@gmail.com
- LinkedIn: [linkedin.com/in/vedant](https://www.linkedin.com/in/vedant)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Generative Art Gallery</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
</head>
<body>

    <div class="gallery-container">
        <h1>Generative Art #<span id="art-id">001</span></h1>
        <p>Click anywhere on the canvas to generate a new masterpiece.</p>
        
        <main id="canvas-container"></main>
    </div>

    <script src="sketch.js"></script>
    <script>
        // Simple script to randomize the Art ID number on reload
        document.getElementById('art-id').innerText = Math.floor(Math.random() * 999);
    </script>
</body>
</html>
body {
    margin: 0;
    padding: 0;
    background-color: #1a1a1a; /* Dark museum grey */
    color: #ffffff;
    font-family: 'Courier New', Courier, monospace; /* Tech/Code vibe */
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
}

h1 {
    font-weight: lighter;
    letter-spacing: 2px;
    margin-bottom: 0.5rem;
}

p {
    color: #888;
    font-size: 0.9rem;
    margin-bottom: 2rem;
}

canvas {
    border: 1px solid #333;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5); /* Nice shadow for depth */
    cursor: pointer;
}
function setup() {
    // Create a canvas that fits nicely inside the window
    let canvas = createCanvas(600, 600);
    canvas.parent('canvas-container'); // Put canvas inside our HTML div
    
    rectMode(CENTER); // Draw rectangles from the center, not corner
    angleMode(DEGREES); // Use degrees for easier rotation
    noLoop(); // Stop it from looping continuously (we want static art)
}

function draw() {
    background(20); // Dark background
    
    // Create a Grid
    let step = 50; // Distance between shapes
    
    for (let x = 50; x < width; x += step) {
        for (let y = 50; y < height; y += step) {
            
            push(); // Start a new drawing state
            translate(x, y); // Move to the grid position
            
            // GENERATIVE LOGIC:
            // 1. Random size
            let size = random(10, 45); 
            
            // 2. Random rotation
            rotate(random(0, 360));
            
            // 3. Random Colors (Neon Palette)
            let r = random(50, 255);
            let g = random(0, 100);
            let b = random(150, 255);
            let alpha = random(100, 200); // Transparency
            
            // 4. Random Shape choice
            if (random(1) > 0.5) {
                noStroke();
                fill(r, g, b, alpha);
                circle(0, 0, size);
            } else {
                noFill();
                stroke(r, g, b, alpha);
                strokeWeight(2);
                rect(0, 0, size, size);
            }
            
            pop(); // Restore original state for next loop
        }
    }
}

// When mouse is clicked, redraw the art!
function mousePressed() {
    redraw();
    // Update the ID number in HTML for fun
    document.getElementById('art-id').innerText = Math.floor(Math.random() * 999);
}
