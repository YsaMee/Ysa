<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Valentines Day</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    .gradient-background {
      background: rgb(255, 208, 229);
      background: linear-gradient(180deg, rgba(255, 208, 229, 1) 0%, rgba(255, 232, 242, 1) 36%, rgba(255, 255, 255, 1) 100%);
    }

    .bounce2 {
      animation: bounce2 2s ease infinite;
    }

    @keyframes bounce2 {
      0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
      }
      40% {
        transform: translateY(-20px);
      }
      60% {
        transform: translateY(-10px);
      }
    }
  </style>
</head>
<body class="gradient-background">
  <div class="flex items-center justify-center h-screen">
    <div class="flex flex-col items-center p-4">
      <img id="imageDisplay" src="https://i.pinimg.com/736x/fc/58/7a/fc587a810b18f8add4f55f3cd4817f74.jpg" alt="Cute kitten with flowers" class="rounded-md h-[300px]" style="object-fit: cover;" />
      <h2 id="valentineQuestion" class="text-4xl font-bold italic text-[#bd1e59] my-4">Will you be my Valentine?</h2>
      <div class="flex gap-4 pt-[20px] items-center" id="responseButtons">
        <button id="yesButton"
          class="bounce2 inline-flex items-center justify-center whitespace-nowrap rounded-md text-[20px] font-medium disabled:pointer-events-none disabled:opacity-50 hover:bg-green-400 min-h-12 min-w-[75px] px-4 py-2 bg-green-500 text-white transition">
          Yes
        </button>
        <button id="noButton"
          class="inline-flex items-center justify-center whitespace-nowrap rounded-md text-[20px] font-medium transition disabled:pointer-events-none disabled:opacity-50 hover:bg-red-700 h-12 min-w-[75px] w-auto px-4 py-2 bg-red-500 text-white">
          No
        </button>
      </div>
    </div>
  </div>

  <script type="module">
    import confetti from 'https://cdn.skypack.dev/canvas-confetti';
    const yesButton = document.getElementById('yesButton');
    const noButton = document.getElementById('noButton');
    const imageDisplay = document.getElementById('imageDisplay');
    const valentineQuestion = document.getElementById('valentineQuestion');
    const responseButtons = document.getElementById('responseButtons');
  
    let noClickCount = 0;
    let buttonHeight = 48; // Starting height in pixels
    let buttonWidth = 80;
    let fontSize = 20; // Starting font size in pixels
    const imagePaths = [
      "https://i.pinimg.com/736x/a3/e1/7a/a3e17a9b0f58e4f11da773773836ae84.jpg", 
      "https://i.pinimg.com/736x/5a/4f/ac/5a4fac9219634d2177fe28644905fc3a.jpg",
      "https://i.pinimg.com/736x/3f/11/24/3f1124faa0a6897b0803ea86319fdcba.jpg",
      "https://i.pinimg.com/736x/a9/97/9e/a9979e400d60ce0a12c6aa9771abb9cb.jpg",
      "https://i.pinimg.com/736x/8a/c3/6d/8ac36d8bcef49b837069fec5a31eeef5.jpg",
      "https://i.pinimg.com/736x/31/d1/76/31d1760c3f880f27d5936f19e152f661.jpg",
      "https://i.pinimg.com/736x/87/2b/f5/872bf5f9b4df7b1b498b793bd79140bb.jpg"
    ];
  
    noButton.addEventListener('click', function() {
      if (noClickCount < 5) {
        noClickCount++;
        imageDisplay.src = imagePaths[noClickCount];
        buttonHeight += 35; // Increase height by 5px on each click
        buttonWidth += 35;
        fontSize += 25; // Increase font size by 1px on each click
        yesButton.style.height = `${buttonHeight}px`; // Update button height
        yesButton.style.width = `${buttonWidth}px`;
        yesButton.style.fontSize = `${fontSize}px`; // Update font size
        if (noClickCount < 6) {
          noButton.textContent = ["No", "Are you sure?", "I really think we'd be cute.", "Don't do this to me :(", "You're breaking my heart", "I'm gonna cry..."][noClickCount];
        }
      }
    });
  
    yesButton.addEventListener('click', () => {
      imageDisplay.src = 'https://i.pinimg.com/736x/ec/46/0a/ec460a723580632481797bba88ada35b.jpg'; // Change to kiss.image
      valentineQuestion.textContent = "Yayyy!! :3"; // Change the question text
      responseButtons.style.display = 'none'; // Hide both buttons
      confetti(); // Trigger confetti animation
    });
  </script>  
</body>
</html>
