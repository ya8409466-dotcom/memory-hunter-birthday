# memory-hunter-birthday

<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>THE LAST MISSION</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;800&family=Playfair+Display:wght@600;700&display=swap');

:root {
  --gold: #d8b56b;
  --gold-light: #f1d99e;
  --bg: #080a10;
  --panel: #11151f;
  --muted: #9ba0aa;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  min-height: 100vh;
  color: #f5f0e5;
  background:
    radial-gradient(ellipse at 50% 0%, #24202a 0%, transparent 55%),
    var(--bg);
  font-family: 'Cairo', sans-serif;
  display: flex;
  justify-content: center;
  padding: 25px 15px;
}
main {
  width: 100%;
  max-width: 520px;
  margin: auto;
}
.top {
  text-align: center;
  margin-bottom: 25px;
}
.symbol {
  color: var(--gold);
  font-size: 30px;
  margin-bottom: 8px;
}
.english {
  font-family: 'Playfair Display', serif;
  letter-spacing: 3px;
  color: var(--gold);
}
h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(30px, 8vw, 43px);
  margin: 5px 0;
  letter-spacing: 2px;
}
.subtitle {
  color: var(--muted);
  font-size: 12px;
  letter-spacing: 2px;
}
.line {
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--gold), transparent);
  margin: 22px 0;
}
.card {
  background: linear-gradient(145deg, #151a25, #0d1018);
  border: 1px solid #5b4a2d;
  border-radius: 16px;
  padding: 27px 21px;
  box-shadow: 0 15px 45px #0008;
}
.tag {
  color: var(--gold);
  font-size: 11px;
  letter-spacing: 3px;
  text-align: center;
  direction: ltr;
}
h2 {
  text-align: center;
  font-size: 23px;
  margin: 12px 0;
}
p {
  line-height: 2;
  color: #d6d3cc;
  font-size: 15px;
}
.center { text-align: center; }
.muted { color: var(--muted); }
.gold { color: var(--gold-light); }
button {
  width: 100%;
  border: 1px solid var(--gold);
  border-radius: 8px;
  padding: 13px;
  background: linear-gradient(120deg, #b58b43, #e4c783);
  color: #15120c;
  font-family: 'Cairo', sans-serif;
  font-weight: 800;
  font-size: 15px;
  cursor: pointer;
  margin-top: 17px;
}
button:active { transform: scale(.98); }
input {
  display: block;
  width: 100%;
  padding: 14px;
  margin-top: 18px;
  border-radius: 8px;
  border: 1px solid #625333;
  background: #090c13;
  color: white;
  text-align: center;
  font-family: 'Cairo', sans-serif;
  font-size: 17px;
  outline: none;
}
input:focus { border-color: var(--gold-light); }
.feedback {
  min-height: 30px;
  text-align: center;
  color: #e9bd75;
  font-size: 13px;
  margin-top: 12px;
}
.progress {
  display: flex;
  gap: 7px;
  justify-content: center;
  margin: 20px 0;
  direction: ltr;
}
.dot {
  width: 30px;
  height: 3px;
  background: #343743;
  border-radius: 5px;
}
.dot.done { background: var(--gold); }
.riddle {
  border-right: 2px solid var(--gold);
  padding: 8px 14px;
  margin: 20px 0;
  background: #ffffff08;
  border-radius: 5px;
}
.scramble {
  direction: ltr;
  text-align: center;
  color: var(--gold-light);
  font-size: 21px;
  letter-spacing: 3px;
  margin: 23px 0;
}
.hidden { display: none !important; }
.final-code {
  direction: ltr;
  letter-spacing: 12px;
  font-size: 25px;
}
.message-line {
  opacity: 0;
  transform: translateY(10px);
  animation: appear .8s forwards;
  margin: 0 0 13px;
  text-align: right;
}
@keyframes appear {
  to { opacity: 1; transform: translateY(0); }
}
.heart {
  color: #d9a7a1;
  font-size: 24px;
}
.footer {
  text-align: center;
  color: #777b83;
  font-size: 10px;
  letter-spacing: 2px;
  margin-top: 23px;
  direction: ltr;
}
</style>
</head>

<body>
<main>
  <header class="top">
    <div class="symbol">✦</div>
    <div class="english">A CLASSIFIED BIRTHDAY FILE</div>
    <h1>THE LAST MISSION</h1>
    <div class="subtitle">ONLY THE RIGHT PERSON CAN SOLVE IT</div>
  </header>

  <div class="line"></div>

  <section class="card" id="intro">
    <div class="tag">CONFIDENTIAL FILE #001</div>
    <h2>أهلًا أيها المحقق...</h2>
    <p class="center">
      قدامك مهمة من 4 مراحل.<br>
      كل مرحلة فيها لغز، وكل إجابة هتقربك من كشف السر الأخير.
    </p>
    <p class="center muted">خليك مركز... التفاصيل الصغيرة هي المفتاح.</p>
    <button onclick="startGame()">START MISSION</button>
  </section>

  <section class="card hidden" id="game">
    <div class="tag" id="levelTag">LEVEL 01</div>
    <div class="progress" id="progress">
      <span class="dot"></span><span class="dot"></span>
      <span class="dot"></span><span class="dot"></span>
    </div>
    <h2 id="levelTitle"></h2>
    <p id="question"></p>
    <div class="riddle hidden" id="extra"></div>
    <div class="scramble hidden" id="scramble"></div>
    <input id="answer" type="text" placeholder="اكتب إجابتك هنا..." autocomplete="off">
    <button onclick="checkAnswer()">SUBMIT ANSWER</button>
    <div class="feedback" id="feedback"></div>
  </section>

  <section class="card hidden" id="codeScreen">
    <div class="tag">FINAL SECURITY CHECK</div>
    <h2>وصلت للنهاية...</h2>
    <p class="center">كل الإجابات كانت بتشير لحاجة واحدة.<br>دلوقتي اجمع الأرقام وافتح الملف الأخير.</p>
    <div class="riddle center">
      <p>عدد حروف PUBG</p>
      <p>عدد حروف الكلمة السرية</p>
      <p>عدد حروف كلمة «حلو»</p>
    </div>
    <input id="secretCode" class="final-code" type="text" inputmode="numeric" maxlength="3" placeholder="•••">
    <button onclick="checkCode()">UNLOCK THE FILE</button>
    <div class="feedback" id="codeFeedback"></div>
  </section>

  <section class="card hidden center" id="completed">
    <div class="symbol">✦</div>
    <div class="tag">MISSION COMPLETED</div>
    <h2>تم فتح الملف بنجاح</h2>
    <p class="center">كل لغز كان وراه حكاية...<br>ودلوقتي جه وقت آخر مفاجأة.</p>
    <button onclick="openMessage()">OPEN YOUR FINAL MESSAGE</button>
  </section>

  <section class="card hidden" id="message">
    <div class="tag center">A MESSAGE FROM THE HEART</div>
    <h2 class="center">Before the day ends...</h2>
    <div class="line"></div>
    <div id="messageText"></div>
    <div class="line"></div>
    <p class="center gold english">Some memories never lose their beauty.</p>
    <p class="center heart">♥</p>
    <h2 class="center english">HAPPY BIRTHDAY</h2>
  </section>

  <footer class="footer">END OF TRANSMISSION • 2026</footer>
</main>

<script>
const levels = [
  {
    tag: "LEVEL 01 — THE BEGINNING",
    title: "البداية كانت من هنا",
    question: "لعبة بنبدأها من طيارة، وبننزل منها بالباراشوت على خريطة كبيرة، والهدف إنك تفضل آخر واحد واقف. اسم اللعبة إيه؟",
    answers: ["pubg", "بوبجي", "ببجي"]
  },
  {
    tag: "LEVEL 02 — THE SECRET WORD",
    title: "كلمة صغيرة... ومعنى كبير",
    question: "كلمة من 3 حروف، بنستخدمها كتير، وبقت جزء من قاموس خاص بين شخصين. إيه هي؟",
    answers: ["حلو"]
  },
  {
    tag: "LEVEL 03 — THE INSIDE JOKE",
    title: "رتّب الحروف",
    question: "الحروف دي مبعثرة... رتّبها عشان توصل لكلمة مش أي حد هيفهم معناها.",
    extra: "تلميح: كلمة خاصة جدًا بين أصحاب الحكاية.",
    scramble: "ل – ي – ك – ر – و – س – ب – ا",
    answers: ["ابسروكلي"]
  },
  {
    tag: "LEVEL 04 — THE FINAL CASE",
    title: "آخر لغز يا Detective...",
    question: "عندك 3 أدلة:<br><br>• البداية كانت مجرد لعبة.<br>• كلمة بسيطة بقت جزء من قاموس خاص.<br>• كلمة غريبة محدش هيفهم معناها غير أصحابها.<br><br>إيه الحاجة المشتركة بين التلاتة؟<br>حاجة مش لعبة، ولا كلمة، ولا شفرة... لكنها السبب إن الأدلة دي كلها بقت ليها معنى.",
    answers: ["الذكريات", "ذكريات"]
  }
];

let currentLevel = 0;

function show(id) {
  ["intro", "game", "codeScreen", "completed", "message"].forEach(x => {
    document.getElementById(x).classList.add("hidden");
  });
  document.getElementById(id).classList.remove("hidden");
}

function startGame() {
  show("game");
  loadLevel();
}

function normalize(value) {
  return value.trim()
    .toLowerCase()
    .replace(/\s+/g, "")
    .replace(/[أإآ]/g, "ا")
    .replace(/ى/g, "ي");
}

function loadLevel() {
  const level = levels[currentLevel];
  document.getElementById("levelTag").textContent = level.tag;
  document.getElementById("levelTitle").textContent = level.title;
  document.getElementById("question").innerHTML = level.question;

  const extra = document.getElementById("extra");
  extra.classList.toggle("hidden", !level.extra);
  extra.textContent = level.extra || "";

  const scramble = document.getElementById("scramble");
  scramble.classList.toggle("hidden", !level.scramble);
  scramble.textContent = level.scramble || "";

  document.getElementById("answer").value = "";
  document.getElementById("feedback").textContent = "";

  document.querySelectorAll(".dot").forEach((dot, i) => {
    dot.classList.toggle("done", i < currentLevel);
  });

  document.getElementById("answer").focus();
}

function checkAnswer() {
  const value = normalize(document.getElementById("answer").value);
  const correct = levels[currentLevel].answers.some(a => normalize(a) === value);
  const feedback = document.getElementById("feedback");

  if (!value) {
    feedback.textContent = "اكتب إجابتك الأول يا Detective.";
    return;
  }

  if (!correct) {
    feedback.textContent = "مش دي الإجابة... ركّز في الأدلة وحاول تاني.";
    return;
  }

  feedback.textContent = "إجابة صحيحة ✓";
  currentLevel++;

  setTimeout(() => {
    if (currentLevel < levels.length) {
      loadLevel();
    } else {
      show("codeScreen");
    }
  }, 900);
}

function checkCode() {
  const code = document.getElementById("secretCode").value.trim();
  const feedback = document.getElementById("codeFeedback");

  if (code === "483") {
    feedback.textContent = "ACCESS GRANTED ✓";
    setTimeout(() => show("completed"), 900);
  } else {
    feedback.textContent = "الكود مش صحيح... راجع الأدلة من البداية.";
  }
}

const finalMessage = [
  "يمكن تكون دي آخر مرحلة في اللعبة، بس الحقيقة إن في حاجات ملهاش نهاية، حتى لو الأيام أخدتها في طريق تاني.",
  "عايزة أقولك إنك من الأشخاص الجميلة والمميزة اللي قابلتهم في حياتي، وإنك شخص غالي عندي أكتر ما تتخيل.",
  "إنت شخص طيب أوي، وجدع، وحنين، وفيك تفاصيل كتير تخلي أي حد يعرفك يحمد ربنا إن في حياته شخص زيك. ويا بخت أي حد عنده حد بقلبك وبأصلك وبجمال روحك.",
  "يمكن اتخنقنا، ويمكن اختلفنا، ويمكن في وقت ما كل واحد فينا كمل طريقه بعيد عن التاني، بس ده عمره ما هيخليني أنكر إن كان بينا أيام وذكريات جميلة بجد.",
  "وهتفضل من الذكريات اللي بحب أرجعلها من وقت للتاني، وأبتسم، وأفصل بيها شوية عن دوشة الدنيا. ذكريات ليها مكانتها الخاصة، ومش محتاجة تتكرر عشان تفضل حلوة.",
  "مش كل شخص بنقابله بيكون مجرد مرحلة عابرة، في أشخاص بيسيبوا جوانا أثر حلو بيفضل معانا، وإنت من الناس دي.",
  "في يوم ميلادك، أتمنى لك من قلبي إن الحياة تكون حنينة عليك قد طيبة قلبك، وإنك تفضل ناجح ومبسوط ومحقق كل اللي نفسك فيه، وإنك تلاقي دايمًا ناس تقدّرك وتعرف قيمتك وتديك من الحنية والجدعنة اللي بتديهُم للي حواليك.",
  "كل سنة وإنت طيب، وكل سنة وإنت شخص جميل ومميز زي ما إنت.",
  "ويا بخت الدنيا بالناس اللي زيك. ❤️"
];

function openMessage() {
  show("message");
  const container = document.getElementById("messageText");
  container.innerHTML = "";

  finalMessage.forEach((line, index) => {
    const paragraph = document.createElement("p");
    paragraph.className = "message-line";
    paragraph.textContent = line;
    paragraph.style.animationDelay = (index * 1.5) + "s";
    container.appendChild(paragraph);
  });
}

document.getElementById("answer").addEventListener("keydown", e => {
  if (e.key === "Enter") checkAnswer();
});

document.getElementById("secretCode").addEventListener("keydown", e => {
  if (e.key === "Enter") checkCode();
});
</script>
</body>
</html>
