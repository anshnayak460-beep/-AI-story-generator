# -AI-story-generator

<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>StoryAI - AI Story Generator</title>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background: #0b1020;
  color: #f5f5ff;
  min-height: 100vh;
}

header {
  padding: 22px 7%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #252b43;
  background: #10162a;
}

.logo {
  font-size: 25px;
  font-weight: bold;
  color: #a78bfa;
}

.logo span {
  color: white;
}

.tag {
  color: #b9bfd3;
  font-size: 13px;
}

.container {
  max-width: 1100px;
  margin: 40px auto;
  padding: 20px;
}

.hero {
  text-align: center;
  margin-bottom: 35px;
}

.hero h1 {
  font-size: clamp(30px, 5vw, 48px);
  margin-bottom: 15px;
}

.hero h1 span {
  color: #a78bfa;
}

.hero p {
  color: #aeb5ca;
  line-height: 1.7;
}

.layout {
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 22px;
}

.panel {
  background: #151c31;
  border: 1px solid #29324c;
  border-radius: 18px;
  padding: 24px;
}

.panel h2 {
  font-size: 20px;
  margin-bottom: 22px;
}

label {
  display: block;
  margin: 17px 0 9px;
  font-size: 14px;
  color: #e1e5f5;
}

input, select, textarea {
  width: 100%;
  padding: 13px;
  color: white;
  background: #0c1223;
  border: 1px solid #343d59;
  border-radius: 9px;
  font-size: 14px;
  outline: none;
}

input:focus, select:focus, textarea:focus {
  border-color: #a78bfa;
}

select option {
  background: #151c31;
}

textarea {
  min-height: 95px;
  resize: vertical;
}

button {
  border: none;
  cursor: pointer;
  font-size: 14px;
  font-weight: bold;
  border-radius: 10px;
  padding: 13px 16px;
  transition: 0.2s;
}

button:hover {
  transform: translateY(-1px);
  opacity: 0.9;
}

.generate {
  margin-top: 22px;
  width: 100%;
  color: #fff;
  background: linear-gradient(135deg, #7c3aed, #a855f7);
  font-size: 16px;
  padding: 16px;
}

.generate:disabled {
  opacity: 0.6;
  cursor: wait;
}

.note {
  color: #9ca8c3;
  font-size: 12px;
  line-height: 1.6;
  margin-top: 12px;
}

.story-panel {
  min-height: 500px;
}

.story-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
  margin-bottom: 20px;
}

.story-top h2 {
  margin: 0;
}

