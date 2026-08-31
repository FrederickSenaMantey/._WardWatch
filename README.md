# WardWatch
This is how i created a light version of the program

 WardWatch — Build Guide
A modern glassmorphism authentication UI built with HTML, CSS, and vanilla JavaScript.

The project is organized into three main files:

WardWatch/
│
├── index.html
├── style.css
└── script.js

1. Project Setup
Create a new folder called:

WardWatch

Inside it, create three files:

index.html
style.css
script.js

The responsibility of each file is:

File	          -      Purpose
index.html      -      Page structure and content
style.css	      -      Design, animations, layout, responsiveness
script.js	      -      Interactions and dynamic behavior (Programming)


2. Build the HTML Foundation
Start with the basic HTML document.

In index.html, create:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>WardWatch</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

</body>
</html>

What this section does
Defines the document as HTML5.
Sets the page language to English.
Makes the page responsive.
Loads style.css.
Sets the browser title to WardWatch.


3. Add the Particle Canvas
Inside <body>, add:

<canvas id="particlesCanvas"></canvas>

The canvas will eventually become the animated background.

HTML provides the canvas.

CSS positions it behind the application.

JavaScript creates and animates the particles.



4. Create the Main WardWatch Card
Inside <body>, create the main application card:

<div class="card">

    <h1>✦ WardWatch</h1>

    <p class="subtitle">
        enter the grid
    </p>

</div>

This creates the central authentication panel.

The structure is:

.card
├── h1
└── subtitle



5. Create the Login / Signup Tabs
Inside .card, add:

<div class="tabs">

    <button class="tab-btn active" data-form="login">
        Log In
    </button>

    <button class="tab-btn" data-form="signup">
        Sign Up
    </button>

</div>

The data-form attributes tell JavaScript which form belongs to each tab.

data-form="login"
        ↓
   Login form

data-form="signup"
        ↓
   Signup form

   

6. Create the Form Container
After the tabs:

<div class="form-container">

</div>

This is where the login and signup forms will live.

The structure is now:

.card
├── WardWatch title
├── subtitle
├── tabs
└── form-container



7. Build the Login Form
Inside .form-container:

<form class="form" id="loginForm">

    <div class="input-group">

        <input
            type="email"
            placeholder="Email"
            required
        >

    </div>

    <div class="input-group">

        <input
            type="password"
            placeholder="Password"
            id="loginPw"
            required
        >

        <button
            type="button"
            class="toggle-pw"
            data-target="loginPw"
        >
            👁
        </button>

    </div>

    <button type="submit" class="btn-submit">
        → Log In
    </button>

</form>

This creates:

Email
Password
Show/hide password
Log In



8. Add Social Login Buttons
Under the login button:

<div class="divider">
    or
</div>

<div class="social-row">

    <button type="button" class="social-btn">
        <span class="icon">🕊</span> Google
    </button>

    <button type="button" class="social-btn">
        <span class="icon">🐦</span> X
    </button>

    <button type="button" class="social-btn">
        <span class="icon">◆</span> GitHub
    </button>

</div>

These are currently UI/demo buttons.

They do not perform real authentication yet.



9. Add the Login Footer
<div class="form-footer">

    <label>
        <input type="checkbox">
        Remember
    </label>

    <a href="#">
        Forgot?
    </a>

</div>

This adds:

Remember me
Forgot password
The forgot-password link is currently a placeholder.



10. Build the Signup Form
Create the second form:

<form class="form form--hidden" id="signupForm">

</form>

The form--hidden class keeps the signup form hidden initially.

JavaScript will show it when the user clicks Sign Up.




11. Add Signup Inputs
Inside the signup form:

<div class="input-group">

    <input
        type="text"
        placeholder="Full name"
        required
    >

</div>

<div class="input-group">

    <input
        type="email"
        placeholder="Email"
        required
    >

</div>

<div class="input-group">

    <input
        type="password"
        placeholder="Password"
        id="signupPw"
        required
    >

    <button
        type="button"
        class="toggle-pw"
        data-target="signupPw"
    >
        👁
    </button>

</div>

The signup form now contains:

Full name
Email
Password



12. Add the Password Strength Meter
Under the password:

<div class="strength-bar" id="strengthBar">

    <span></span>
    <span></span>
    <span></span>

</div>

<div class="strength-label" id="strengthLabel">
</div>

The three bars represent password strength.

Weak

[RED] [   ] [   ]

Medium

[ORANGE] [ORANGE] [   ]

Strong

[GREEN] [GREEN] [GREEN]



