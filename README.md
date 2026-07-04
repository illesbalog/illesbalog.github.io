<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raspberry Pi iMac | Project Showcase</title>
    <style>
        /* Apple-style CSS Reset and Font Stack */
        :root {
            --bg-color: #fbfbfd;
            --text-main: #1d1d1f;
            --text-secondary: #86868b;
            --accent-color: #0066cc;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            /* This natively calls SF Pro on Apple devices, and Segoe UI/Roboto on others */
            font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display", "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            overflow-x: hidden;
        }

        /* Typography */
        h1 {
            font-size: clamp(3rem, 6vw, 5rem);
            font-weight: 700;
            letter-spacing: -0.02em;
            line-height: 1.1;
            margin-bottom: 0.2em;
            text-align: center;
            margin-top: 10vh;
        }

        h2 {
            font-size: clamp(1.5rem, 3vw, 2rem);
            font-weight: 600;
            letter-spacing: -0.015em;
            color: var(--text-secondary);
            text-align: center;
            margin-bottom: 3rem;
        }

        .container {
            max-width: 980px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .description {
            max-width: 800px;
            margin: 0 auto 5rem auto;
            font-size: 21px;
            line-height: 1.5;
            font-weight: 400;
            letter-spacing: 0.011em;
            text-align: center;
            color: var(--text-main);
        }

        .description p {
            margin-bottom: 1.5rem;
        }

        /* Unconventional "Scattered Cards" Image Gallery */
        .gallery-container {
            position: relative;
            height: 600px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 10vh;
            perspective: 1000px;
        }

        .scatter-card {
            position: absolute;
            width: 320px;
            height: auto;
            border-radius: 20px; /* Apple-like squircle radius */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08), 0 1px 8px rgba(0, 0, 0, 0.04);
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275), box-shadow 0.5s ease;
            cursor: pointer;
            background-color: white;
            padding: 10px; /* Polaroid-ish white border effect */
        }

        .scatter-card img {
            width: 100%;
            height: auto;
            border-radius: 12px;
            display: block;
            pointer-events: none; /* Prevents dragging the image itself */
        }

        /* Initial scattered positions (you can add more by following this pattern) */
        .scatter-card:nth-child(1) { transform: translate(-180px, 20px) rotate(-12deg); }
        .scatter-card:nth-child(2) { transform: translate(-60px, -30px) rotate(-4deg); }
        .scatter-card:nth-child(3) { transform: translate(70px, 10px) rotate(6deg); }
        .scatter-card:nth-child(4) { transform: translate(190px, -15px) rotate(15deg); }

        /* Hover Effect: Card pops up and straightens */
        .scatter-card:hover {
            transform: scale(1.15) translate(0, -30px) rotate(0deg) !important;
            box-shadow: 0 30px 60px rgba(0, 0, 0, 0.15), 0 4px 15px rgba(0, 0, 0, 0.07);
        }

        /* Mobile responsiveness */
        @media (max-width: 768px) {
            .gallery-container {
                height: 450px;
            }
            .scatter-card { width: 220px; }
            .scatter-card:nth-child(1) { transform: translate(-80px, 30px) rotate(-10deg); }
            .scatter-card:nth-child(2) { transform: translate(-20px, -20px) rotate(-3deg); }
            .scatter-card:nth-child(3) { transform: translate(30px, 15px) rotate(5deg); }
            .scatter-card:nth-child(4) { transform: translate(80px, -10px) rotate(12deg); }
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- Header Section -->
        <header>
            <h1>Raspberry Pi iMac.</h1>
            <h2>Pro power. Miniaturized.</h2>
        </header>

        <!-- Big, readable description -->
        <section class="description">
            <p>
                I engineered a fully functional, miniaturized iMac powered entirely by a Raspberry Pi. 
                This project involved custom 3D modeling, precision resin printing, and soldering custom 
                cooling and display controllers to fit inside a remarkably tiny footprint.
            </p>
            <p>
                Built to emulate the iconic aesthetic of classic Apple hardware, it runs a customized 
                UNIX environment, proving that desktop-class engineering can fit right in the palm of your hand. 
                Hover over the photos below to explore the build process.
            </p>
        </section>

        <!-- Scattered Image Gallery -->
        <section class="gallery-container" id="gallery">
            
            <!-- IMAGE 1 -->
            <div class="scatter-card">
                <img src="image1.jpg" alt="Raspberry Pi iMac Front View">
            </div>

            <!-- IMAGE 2 -->
            <div class="scatter-card">
                <img src="image2.jpg" alt="Inside the case">
            </div>

            <!-- IMAGE 3 -->
            <div class="scatter-card">
                <img src="image3.jpg" alt="3D Printing process">
            </div>

            <!-- IMAGE 4 -->
            <div class="scatter-card">
                <img src="image4.jpg" alt="Final product running">
            </div>

        </section>
    </div>

    <script>
        // Javascript to make the images behave like real photos on a table.
        // When you interact with one, it gets brought to the top of the pile.
        
        const cards = document.querySelectorAll('.scatter-card');
        let highestZIndex = 10;

        cards.forEach(card => {
            // Assign random slight variations on load to make it look organic
            const randomX = Math.floor(Math.random() * 20) - 10;
            const randomY = Math.floor(Math.random() * 20) - 10;
            
            // Mouse enter brings the card to the very front
            card.addEventListener('mouseenter', () => {
                highestZIndex++;
                card.style.zIndex = highestZIndex;
            });
        });
    </script>

</body>
</html>