.actions {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.secondary {
  background: #252e49;
  color: white;
  border: 1px solid #394461;
}

.story {
  color: #e1e5f3;
  line-height: 1.95;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
  font-size: 15px;
}

.story.empty {
  min-height: 340px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: #9ca8c3;
  white-space: normal;
}

.story.empty .big {
  font-size: 55px;
  margin-bottom: 15px;
}

.status {
  color: #c4b5fd;
  margin-bottom: 15px;
  font-size: 13px;
}

footer {
  text-align: center;
  color: #8d97b2;
  padding: 25px;
  font-size: 13px;
}

@media(max-width: 760px) {
  .layout {
    grid-template-columns: 1fr;
  }

  header {
    padding: 18px 5%;
  }

  .tag {
    display: none;
  }

  .container {
    margin: 20px auto;
    padding: 14px;
  }

  .panel {
    padding: 19px;
  }
}
</style>
</head>

<body>

<header>
  <div class="logo">✦ Story<span>AI</span></div>
  <div class="tag">Your imagination, powered by AI</div>
</header>

<main class="container">

  <section class="hero">
    <h1>अपनी अगली कहानी <span>बनाओ ✨</span></h1>
    <p>अपना विचार लिखो और AI की मदद से एक नई, मजेदार कहानी तैयार करो।<br>
    तुम्हारी कल्पना ही तुम्हारी कहानी की शुरुआत है!</p>
  </section>

  <section class="layout">

    <div class="panel">
      <h2>🎨 कहानी बनाओ</h2>

      <form id="storyForm">
        <label for="topic">कहानी किस विषय पर हो?</label>
        <textarea id="topic" placeholder="जैसे: एक गरीब बच्चा जो वैज्ञानिक बनना चाहता है..." required></textarea>

        <label for="genre">कहानी की शैली</label>
        <select id="genre">
          <option>रोमांचक (Adventure)</option>
          <option>डरावनी (Horror)</option>
          <option>जादुई (Fantasy)</option>
          <option>राजा-रानी (Fairy Tale)</option>
          <option>कॉमेडी (Comedy)</option>
          <option>प्रेरणादायक (Motivational)</option>
          <option>विज्ञान कथा (Science Fiction)</option>
          <option>रहस्य (Mystery)</option>
          <option>बच्चों की कहानी (Children)</option>
        </select>

        <label for="language">कहानी की भाषा</label>
        <select id="language">
          <option value="Hindi">हिंदी</option>
          <option value="English">English</option>
          <option value="Hinglish">Hinglish</option>
        </select>

        <label for="length">कहानी कितनी लंबी हो?</label>
        <select id="length">
          <option value="short">छोटी (लगभग 300 शब्द)</option>
          <option value="medium" selected>मध्यम (लगभग 600 शब्द)</option>
          <option value="long">लंबी (लगभग 1000 शब्द)</option>
        </select>

        <label for="audience">किसके लिए कहानी है?</label>
        <select id="audience">
          <option>बच्चों के लिए</option>
          <option>विद्यार्थियों के लिए</option>
          <option>सभी उम्र के लोगों के लिए</option>
        </select>

        <label for="apiKey">Groq API Key</label>
        <input type="password" id="apiKey" placeholder="अपनी Groq API key डालें" autocomplete="off">

        <label for="model">AI Model</label>
        <input id="model" value="llama-3.3-70b-versatile" placeholder="Groq model ID">

        <button class="generate" id="generateBtn" type="submit">
          ✨ AI से कहानी बनाओ
        </button>

        <p class="note">
          API key अपने कंप्यूटर पर ही डालें। इसे किसी के साथ साझा न करें
          और इस फाइल को API key के साथ सार्वजनिक वेबसाइट पर अपलोड न करें।
        </p>
      </form>
    </div>

    <div class="panel story-panel">
      <div class="story-top">
        <h2>📖 तुम्हारी कहानी</h2>
        <div class="actions">
          <button class="secondary" id="copyBtn" type="button">📋 कॉपी</button>
          <button class="secondary" id="downloadBtn" type="button">⬇ डाउनलोड</button>
        </div>
      </div>

      <div id="status" class="status" role="status" aria-live="polite"></div>

      <div id="story" class="story empty">
        <div>
          <div class="big">📚</div>
          <h3>तुम्हारी कहानी यहाँ दिखाई देगी</h3>
          <p style="margin-top:10px">
            विषय लिखो, अपनी पसंद चुनो और AI से कहानी बनवाओ।
          </p>
        </div>
      </div>
    </div>

  </section>
</main>

<footer>Made with ✨ StoryAI · Let your imagination fly</footer>

<script>
const form = document.getElementById("storyForm");
const topicInput = document.getElementById("topic");
const apiKeyInput = document.getElementById("apiKey");
const modelInput = document.getElementById("model");
const storyBox = document.getElementById("story");
const statusBox = document.getElementById("status");
const generateBtn = document.getElementById("generateBtn");

let currentStory = "";
let currentTitle = "my-ai-story";

form.addEventListener("submit", async function(event) {
  event.preventDefault();

  const topic = topicInput.value.trim();
  const apiKey = apiKeyInput.value.trim();
  const genre = document.getElementById("genre").value;
  const language = document.getElementById("language").value;
  const length = document.getElementById("length").value;
  const audience = document.getElementById("audience").value;
  const model = modelInput.value.trim();

  if (!topic) {
    alert("कृपया कहानी का विषय लिखें।");
    return;
  }

  if (!apiKey) {
    alert("पहले अपनी Groq API key डालें।");
    apiKeyInput.focus();
    return;
  }

  if (!model) {
    alert("कृपया AI model का नाम लिखें।");
    return;
  }

  const wordCount = {
    short: "लगभग 300 शब्द",
    medium: "लगभग 600 शब्द",
    long: "लगभग 1000 शब्द"
  }[length];

  const prompt = `
तुम एक रचनात्मक कहानीकार हो।
नीचे दिए गए निर्देशों के अनुसार एक मौलिक कहानी लिखो।

विषय: ${topic}
शैली: ${genre}
भाषा: ${language}
पाठक: ${audience}
लंबाई: ${wordCount}

निर्देश:
1. कहानी के लिए एक आकर्षक शीर्षक दो।
2. शुरुआत दिलचस्प हो।
3. कहानी में पात्र, घटनाएँ और उचित अंत हो।
4. कहानी स्वाभाविक, रोचक और मौलिक हो।
5. कहानी के अलावा अनावश्यक बातचीत न लिखो।
6. बच्चों के लिए कहानी हो तो भाषा सरल और उचित रखो।
`;

  generateBtn.disabled = true;
  generateBtn.textContent = "⏳ कहानी बन रही है...";
  statusBox.textContent = "AI तुम्हारे विचार को कहानी में बदल रहा है...";
  storyBox.className = "story";
  storyBox.textContent = "कृपया प्रतीक्षा करें...";

  try {
    const response = await fetch(
      "https://api.groq.com/openai/v1/chat/completions",
      {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "Authorization": "Bearer " + apiKey
        },
        body: JSON.stringify({
          model: model,
          messages: [
            {
              role: "system",
              content: "You are a creative story writer. Follow the user's language and story instructions."
            },
            {
              role: "user",
              content: prompt
            }
          ],
          temperature: 0.85,
          max_tokens: length === "long" ? 3000 : length === "medium" ? 1800 : 1000
        })
      }
    );

    const data = await response.json();

    if (!response.ok) {
      throw new Error(
        data.error?.message || "API request failed: " + response.status
      );
    }

    const result = data.choices?.[0]?.message?.content;

    if (!result) {
      throw new Error("AI से कहानी नहीं मिली। दोबारा कोशिश करें।");
    }

    currentStory = result.trim();

    const firstLine = currentStory.split("\n").find(line => line.trim());
    currentTitle = (firstLine || "my-ai-story")
      .replace(/^#+\s*/, "")
      .replace(/[^\p{L}\p{N}\s-]/gu, "")
      .trim()
      .replace(/\s+/g, "-")
      .slice(0, 60) || "my-ai-story";

    storyBox.textContent = currentStory;
    statusBox.textContent = "✅ तुम्हारी कहानी तैयार है!";
  } catch (error) {
    currentStory = "";
    storyBox.textContent = "कहानी नहीं बन सकी। नीचे दिए गए सुझाव देखें।";
    statusBox.textContent = "❌ " + error.message;

    alert(
      "कहानी बनाने में समस्या हुई:\n\n" +
      error.message +
      "\n\nAPI key, model name और इंटरनेट कनेक्शन जाँचें।"
    );
  } finally {
    generateBtn.disabled = false;
    generateBtn.textContent = "✨ AI से कहानी बनाओ";
  }
});

document.getElementById("copyBtn").addEventListener("click", async function() {
  if (!currentStory) {
    alert("पहले कोई कहानी बनाओ।");
    return;
  }

  try {
    await navigator.clipboard.writeText(currentStory);
    statusBox.textContent = "✅ कहानी कॉपी हो गई!";
  } catch {
    alert("कॉपी नहीं हो पाई। कहानी को माउस से चुनकर कॉपी करें।");
  }
});

document.getElementById("downloadBtn").addEventListener("click", function() {
  if (!currentStory) {
    alert("पहले कोई कहानी बनाओ।");
    return;
  }

  const blob = new Blob(["\uFEFF" + currentStory], {
    type: "text/plain;charset=utf-8"
  });

  const url = URL.createObjectURL(blob);
  const link = document.createElement("a");

  link.href = url;
  link.download = currentTitle + ".txt";
  document.body.appendChild(link);
  link.click();
  link.remove();

  URL.revokeObjectURL(url);
  statusBox.textContent = "✅ कहानी डाउनलोड हो गई!";
});
</script>

</body>
</html>
