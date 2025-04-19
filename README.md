# Test<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Cool Website</title>
  <style>
    body {
      font-family: 'Courier New', monospace;
      background: #111;
      color: #f2f2f2;
      padding: 40px;
      transition: background 2s;
    }
    h1 {
      font-size: 3em;
    }
    .fade {
      opacity: 0.2;
    }
    .glitch {
      color: #ff3cac;
    }
  </style>
</head>
<body>
  <h1>Welcome to My Cool Website</h1>
  <p>This website is totally normal. Nothing weird is going to happen.</p>
  <p>Just hang out and enjoy the content. Maybe grab a coffee.</p>
  <p>Everything here is stable. Permanent. Trustworthy.</p>

  <script>
    const words = document.querySelectorAll("p, h1");
    const glitchChars = "!@#$%^&*()_+=-[]{}|;:',.<>?/";

    function corruptText(text) {
      return text.split('').map(char => {
        if (Math.random() < 0.08) {
          return glitchChars[Math.floor(Math.random() * glitchChars.length)];
        }
        return char;
      }).join('');
    }

    function fadeWords() {
      words.forEach(el => {
        if (Math.random() < 0.3) {
          el.textContent = corruptText(el.textContent);
        }
        if (Math.random() < 0.1) {
          el.classList.add('fade');
        }
        if (Math.random() < 0.05) {
          el.remove();
        }
      });

      if (document.body.children.length <= 1) {
        document.body.style.background = '#000';
        let end = document.createElement('p');
        end.textContent = "There's nothing left.";
        end.className = 'glitch';
        document.body.appendChild(end);
      }
    }

    setInterval(fadeWords, 3000);
  </script>
</body>
</html>