13. Add the Signup Button
<button type="submit" class="btn-submit">
    → Create Account
</button>

Then add the social buttons just like the login form.




14. Add the Login Switch
At the bottom of the signup form:

<div class="form-footer signup-footer">

    <span>
        Already in?

        <a href="#" id="switchToLogin">
            Log In
        </a>
    </span>

</div>

JavaScript will use switchToLogin to return to the login screen.




15. Connect the CSS
Inside <head>:

<link rel="stylesheet" href="style.css">

This connects:

index.html
     ↓
style.css

16. Build the CSS Reset
Start style.css:

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family:
        'Segoe UI',
        system-ui,
        -apple-system,
        sans-serif;
}

This gives the application a consistent starting point.




17. Build the WardWatch Background
body {
    min-height: 100vh;

    display: flex;
    align-items: center;
    justify-content: center;

    background: #0b0b1a;

    padding: 1.5rem;

    position: relative;

    overflow: hidden;
}

The dark background creates the foundation for the WardWatch interface.




18. Position the Particle Canvas
#particlesCanvas {
    position: fixed;

    top: 0;
    left: 0;

    width: 100%;
    height: 100%;

    z-index: 0;

    pointer-events: none;
}

The canvas sits behind the authentication card.




19. Create the Glass Card
.card {
    position: relative;

    z-index: 1;

    width: 100%;
    max-width: 460px;

    background:
        rgba(255, 255, 255, 0.04);

    backdrop-filter:
        blur(24px)
        saturate(200%);

    border-radius: 3rem;

    padding: 3rem 2.4rem;

    border:
        1px solid
        rgba(255, 255, 255, 0.06);

    box-shadow:
        0 40px 80px
        rgba(0, 0, 0, 0.7);
}

This creates the glassmorphism effect.




20. Create the WardWatch Neon Title
.card h1 {
    text-align: center;

    font-size: 2.4rem;

    font-weight: 800;

    background:
        linear-gradient(
            135deg,
            #f093fb,
            #f5576c,
            #4facfe,
            #43e97b
        );

    background-size: 300% 300%;

    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

    animation:
        shimmer 6s
        ease-in-out
        infinite;
}

Then add:

@keyframes shimmer {

    0%,
    100% {
        background-position: 0% 50%;
    }

    50% {
        background-position: 100% 50%;
    }

}

The title now has an animated neon gradient.




21. Style the Tabs
.tabs {
    display: flex;

    background:
        rgba(255, 255, 255, 0.04);

    border-radius: 60px;

    padding: 4px;

    margin-bottom: 2rem;
}

Then style the buttons:

.tab-btn {
    flex: 1;

    padding: 0.8rem 0;

    border: none;

    background: transparent;

    color:
        rgba(255, 255, 255, 0.35);

    border-radius: 40px;

    cursor: pointer;
}

Active tab:

.tab-btn.active {
    background:
        rgba(255, 255, 255, 0.08);

    color: #fff;

    box-shadow:
        0 4px 20px
        rgba(0, 0, 0, 0.3);
}



22. Style the Forms
.form {
    display: flex;

    flex-direction: column;

    gap: 1.2rem;
}

Hide inactive forms:

.form--hidden {
    display: none;
}

23. Style the Inputs
.input-group input {
    width: 100%;

    padding: 1rem 1.2rem;

    padding-right: 3.2rem;

    background:
        rgba(255, 255, 255, 0.04);

    border:
        1px solid
        rgba(255, 255, 255, 0.06);

    border-radius: 60px;

    font-size: 0.95rem;

    color: #fff;

    outline: none;
}

Focus state:

.input-group input:focus {
    border-color:
        rgba(255, 255, 255, 0.2);

    background:
        rgba(255, 255, 255, 0.06);

    box-shadow:
        0 0 0 5px
        rgba(245, 87, 108, 0.05);
}



24. Style the Password Toggle
.toggle-pw {
    position: absolute;

    right: 1.2rem;

    top: 50%;

    transform:
        translateY(-50%);

    background: none;

    border: none;

    color:
        rgba(255, 255, 255, 0.2);

    cursor: pointer;
}

This places the eye button inside the password field.

25. Build the Password Strength UI
.strength-bar {
    display: flex;

    gap: 6px;

    margin-top: -0.4rem;
}

.strength-bar span {
    flex: 1;

    height: 3px;

    background:
        rgba(255, 255, 255, 0.06);

    border-radius: 10px;

    transition: all 0.4s ease;
}

Then:

.active-weak {
    background: #f5576c;
}

.active-medium {
    background: #f9a825;
}

