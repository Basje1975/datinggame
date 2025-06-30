<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Spicy Couples Question Game</title>
<style>
  body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    background: #1e1e2f;
    color: #f0f0f5;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    min-height: 100vh;
  }
  header {
    background: #ff3c78;
    width: 100%;
    padding: 1rem 0;
    text-align: center;
    font-size: 2rem;
    font-weight: bold;
    letter-spacing: 1px;
    box-shadow: 0 2px 10px rgba(255, 60, 120, 0.5);
  }
  main {
    flex: 1;
    max-width: 600px;
    padding: 2rem;
    text-align: center;
  }
  .category-buttons {
    margin-bottom: 1.5rem;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
  }
  button.category-btn, #random-btn {
    background-color: #ff3c78;
    border: none;
    border-radius: 25px;
    padding: 0.6rem 1.3rem;
    color: #fff;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
    flex-grow: 1;
    min-width: 110px;
    max-width: 150px;
  }
  button.category-btn:hover,
  button.category-btn.active,
  #random-btn:hover {
    background-color: #ff1a55;
  }
  #question-box {
    background: #2a2a40;
    border-radius: 15px;
    padding: 2rem;
    font-size: 1.3rem;
    min-height: 140px;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: inset 0 0 10px #ff3c78aa;
    margin-bottom: 2rem;
  }
  #next-btn {
    background-color: #ff3c78;
    border: none;
    border-radius: 30px;
    padding: 0.8rem 2rem;
    color: white;
    font-size: 1.2rem;
    cursor: pointer;
    box-shadow: 0 4px 12px #ff3c78bb;
    transition: background-color 0.3s ease;
    margin-right: 10px;
  }
  #next-btn:hover {
    background-color: #ff1a55;
  }
  #random-btn {
    box-shadow: 0 4px 12px #ff3c78bb;
    margin-left: 10px;
  }
  .buttons-row {
    display: flex;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
    margin-bottom: 2rem;
  }
  footer {
    padding: 1rem;
    font-size: 0.9rem;
    color: #aaa;
  }
  @media (max-width: 460px) {
    main {
      padding: 1rem;
    }
    .category-buttons {
      flex-direction: column;
      gap: 8px;
    }
    .buttons-row {
      flex-direction: column;
      gap: 8px;
    }
    #next-btn, #random-btn {
      width: 100%;
      max-width: none;
      margin: 0;
    }
  }
</style>
</head>
<body>
<header>Spicy Couples Question Game</header>
<main>
  <div class="category-buttons">
    <button class="category-btn" data-category="juicy">Juicy</button>
    <button class="category-btn" data-category="intimate">Intimate</button>
    <button class="category-btn" data-category="spicy">Spicy</button>
    <button class="category-btn" data-category="naughty">Naughty</button>
    <button class="category-btn" data-category="wild">Dirty</button>
  </div>
  <div id="question-box">Select a category to get started!</div>
  <div class="buttons-row">
    <button id="next-btn" disabled>Next Question</button>
    <button id="random-btn">Random Question</button>
  </div>
</main>

