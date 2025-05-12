<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>CSS Animation with localStorage and JS</title>
<style>
  /* Basic styles */
  body {
    font-family: Arial, sans-serif;
    padding: 20px;
  }

  /* Style for the button */
  button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    margin: 10px 0;
  }

  /* Style for the image */
  img {
    width: 200px;
    height: auto;
    display: block;
    margin-top: 20px;
    cursor: pointer;
  }

  /* Define a CSS animation for the button (e.g., pulse) */
  @keyframes pulse {
    0% { transform: scale(1); background-color: #4CAF50; color: white; }
    50% { transform: scale(1.2); background-color: #45a049; color: white; }
    100% { transform: scale(1); background-color: #4CAF50; color: white; }
  }

  /* Class to trigger the pulse animation */
  .animate-pulse {
    animation: pulse 0.5s;
  }

  /* Define a CSS animation for the image (e.g., shake) */
  @keyframes shake {
    0% { transform: translate(0, 0); }
    20% { transform: translate(-10px, 0); }
    40% { transform: translate(10px, 0); }
    60% { transform: translate(-10px, 0); }
    80% { transform: translate(10px, 0); }
    100% { transform: translate(0, 0); }
  }

  /* Class to trigger the shake animation */
  .animate-shake {
    animation: shake 0.5s;
  }
</style>
</head>
<body>

<h2>CSS Animations with localStorage and JavaScript</h2>

<!-- Button to trigger animation -->
<button id="myButton">Click me for a surprise!</button>

<!-- Image to animate -->
<img id="myImage" src="C:\Users\caiphus Laka\Downloads\pexels-ahmetyuksek-31444048.jpg" alt="Placeholder Image" />

<!-- Input to store user preference -->
<label for="favoriteColor">Choose your favorite color:</label>
<input type="color" id="favoriteColor" />

<script>
  // Function to store user preference in localStorage
  function savePreference(key, value) {
    localStorage.setItem(key, value);
  }

  // Function to retrieve user preference from localStorage
  function getPreference(key) {
    return localStorage.getItem(key);
  }

  // Apply stored preferences on page load
  document.addEventListener("DOMContentLoaded", () => {
    const colorInput = document.getElementById("favoriteColor");
    const savedColor = getPreference("favoriteColor");
    if (savedColor) {
      colorInput.value = savedColor;
      document.body.style.backgroundColor = savedColor; // Example: change background
    }

    // Listen for color change to save preference
    colorInput.addEventListener("change", () => {
      savePreference("favoriteColor", colorInput.value);
      // Optionally, apply the color
      document.body.style.backgroundColor = colorInput.value;
    });
  });

  // Trigger animations on button click
  document.getElementById("myButton").addEventListener("click", () => {
    const btn = document.getElementById("myButton");
    // Remove class if already present to restart animation
    btn.classList.remove("animate-pulse");
    // Trigger reflow to restart animation
    void btn.offsetWidth;
    // Add class to start animation
    btn.classList.add("animate-pulse");
  });

  // Trigger animation on image click
  document.getElementById("myImage").addEventListener("click", () => {
    const img = document.getElementById("myImage");
    img.classList.remove("animate-shake");
    void img.offsetWidth;
    img.classList.add("animate-shake");
  });
</script>

</body>
</html>