.active-strong {
    background: #43e97b;
}



26. Style the Main Buttons
.btn-submit {
    padding: 1rem;

    border: none;

    border-radius: 60px;

    font-size: 1rem;

    font-weight: 700;

    color: #fff;

    background:
        linear-gradient(
            135deg,
            #f093fb,
            #f5576c
        );

    cursor: pointer;

    transition: all 0.3s ease;

    box-shadow:
        0 8px 30px
        rgba(245, 87, 108, 0.2);
}

Hover effect:

.btn-submit:hover {
    transform: scale(1.02);

    box-shadow:
        0 12px 40px
        rgba(245, 87, 108, 0.35);
}



27. Add Responsive Design
At the bottom of style.css:

@media (max-width: 480px) {

    .card {
        padding: 2rem 1.2rem;

        border-radius: 2rem;
    }

    .card h1 {
        font-size: 1.8rem;
    }

    .tab-btn {
        font-size: 0.8rem;

        padding: 0.6rem 0;
    }

    .social-btn {
        font-size: 0.7rem;

        padding: 0.4rem 0.8rem;
    }

}

This makes WardWatch work better on smaller screens.



28. Connect JavaScript
At the bottom of index.html, before </body>:

<script src="script.js"></script>

Now the three files are connected:

HTML
 │
 ├── CSS
 │
 └── JavaScript

 

29. Build the Particle System
In script.js:

const canvas =
    document.getElementById(
        'particlesCanvas'
    );

const ctx =
    canvas.getContext('2d');

let w;
let h;

let particles = [];

Create the resize function:

function resize() {

    w =
        canvas.width =
        window.innerWidth;

    h =
        canvas.height =
        window.innerHeight;

}

window.addEventListener(
    'resize',
    resize
);

resize();



30. Create the Particle Class
Each particle needs:

X position
Y position
Size
Speed
Opacity

Create:

class Particle {

    constructor() {
        this.reset();
    }

    reset() {

        this.x =
            Math.random() * w;

        this.y =
            Math.random() * h;

        this.size =
            Math.random() * 2.5 + 0.5;

        this.speedX =
            (Math.random() - 0.5) * 0.5;

        this.speedY =
            (Math.random() - 0.5) * 0.5;

        this.opacity =
            Math.random() * 0.5 + 0.1;

    }

}

31. Make Particles Move
Add an update() method:

update() {

    this.x += this.speedX;

    this.y += this.speedY;

    if (this.x < 0 || this.x > w) {
        this.speedX *= -1;
    }

    if (this.y < 0 || this.y > h) {
        this.speedY *= -1;
    }

}

The particles now bounce around the screen.



32. Draw the Particles
Add:

draw() {

    ctx.beginPath();

    ctx.arc(
        this.x,
        this.y,
        this.size,
        0,
        Math.PI * 2
    );

    ctx.fillStyle =
        `rgba(
            255,
            255,
            255,
            ${this.opacity}
        )`;

    ctx.fill();

}



33. Generate the Particles
Create 70 particles:

for (let i = 0; i < 70; i++) {

    particles.push(
        new Particle()
    );

}



34. Connect Nearby Particles
Calculate the distance between particles.

When two particles are close enough, draw a line:

if (dist < 120) {

    ctx.beginPath();

    ctx.moveTo(
        particles[i].x,
        particles[i].y
    );

    ctx.lineTo(
        particles[j].x,
        particles[j].y
    );

    ctx.stroke();

}

This creates the connected network effect behind WardWatch.



35. Create the Animation Loop
function animateParticles() {

    ctx.clearRect(
        0,
        0,
        w,
        h
    );

    particles.forEach(p => {

        p.update();

        p.draw();

    });

    drawLines();

    requestAnimationFrame(
        animateParticles
    );

}

animateParticles();

The background is now animated.



36. Build the Tab System
Select the forms:

const tabs =
    document.querySelectorAll(
        '.tab-btn'
    );

const loginForm =
    document.getElementById(
        'loginForm'
    );

const signupForm =
    document.getElementById(
        'signupForm'
    );

Create:

function setActiveForm(formName) {

    tabs.forEach(btn => {

        btn.classList.toggle(
            'active',
            btn.dataset.form === formName
        );

    });

    if (formName === 'login') {

        loginForm.classList.remove(
            'form--hidden'
        );

        signupForm.classList.add(
            'form--hidden'
        );

    } else {

        signupForm.classList.remove(
            'form--hidden'
        );

        loginForm.classList.add(
            'form--hidden'
        );

    }

}



