# Fernvaldaycard
Valentine’s Day card
// JavaScript version of the interactive Valentine's Day card

const messages = [ "Happy Valentine’s Day, Lucy ❤️", "Long distance just means my heart has to travel a little further to reach you 💌", "You’re my favorite notification, my favorite voice, and my favorite person.", "If loving you was a job, I’d be Employee of the Month every month 😌", "No matter the miles between us, you’ll always be right here 💘" ];

const photos = ["/lucy1.jpg", "/lucy2.jpg"]; const backgroundSong = "/todos-los-dias.mp3";

let step = 0;

// Create main container const container = document.createElement('div'); container.style.minHeight = '100vh'; container.style.display = 'flex'; container.style.alignItems = 'center'; container.style.justifyContent = 'center'; container.style.backgroundColor = '#ffe4e6'; container.style.padding = '24px'; document.body.appendChild(container);

// Card element const card = document.createElement('div'); card.style.width = '100%'; card.style.maxWidth = '400px'; card.style.background = 'white'; card.style.borderRadius = '1rem'; card.style.boxShadow = '0 10px 25px rgba(0,0,0,0.2)'; card.style.padding = '24px'; container.appendChild(card);

// Message display const messageEl = document.createElement('h1'); messageEl.style.fontSize = '1.25rem'; messageEl.style.fontWeight = '600'; messageEl.style.color = '#db2777'; messageEl.style.textAlign = 'center'; messageEl.style.marginBottom = '16px'; card.appendChild(messageEl);

// Image display const imgEl = document.createElement('img'); imgEl.style.width = '12rem'; imgEl.style.height = '12rem'; imgEl.style.objectFit = 'cover'; imgEl.style.borderRadius = '1rem'; imgEl.style.boxShadow = '0 4px 15px rgba(0,0,0,0.2)'; imgEl.style.display = 'block'; imgEl.style.margin = '0 auto 16px'; card.appendChild(imgEl);

// Button const button = document.createElement('button'); button.textContent = 'Tap for More ❤️'; button.style.borderRadius = '1rem'; button.style.padding = '0.5rem 1.5rem'; button.style.fontSize = '1rem'; button.style.cursor = 'pointer'; button.style.display = 'block'; button.style.margin = '0 auto'; card.appendChild(button);

// Audio const audio = new Audio(backgroundSong); audio.loop = true;

// Heart sparkle animation function addSparkles() { const sparkle = document.createElement('div'); sparkle.textContent = '✨💖✨'; sparkle.style.position = 'absolute'; sparkle.style.fontSize = '2rem'; sparkle.style.color = '#f472b6'; sparkle.style.left = '50%'; sparkle.style.top = '50%'; sparkle.style.transform = 'translate(-50%, -50%)'; card.appendChild(sparkle); setTimeout(() => sparkle.remove(), 2000); }

function updateCard() { if (step === 1 || step === 3) addSparkles(); if (step === 1) imgEl.src = photos[0]; else if (step === 3) imgEl.src = photos[1]; else imgEl.src = '';

messageEl.textContent = messages[step];

if (step >= messages.length - 1) { button.textContent = 'Obviously Yes 😘'; button.onclick = null; } }

button.onclick = () => { if (step === 0) audio.play(); step++; updateCard(); };

updateCard();
