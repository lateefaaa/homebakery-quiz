<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Which Home Bakery Dessert Are You?</title>
  <style>
    body { font-family: 'Segoe UI', sans-serif; background: #fff7f2; text-align: center; padding: 2em; color: #5c4033; }
    h1 { font-size: 2em; margin-bottom: 20px; }
    .question { margin-bottom: 30px; }
    button { padding: 10px 20px; margin: 10px; cursor: pointer; border: none; border-radius: 8px; background-color: #f7d9c4; color: #5c4033; font-weight: bold; }
    button:hover { background-color: #eac7b0; }
    #result { margin-top: 40px; font-size: 1.4em; font-weight: bold; }
  </style>
</head>
<body>

  <h1>🍰 Which Home Bakery Dessert Are You?</h1>
  <div id="quiz"></div>
  <div id="result"></div>

  <script>
    const quizData = [
      {
        question: "What's your ideal day off?",
        answers: {
          "Spa day, skincare, and a good book": "saffron",
          "Getting creative or DIY crafting": "cheesecake",
          "Sunshine, music, and a bit of chaos": "mango",
          "A cozy corner, coffee, and deep convos": "tiramisu",
          "Couch, movies, and snacks on repeat": "cookie"
        }
      },
      {
        question: "Pick a flavor profile:",
        answers: {
          "Light & floral with a luxe twist": "saffron",
          "Rich, creamy, and timeless": "cheesecake",
          "Fruity and fun": "mango",
          "Layered, deep, and slightly dramatic": "tiramisu",
          "Classic, warm, and gooey": "cookie"
        }
      },
      {
        question: "How do friends describe you?",
        answers: {
          "Elegant and put-together": "saffron",
          "Reliable and nurturing": "cheesecake",
          "Fun, spontaneous, a little wild": "mango",
          "Mysterious and soulful": "tiramisu",
          "Comforting and loyal": "cookie"
        }
      }
    ];

    const scores = {
      saffron: 0,
      cheesecake: 0,
      mango: 0,
      tiramisu: 0,
      cookie: 0
    };

    let currentQuestion = 0;

    function renderQuiz() {
      const quiz = document.getElementById("quiz");
      quiz.innerHTML = "";

      if (currentQuestion < quizData.length) {
        const q = quizData[currentQuestion];
        const questionDiv = document.createElement("div");
        questionDiv.className = "question";
        questionDiv.innerHTML = `<h2>${q.question}</h2>`;
        
        for (let [text, dessert] of Object.entries(q.answers)) {
          const btn = document.createElement("button");
          btn.textContent = text;
          btn.onclick = () => {
            scores[dessert]++;
            currentQuestion++;
            renderQuiz();
          };
          questionDiv.appendChild(btn);
        }

        quiz.appendChild(questionDiv);
      } else {
        const result = Object.entries(scores).sort((a, b) => b[1] - a[1])[0][0];
        const descriptions = {
          saffron: "🌸 You’re the Saffron Milk Cake – refined, elegant, and loved by those with great taste.",
          cheesecake: "🍰 You’re the Baked Cheesecake – dependable, soft-hearted, and always comforting.",
          mango: "🥭 You’re the Mango Flop – vibrant, energetic, and full of sunshine!",
          tiramisu: "☕ You’re the Tiramisu – deep, layered, and unforgettable.",
          cookie: "🍪 You’re the Chewy Melt Cookie – warm, cozy, and everyone’s favorite go-to."
        };
        document.getElementById("result").textContent = descriptions[result];
      }
    }

    renderQuiz();
  </script>
</body>
</html>
