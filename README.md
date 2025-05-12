# week7-html-assignment
html
<button id="animateBtn">Click me!</button>

css
#animateBtn {
  padding: 12px 24px;
  font-size: 16px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: transform 0.4s ease, background-color 0.4s ease;
}

/* Animation triggered by adding the "active" class */
#animateBtn.active {
  transform: scale(1.2) rotate(10deg);
  background-color: #2ecc71;
  transition: transform 0.4s ease, background-color 0.4s ease;
}


javascript
const button = document.getElementById('animateBtn');

// Function to apply animation class
function triggerAnimation() {
  button.classList.add('active');
  // Remove the class after animation duration to allow re-trigger
  setTimeout(() => {
    button.classList.remove('active');
  }, 400);
}

// Function to save user preference (e.g., animation enabled)
function savePreference(enabled) {
  localStorage.setItem('animationEnabled', enabled);
}

// Function to load user preference
function loadPreference() {
  return localStorage.getItem('animationEnabled') === 'true';
}

// Event listener to trigger animation and save preference
button.addEventListener('click', () => {
  triggerAnimation();
  savePreference(true);
});

// On page load, check preference and optionally trigger animation
window.addEventListener('load', () => {
  if (loadPreference()) {
    // Optionally trigger animation or apply styles based on preference
    console.log('User prefers animations.');
  } else {
    console.log('No animation preference found.');
  }
});