37. Make the Tabs Clickable
tabs.forEach(btn => {

    btn.addEventListener(
        'click',
        function() {

            setActiveForm(
                this.dataset.form
            );

        }
    );

});

Now:

Log In
   ↓
Login form

Sign Up
   ↓
Signup form



38. Add Password Visibility
Find all password toggle buttons:

document
    .querySelectorAll('.toggle-pw')
    .forEach(btn => {

        btn.addEventListener(
            'click',
            function() {

                const target =
                    document.getElementById(
                        this.dataset.target
                    );

                if (!target) return;

                if (
                    target.type ===
                    'password'
                ) {

                    target.type = 'text';

                    this.textContent = '🙈';

                } else {

                    target.type =
                        'password';

                    this.textContent = '👁';

                }

            }
        );

    });

Now users can show and hide their password.



39. Build Password Strength Detection
Create:

function checkStrength(pw) {

    let score = 0;

    if (pw.length >= 6)
        score++;

    if (pw.length >= 10)
        score++;

    if (
        /[a-z]/.test(pw) &&
        /[A-Z]/.test(pw)
    ) {
        score++;
    }

    if (/\d/.test(pw))
        score++;

    if (
        /[^a-zA-Z0-9]/.test(pw)
    ) {
        score++;
    }

    return Math.min(score, 3);
}

The strength levels are:

1 → Weak
2 → Medium
3 → Strong



40. Listen to Password Input
pwInput.addEventListener(
    'input',
    function() {

        const pw = this.value;

        const level =
            checkStrength(pw);

    }
);

Every time the user types, the strength is recalculated.

41. Update the Strength Meter
Reset the bars:

strengthBars.forEach(bar => {

    bar.className = '';

});

Activate the appropriate bars:

for (
    let i = 0;
    i < level &&
    i < strengthBars.length;
    i++
) {

    strengthBars[i]
        .classList
        .add(colors[i]);

}

Then update the label:

strengthLabel.textContent =
    `● ${labelText}`;

    

42. Handle Form Submission
For the current WardWatch prototype, form submission is simulated.

Prevent the browser from submitting:

document
    .querySelectorAll('.form')
    .forEach(form => {

        form.addEventListener(
            'submit',
            function(e) {

                e.preventDefault();

            }
        );

    });

Then display a demo message:

const isLogin =
    this.id === 'loginForm';

alert(
    isLogin
        ? '🔐 Logging in... (demo)'
        : '✨ Account created! (demo)'
);

Important
This is not real authentication.

The current version is a frontend prototype.

Real authentication requires a backend or authentication service.



43. Initialize WardWatch
At the bottom of script.js:

setActiveForm('login');

This makes the login screen appear when WardWatch starts.

44. Final WardWatch Architecture
The finished application is organized like this:

                    WARDWATCH
                       │
           ┌───────────┴───────────┐
           │                       │
         HTML                    CSS
           │                       │
     Page structure          Visual design
           │                       │
           └───────────┬───────────┘
                       │
                  JavaScript
                       │
        ┌──────────────┼──────────────┐
        │              │              │
    Particles        Tabs       Password tools
        │              │              │
    Animation     Login/Signup    Eye toggle
                                  Strength
                       │
                       ▼
                  Form Events
                       │
                       ▼
                 Demo Responses

    

46. Recommended Build Order
If you're learning how to build WardWatch, don't paste everything at once.

Build it in this order:

HTML document
WardWatch card
Login form
Signup form
CSS reset
Dark background
Glass card
WardWatch neon title
Tabs
Input fields
Buttons
Responsive design
Canvas
Particle class
Particle animation
Login/signup switching
Password visibility toggle
Password strength meter
Form submission
Final cleanup
Test the application after every section.

This makes it much easier to understand what each piece of code does and where a problem occurs.



46. Final File Responsibilities
index.html
Contains:

Page structure
WardWatch branding
Forms
Inputs
Buttons
Links
Canvas

style.css
Contains:

Colors
Spacing
Sizes
Layouts
Glass effects
Gradients
Animations
Hover effects
Responsive styles

script.js
Contains:

Particle system
Canvas animation
Tab switching
Password visibility
Password strength
Form events
Initialization



47. Future WardWatch Features
Once the frontend prototype is working, WardWatch can be expanded with:

Real user registration
Real login
Secure password handling
Database integration
Email verification
Forgot-password functionality
Google authentication
GitHub authentication
User profiles
Dashboard
Notifications
Loading states
Toast messages
Form validation
Protected pages
Logout
Remember-me functionality
This gives you a clear path from a frontend WardWatch prototype to a complete web application.
