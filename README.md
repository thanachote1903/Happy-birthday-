// Happy Birthday JavaScript Animation

// Function to create and display the "Happy Birthday JavaScript" message
function showMessage() {
  const body = document.body;

  // Create the main container for the message
  const container = document.createElement('div');
  container.style.position = 'fixed';
  container.style.top = '50%';
  container.style.left = '50%';
  container.style.transform = 'translate(-50%, -50%)';
  container.style.textAlign = 'center';
  container.style.fontFamily = 'Arial, sans-serif';
  container.style.zIndex = '9999';

  // Create the message
  const message = document.createElement('h1');
  message.textContent = '🎉 Happy Birthday JavaScript! 🎂';
  message.style.fontSize = '2.5rem';
  message.style.color = '#ff8c00';
  message.style.marginBottom = '20px';

  // Append the message to the container
  container.appendChild(message);

  // Create a button to remove the message
  const button = document.createElement('button');
  button.textContent = 'Close';
  button.style.padding = '10px 20px';
  button.style.fontSize = '1rem';
  button.style.backgroundColor = '#ff4500';
  button.style.color = 'white';
  button.style.border = 'none';
  button.style.cursor = 'pointer';
  button.style.borderRadius = '5px';

  // Button click event to remove the message
  button.addEventListener('click', () => {
    body.removeChild(container);
  });

  // Append the button to the container
  container.appendChild(button);

  // Append the container to the body
  body.appendChild(container);
}

// Fireworks animation
function launchFireworks() {
  const colors = ['#ff6347', '#ffa500', '#7fff00', '#1e90ff', '#dda0dd'];

  for (let i = 0; i < 30; i++) {
    const particle = document.createElement('div');
    const size = Math.random() * 10 + 5;
    particle.style.width = `${size}px`;
    particle.style.height = `${size}px`;
    particle.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
    particle.style.position = 'fixed';
    particle.style.borderRadius = '50%';
    particle.style.pointerEvents = 'none';

    const startX = Math.random() * window.innerWidth;
    const startY = Math.random() * window.innerHeight;
    const endX = Math.random() * window.innerWidth;
    const endY = Math.random() * window.innerHeight;

    particle.style.left = `${startX}px`;
    particle.style.top = `${startY}px`;

    document.body.appendChild(particle);

    const animation = particle.animate(
      [
        { transform: `translate(${startX}px, ${startY}px)` },
        { transform: `translate(${endX}px, ${endY}px)` },
      ],
      {
        duration: 1000 + Math.random() * 2000,
        easing: 'ease-out',
      }
    );

    animation.onfinish = () => {
      document.body.removeChild(particle);
    };
  }
}

// Run the fireworks and show the message
launchFireworks();
showMessage();
