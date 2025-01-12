<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>MA Agency - The Dark Nexus</title>
    <style>
        /* General Styles */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #000;
            color: #c00;
            margin: 0;
            padding: 0;
            scroll-behavior: smooth;
            background: linear-gradient(to bottom, #000, #111);
        }
        a {
            text-decoration: none;
        }
        h1, h2, h3, p {
            margin: 0;
        }

        /* Header */
        header {
            text-align: center;
            padding: 50px 20px;
            background: radial-gradient(circle, rgba(34, 34, 34, 0.9), #000);
            color: white;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.8);
        }
        header h1 {
            font-size: 3.5rem;
            letter-spacing: 4px;
            text-shadow: 0 0 15px #c00, 0 0 30px black;
        }
        header p {
            font-size: 1.2rem;
            color: #888;
            text-shadow: 0 0 10px #c00;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: center;
            gap: 20px;
            padding: 15px;
            background-color: #111;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        nav a {
            color: #c00;
            font-size: 1.2rem;
            font-weight: bold;
            text-transform: uppercase;
            transition: all 0.3s ease;
        }
        nav a:hover {
            color: white;
            transform: scale(1.1);
        }

        /* Hero Section */
        .hero {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
            color: white;
            background: url('https://yourimagepath.com/dark-hero-bg.jpg') no-repeat center center/cover;
            box-shadow: inset 0 0 50px rgba(255, 0, 0, 0.5);
        }
        .hero h2 {
            font-size: 4rem;
            text-shadow: 0 0 20px #c00, 0 0 40px black;
            animation: pulse 2s infinite;
        }
        .hero p {
            font-size: 1.5rem;
            margin: 20px 0;
        }
        .hero .cta-button {
            background-color: #111;
            color: #fff;
            padding: 15px 40px;
            border: 2px solid #c00;
            border-radius: 5px;
            font-size: 1.3rem;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 0 10px rgba(255, 0, 0, 0.8);
        }
        .hero .cta-button:hover {
            background-color: #c00;
            transform: scale(1.1);
        }

        /* Targets Section */
        #targets {
            padding: 50px 20px;
            background-color: #111;
            text-align: center;
        }
        #targets h2 {
            font-size: 2.5rem;
            color: white;
        }
        #targets ul {
            list-style: none;
            padding: 0;
        }
        #targets li {
            font-size: 1.5rem;
            color: #c00;
            margin: 15px 0;
            cursor: pointer;
            transition: color 0.3s, transform 0.3s;
        }
        #targets li:hover {
            color: white;
            transform: scale(1.1);
        }

        /* Modal */
        #overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 999;
        }
        .modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 500px;
            padding: 20px;
            background: #222;
            color: white;
            border-radius: 5px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.9);
            z-index: 1000;
        }
        .modal h3 {
            font-size: 2rem;
            margin-bottom: 20px;
        }
        .modal p {
            font-size: 1.2rem;
        }
        .modal .close {
            position: absolute;
            top: 10px;
            right: 20px;
            font-size: 1.5rem;
            cursor: pointer;
            color: #c00;
        }
        .modal .close:hover {
            color: white;
        }

        /* Keyframes */
        @keyframes pulse {
            0%, 100% {
                text-shadow: 0 0 20px #c00, 0 0 40px black;
            }
            50% {
                text-shadow: 0 0 30px white, 0 0 60px #c00;
            }
        }

        /* Media Queries */
        @media (max-width: 768px) {
            header h1 {
                font-size: 2.5rem;
            }
            nav a {
                font-size: 1rem;
            }
            .hero h2 {
                font-size: 3rem;
            }
            #targets h2 {
                font-size: 2rem;
            }
            .modal {
                width: 90%;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>MA Agency</h1>
    <p>The Most Dangerous Nexus of the Dark Web</p>
</header>

<nav>
    <a href="#about">About</a>
    <a href="#agents">Agents</a>
    <a href="#targets">Targets</a>
</nav>

<main>
    <section class="hero">
        <div>
            <h2>Where Shadows Reign</h2>
            <p>Blood marks every corner of this domain. Dare to enter?</p>
            <a href="#targets" class="cta-button">Explore Targets</a>
        </div>
    </section>

    <section id="targets">
        <h2>Target List</h2>
        <ul>
            <li onclick="showTargetInfo('Chonchol')">Chonchol</li>
            <li onclick="showTargetInfo('Tonmoy')">Tonmoy</li>
        </ul>
    </section>
</main>

<div id="overlay"></div>
<div class="modal" id="targetModal">
    <span class="close" onclick="closeModal()">×</span>
    <h3 id="targetName"></h3>
    <p id="targetInfo"></p>
</div>

<script>
    const targets = {
        "Chonchol": "Crime: Smuggling weapons. Status: ELIMINATED.",
        "Tonmoy": "Crime: Cybercrime mastermind."
    };

    function showTargetInfo(name) {
        document.getElementById('targetName').textContent = name;
        document.getElementById('targetInfo').textContent = targets[name];
        document.getElementById('overlay').style.display = 'block';
        document.getElementById('targetModal').style.display = 'block';
    }

    function closeModal() {
        document.getElementById('overlay').style.display = 'none';
        document.getElementById('targetModal').style.display = 'none';
    }
</script>

</body>
</html>