<script>
  const questions = {
    juicy: [
      "What’s the most adventurous place you’ve ever wanted to make love?",
      "Have you ever had a secret crush on someone else while we were together?",
      "What’s one fantasy you’ve never told me about?",
      "Have you ever been tempted to cheat, even if you didn’t?",
      "What’s the most romantic thing someone’s done for you before?",
      "If you had to pick one part of my body to stare at all day, what would it be?",
      "What’s a pet name you’ve always wanted me to call you?",
      "What’s the wildest thing you’ve done in public?",
      "Have you ever had a dream about me that made you blush?",
      "What’s one thing that instantly turns you on when you see me?",
      "What’s the craziest place you’d want to get caught making out?",
      "Have you ever thought about how many people I’ve been with before you?",
      "What’s a secret desire you’ve been too shy to share?",
      "What’s the sexiest outfit you’ve ever worn for me or wanted to wear?",
      "If you could erase one memory of us and relive it, which would it be?",
      "What’s the most spontaneous thing you’d want to try with me?",
      "Have you ever fake texted someone to get out of plans for just us time?",
      "What’s a compliment you secretly want to hear from me more often?",
      "What’s a phrase or word I say that drives you crazy in a good way?",
      "What’s the most unforgettable kiss we’ve shared?",
      "What was your first impression of me when we met?",
      "Have you ever had a crush on a fictional character? Who?",
      "What’s something you’ve always wanted to ask me but never did?",
      "What’s the most unforgettable compliment you’ve ever received?",
      "Have you ever lied to impress someone? What was the lie?",
      "What’s a secret talent or skill you have that I don’t know about?",
      "What’s the most romantic date you can imagine us having?",
      "If we could teleport anywhere for a weekend, where would you want to go?",
      "What’s something silly that always makes you laugh about us?",
      "Have you ever had a nickname you hated? What was it?",
      "What’s the most spontaneous thing you’ve done for love?",
      "If you could relive one day with me, which would it be and why?",
      "What’s your favorite memory of us from the past month?",
      "What’s something you’ve learned about yourself since we started dating?",
      "What’s one thing about me that surprised you in a good way?",
      "If you could write a love song about us, what would the title be?",
      "What’s your favorite way to celebrate special occasions together?",
      "Have you ever been jealous of someone? Why?",
      "What’s a habit of mine that you secretly find adorable?",
      "What’s the craziest thing you’d do to make me smile?",
    ],
    intimate: [
      "What’s your favorite way to be comforted after a bad day?",
      "How do you feel about sharing your deepest fears with me?",
      "What’s one part of your body you love having touched the most?",
      "What’s a moment when you felt most connected to me emotionally?",
      "How do you like to be kissed when you want to feel close but not rushed?",
      "What’s something I do that makes you feel completely safe?",
      "What’s a romantic gesture that means more to you than grand gifts?",
      "How do you like to be cuddled after we’re intimate?",
      "What’s one thing you think we could do to deepen our intimacy?",
      "What’s a secret you’ve wanted to tell me but felt nervous about?",
      "How do you feel about slow, sensual massages as foreplay?",
      "What’s the most vulnerable you’ve ever felt with me?",
      "What’s a quality in me that makes you trust me instantly?",
      "What’s something small I do daily that makes you feel loved?",
      "How do you like to be reassured when you’re feeling insecure?",
      "What’s a dream you have for us as a couple in the next year?",
      "What’s your favorite way to wake up next to me?",
      "How do you imagine our ideal romantic getaway?",
      "What’s a song that always reminds you of me or us?",
      "What’s one way I can show you love that you might not expect?",
      "What’s one thing I do that instantly makes you feel loved?",
      "How do you like to be supported when you’re stressed or anxious?",
      "What’s a fear you’ve overcome with my help or support?",
      "What’s your favorite way for us to spend a lazy day together?",
      "How do you feel about sharing your dreams and goals with me?",
      "What’s a small gesture I do that means a lot to you?",
      "What’s something you want us to learn or grow in as a couple?",
      "How do you like to reconnect after a disagreement?",
      "What’s your favorite way to show affection without words?",
      "What’s one thing you wish I knew about your past?",
      "How do you feel about vulnerability in our relationship?",
      "What’s a moment when you felt truly understood by me?",
      "What’s something new you’d like to try to deepen our bond?",
      "How do you like to celebrate our milestones together?",
      "What’s a secret wish you have for our future?",
      "What’s your love language, and how do you like it expressed?",
      "How do you feel about sharing your insecurities with me?",
      "What’s a moment when you felt proud of us as a couple?",
      "What’s your favorite way to say “I love you” without words?",
      "How do you imagine us growing old together?",
    ],
    spicy: [
      "What’s your favorite type of kiss to start things off?",
      "Have you ever wanted to role-play? If yes, what scenario?",
      "What’s one thing you wish I’d initiate more often in the bedroom?",
      "What’s your favorite part of my body to undress first?",
      "Have you ever wanted to try toys or props while we’re together?",
      "What’s the naughtiest thing you’ve ever done with me?",
      "How do you feel about whispering dirty things in public?",
      "What’s a secret move or touch that always gets you going?",
      "What’s your favorite time of day for intimacy and why?",
      "Would you ever want to try blindfolds or restraints?",
      "What’s the hottest compliment I could say during sex?",
      "Have you ever fantasized about watching me with someone else?",
      "What’s a new position or technique you want to try together?",
      "What’s your favorite way to tease me without touching?",
      "How do you feel about using food or drinks in our play?",
      "Have you ever been turned on by something unexpected?",
      "What’s your favorite place on my body to be kissed slowly?",
      "How do you like to be touched to build anticipation?",
      "What’s your idea of the perfect sexy outfit for me?",
      "Would you ever want to try a quickie in a risky place?",
      "What’s your favorite way to be kissed that drives you wild?",
      "Have you ever wanted to try sexting? What would you say first?",
      "What’s a fantasy involving costumes or dress-up you want to explore?",
      "What’s the sexiest thing I’ve ever done that surprised you?",
      "How do you feel about teasing with ice cubes or warm oils?",
      "What’s a secret spot on your body that’s incredibly sensitive?",
      "Have you ever wanted to try a sensual dance for me?",
      "What’s your favorite way to initiate intimacy unexpectedly?",
      "How do you feel about using scented candles or music to set the mood?",
      "What’s a sexy phrase or word you want me to say more often?",
      "What’s your favorite way to be touched that’s slow and teasing?",
      "Have you ever wanted to try a massage that leads to something more?",
      "What’s a daring place you want to kiss me passionately?",
      "How do you feel about incorporating flavored lubricants or edible treats?",
      "What’s a secret move or touch that always makes you shiver?",
      "Have you ever had a naughty dream about me that you want to share?",
      "What’s your favorite way to build anticipation before intimacy?",
      "How do you feel about role reversal or switching roles in bed?",
      "What’s one thing you want to whisper in my ear during a romantic moment?",
      "What’s your favorite way to be surprised with affection?",
    ],
    naughty: [
      "What’s one naughty thought you had about me today?",
      "Have you ever wanted to surprise me with something sexy?",
      "What’s your favorite way to catch me off guard in a good way?",
      "Have you ever imagined us in a scandalous situation?",
      "What’s the most inappropriate place you’ve wanted to make love?",
      "What’s a secret fantasy involving costumes or uniforms?",
      "Have you ever wanted to send me a flirty text during work?",
      "What’s one naughty thing you want me to do when I get home?",
      "How do you feel about public displays of affection that border on risky?",
      "What’s a seductive nickname you’d want to call me?",
      "Have you ever wanted to play a sexy game together?",
      "What’s the naughtiest thing you’ve thought about doing with me in the car?",
      "What’s your favorite way to initiate when you want me badly?",
      "Have you ever imagined us in a steamy movie scene?",
      "What’s one naughty secret you’ve kept just for yourself?",
      "How do you feel about teasing text messages throughout the day?",
      "What’s your favorite way to be teased until you can’t take it anymore?",
      "Have you ever wanted to experiment with temperature play?",
      "What’s a sexy surprise you’d want to plan for me?",
      "What’s one thing you want to do that we haven’t tried yet?",
      "What’s a naughty secret you’ve never told anyone before?",
      "Have you ever wanted to sneak away for a quick, secret rendezvous?",
      "What’s the most mischievous thing you’ve done to get my attention?",
      "How do you feel about teasing me with a slow striptease?",
      "What’s one place you want to try making love that’s totally unexpected?",
      "Have you ever wanted to send me a flirty photo? What would it be?",
      "What’s your favorite way to playfully dominate or be dominated?",
      "How do you feel about using handcuffs or silk scarves for fun?",
      "What’s a naughty game you’d want to play with me?",
      "Have you ever thought about us being caught in the act? Where?",
      "What’s your favorite way to tease me until I can’t resist anymore?",
      "Have you ever wanted to try light spanking or playful slaps?",
      "What’s a secret fantasy involving public flirting or teasing?",
      "How do you feel about whispering naughty things in public discreetly?",
      "What’s one thing you want me to do to surprise you when you least expect it?",
      "Have you ever wanted to roleplay a boss/employee or teacher/student scenario?",
      "What’s the naughtiest text you’ve imagined sending me?",
      "How do you feel about using ice or feathers as playful tools?",
      "What’s a sexy dare you’d want to challenge me with?",
      "Have you ever wanted to experiment with temperature play?",
    ],
    wild: [
      "What’s your dirtiest thought about me right now?",
      "Have you ever wanted to talk dirty but didn’t know what to say?",
      "What’s the most explicit fantasy you’ve had with me?",
      "What’s your favorite dirty word to hear during sex?",
      "Have you ever wanted to record a private video or audio for me?",
      "What’s the sexiest thing you’d do if no one could ever find out?",
      "How do you feel about dirty or sexy talk over the phone or video?",
      "What’s one dirty or sexy secret you’ve been dying to confess?",
      "What’s the wildest place you want to have sex but haven’t yet?",
      "How do you feel about trying anal or other taboo activities?",
      "What’s your favorite way to be dominated or take control?",
      "What’s a wild sexual experience you’ve always wanted to explore with a partner but haven’t yet?",
      "What’s the dirtiest thing you’ve ever whispered in my ear?",
      "What’s a kink or fetish you’re curious to explore with me?",
      "How do you feel about group play or watching others?",
      "What’s the most taboo thing you’d want to try just once?",
      "How do you feel about mutual masturbation via a webcam?",
      "What’s one dirty thought that makes you smile secretly?",
      "How do you feel about incorporating toys or props?",
      "What’s your ultimate sexual fantasy that you want to make real?",
      "What’s the hottest sexual fantasy you’ve been too shy to tell me?",
      "Have you ever wanted to try dirty talk but didn’t know where to start?",
      "What’s your favorite explicit compliment to hear during intimacy?",
      "How do you feel about recording our intimate moments for private fun?",
      "What’s the wildest thing you want to do that you’ve never said out loud?",
      "Have you ever wanted to try using toys together? Which ones?",
      "What’s your favorite way to be dominated or to take control?",
      "How do you feel about public sex or exhibitionism fantasies?",
      "What’s the kink or fetish you’re most curious about exploring?",
      "Have you ever wanted to try bondage or light restraint play?",
      "What’s a taboo scenario you want to roleplay with me?",
      "How do you feel about dirty talk over video calls?",
      "What’s your favorite way to be teased until you’re begging?",
      "Have you ever wanted to watch or be watched during intimacy?",
      "What’s the most explicit thing you’ve ever whispered in my ear?",
      "How do you feel about trying anal or other adventurous acts?",
      "What’s your favorite dirty word or phrase to hear from me?",
      "Have you ever wanted to experiment with spanking or impact play?",
      "What’s one wild fantasy you want to make a reality soon?",
      "How do you feel about incorporating roleplay that involves power dynamics?",
    ]
  };

  let currentCategory = null;
  let usedIndexes = {};

  // Initialize usedIndexes for each category
  Object.keys(questions).forEach(cat => {
    usedIndexes[cat] = [];
  });

  const categoryButtons = document.querySelectorAll('.category-btn');
  const questionBox = document.getElementById('question-box');
  const nextBtn = document.getElementById('next-btn');
  const randomBtn = document.getElementById('random-btn');

  function getRandomQuestion(category) {
    if (!questions[category]) return null;
    if (usedIndexes[category].length === questions[category].length) {
      // Reset used questions when all have been shown
      usedIndexes[category] = [];
      alert(`You've gone through all questions in the "${category.charAt(0).toUpperCase() + category.slice(1)}" category. Starting over!`);
    }
    let index;
    do {
      index = Math.floor(Math.random() * questions[category].length);
    } while (usedIndexes[category].includes(index));
    usedIndexes[category].push(index);
    return questions[category][index];
  }

  categoryButtons.forEach(button => {
    button.addEventListener('click', () => {
      categoryButtons.forEach(btn => btn.classList.remove('active'));
      button.classList.add('active');
      currentCategory = button.getAttribute('data-category');
      nextBtn.disabled = false;
      const question = getRandomQuestion(currentCategory);
      questionBox.textContent = question || "No questions available.";
    });
  });

  nextBtn.addEventListener('click', () => {
    if (!currentCategory) return;
    const question = getRandomQuestion(currentCategory);
    questionBox.textContent = question || "No questions available.";
  });

  randomBtn.addEventListener('click', () => {
    // Remove active highlight from category buttons
    categoryButtons.forEach(btn => btn.classList.remove('active'));
    currentCategory = null;
    nextBtn.disabled = false;

    const categories = Object.keys(questions);
    // Pick a random category
    const randomCategory = categories[Math.floor(Math.random() * categories.length)];
    const question = getRandomQuestion(randomCategory);
    questionBox.textContent = question || "No questions available.";
  });
</script>
</body>
</html>
