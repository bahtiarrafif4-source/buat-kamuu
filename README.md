[script.js](https://github.com/user-attachments/files/23326403/script.js)
document.addEventListener('DOMContentLoaded', function() {
    const heartsContainer = document.querySelector('.hearts-container');
    const startButton = document.getElementById('startButton');
    const message = document.getElementById('message');

    function createHeart() {
        const heart = document.createElement('div');
        heart.classList.add('heart');[index.html](https://github.com/user-attachments/files/23326407/index.html)
[TODO.md](https://github.com/user-attachments/files/23326405/TODO.md)
[styles.css](https://github.com/user-attachments/files/23326404/styles.css)

        heart.innerHTML = '❤️';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = Math.random() * 3 + 3 + 's'; // 3-6 seconds
        heartsContainer.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 6000);
    }

    // Create hearts every 300ms
    setInterval(createHeart, 300);

    // Add click event to create extra hearts
    document.addEventListener('click', function() {
        for (let i = 0; i < 5; i++) {
            setTimeout(createHeart, i * 100);
        }
    });

    let clickCount = 0;

    // Start button event
    startButton.addEventListener('click', function() {
        clickCount++;
        if (clickCount < 3) {
            // Move the heart to a random position
            const container = document.querySelector('.container');
            const containerRect = container.getBoundingClientRect();
            const heart = startButton;
            const maxX = containerRect.width - heart.offsetWidth;
            const maxY = containerRect.height - heart.offsetHeight;
            const randomX = Math.random() * maxX;
            const randomY = Math.random() * maxY;
            heart.style.position = 'absolute';
            heart.style.left = randomX + 'px';
            heart.style.top = randomY + 'px';
        } else {
            // After third click, show name input
            document.querySelector('.start-section').style.display = 'none';
            document.getElementById('nameInput').style.display = 'block';
        }
    });

    // Submit button event
    document.getElementById('submitButton').addEventListener('click', function() {
        const name = document.getElementById('nameField').value.trim();
        if (name) {
            document.getElementById('userName').textContent = name;
            document.getElementById('nameInput').style.display = 'none';
            message.style.display = 'block';
            message.style.animation = 'slideIn 3s ease-in-out both';
        } else {
            alert('Silakan masukkan nama kamu!');
        }
    });
});

body {
    font-family: 'Dancing Script', cursive;
    background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #fecfef 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    overflow: hidden;
}

.hearts-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
}

.heart {
    position: absolute;
    color: #ff6b9d;
    font-size: 24px;
    animation: float 6s linear infinite;
}

@keyframes float {
    0% {
        transform: translateY(100vh) rotate(0deg);
        opacity: 1;
    }
    100% {
        transform: translateY(-100px) rotate(360deg);
        opacity: 0;
    }
}

.container {
    background-color: rgba(255, 255, 255, 0.9);
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 0 30px rgba(0, 0, 0, 0.2);
    text-align: center;
    max-width: 600px;
    animation: fadeIn 2s ease-in-out;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(50px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

h1 {
    color: #e91e63;
    font-size: 3em;
    margin-bottom: 20px;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
}

.message {
    font-family: 'Arial', sans-serif;
    font-size: 1.2em;
    line-height: 1.6;
    color: #333;
    animation: slideIn 3s ease-in-out 1s both;
}

@keyframes slideIn {
    from {
        opacity: 0;
        transform: translateX(-50px);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

.message p {
    margin-bottom: 15px;
}

.start-section {
    margin-bottom: 20px;
    position: relative;
}

.instruction {
    font-size: 1.2em;
    color: #e91e63;
    margin-bottom: 10px;
    font-weight: bold;
}

#startButton {
    font-size: 4em;
    background: none;
    border: none;
    cursor: pointer;
    transition: transform 0.3s ease;
    animation: pulse 2s infinite;
}

#startButton:hover {
    transform: scale(1.1);
}

@keyframes pulse {
    0% {
        transform: scale(1);
    }
    50% {
        transform: scale(1.05);
    }
    100% {
        transform: scale(1);
    }
}

.name-input {
    margin-bottom: 20px;
}

#nameField {
    padding: 10px;
    font-size: 1em;
    border: 2px solid #e91e63;
    border-radius: 5px;
    margin-right: 10px;
    width: 200px;
    text-align: center;
}

#submitButton {
    padding: 10px 20px;
    font-size: 1em;
    background-color: #e91e63;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

#submitButton:hover {
    background-color: #c2185b;
}

# TODO List for Romantic Encouragement Page with Interactive Start

- [x] Update index.html to display the encouragement message instead of the birthday message
- [x] Update styles.css if needed for any adjustments (keep romantic styling and animations)
- [x] Update script.js if needed for any adjustments (keep floating hearts)
- [x] Test the page by opening it in a browser to ensure animations work
- [x] Add a "Start" button to trigger the message appearance
- [x] Hide the message initially and show it on button click with animation
- [x] Update styles for the button
- [x] Test the interactive feature
- [x] Add input field for name after Start button click
- [x] Add Submit button to confirm name input
- [x] Update script.js to handle name input and personalize message
- [x] Update styles.css for input and submit button
- [x] Test the name input interaction
- [x] Change Start button to heart shape
- [x] Add text and arrow to indicate clicking the heart
- [x] Make heart button move on click
- [x] Show name input only after third click

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semangat, Sayang!</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="hearts-container"></div>
    <div class="container">
        <div class="start-section">
            <p class="instruction">Klik hati ini untuk memulai →</p>
            <button id="startButton">❤️</button>
        </div>
        <div class="name-input" id="nameInput" style="display: none;">
            <input type="text" id="nameField" placeholder="Masukkan nama kamu" maxlength="20">
            <button id="submitButton">Submit</button>
        </div>
        <div class="message" id="message" style="display: none;">
            <h1>Semangat, Yaa 🌟</h1>
            <p>Haloo <span id="userName">intann</span> 🌟</p>
            <p>Aku tahu hari ini bukan hari biasa buat kamu. Hari ini kamu lagi berjuang di lomba yang udah kamu persiapin dengan sepenuh hati. Aku cuma mau bilang, aku bangga banget sama kamu. Serius. Nggak semua orang punya keberanian buat tampil, apalagi untuk berkompetisi dan ngeluarin kemampuan terbaiknya seperti kamu.</p>
            <p>Aku tahu kamu udah latihan, capek, dan kadang mungkin sempat ragu sama diri sendiri. Tapi percaya deh, semua kerja keras kamu nggak akan sia-sia. Kamu itu hebat — bukan cuma karena bisa menang, tapi karena kamu mau berjuang. Kamu udah jauh banget sampai di titik ini, dan aku yakin hasilnya bakal indah.</p>
            <p>Kalau nanti rasa gugup datang, tarik napas pelan-pelan. Ingat, kamu nggak sendirian. Ada aku di sini, yang diam-diam selalu ngedoain kamu dari jauh, berharap semua berjalan lancar. Aku percaya sama kamu, lebih dari kamu percaya pada diri sendiri.</p>
            <p>Menang atau nggak, kamu tetap luar biasa di mataku. Karena buatku, keberanian kamu untuk maju itu udah kemenangan tersendiri. Jadi, hadapi semuanya dengan senyum, ya. Tunjukkan versi terbaik dari dirimu — bukan buat orang lain, tapi buat diri kamu sendiri.</p>
            <p>Dan jangan lupa, setelah lomba selesai, entah hasilnya gimana, aku tetap bakal bilang hal yang sama: aku bangga banget sama kamu. 🤍</p>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
