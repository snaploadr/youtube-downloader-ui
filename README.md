# youtube-downloader-ui<!DOCTYPE html>
      # New website HTML: YouTube keyword, title, thumbnail & prompt generator (frontend-only / fake AI style)

html_ai_tool = """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>YT Video Idea Generator</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f5f7fb;
      display: flex;
      justify-content: center;
      padding: 30px;
      flex-direction: column;
      align-items: center;
    }
    h1 {
      color: #cc0000;
      font-size: 2rem;
      margin-bottom: 10px;
    }
    input, button {
      width: 100%;
      max-width: 400px;
      margin: 10px 0;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
    }
    button {
      background-color: #cc0000;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    button:hover {
      background-color: #a60000;
    }
    .results {
      background: white;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      margin-top: 20px;
      max-width: 500px;
      width: 100%;
    }
    .result-title {
      font-weight: bold;
      color: #444;
      margin-bottom: 5px;
    }
    .value {
      margin-bottom: 15px;
      color: #111;
    }
  </style>
</head>
<body>

  <h1>YT Idea Generator</h1>
  <input type="text" id="topicInput" placeholder="Enter a video topic (e.g. fitness, gaming, cooking)">
  <button onclick="generateIdeas()">Generate Ideas</button>

  <div class="results" id="resultBox" style="display:none;">
    <div>
      <div class="result-title">🔥 Video Title:</div>
      <div class="value" id="titleOut"></div>
    </div>
    <div>
      <div class="result-title">🔑 Suggested Keywords:</div>
      <div class="value" id="keywordsOut"></div>
    </div>
    <div>
      <div class="result-title">🧠 Video Prompt:</div>
      <div class="value" id="promptOut"></div>
    </div>
    <div>
      <div class="result-title">🖼️ Thumbnail Idea:</div>
      <div class="value" id="thumbOut"></div>
    </div>
  </div>

  <script>
    const data = {
      fitness: {
        title: "10-Min Home Workout That Burns Fat Fast",
        keywords: "home workout, fat burn, no equipment, fitness routine",
        prompt: "Create a high-energy 10-minute home workout for beginners using only bodyweight exercises.",
        thumbnail: "Split screen: before/after body, big bold '10 MINS ONLY'"
      },
      gaming: {
        title: "Top 5 Tricks to Win More in PUBG Mobile",
        keywords: "pubg tips, mobile gaming, battle royale, pro tricks",
        prompt: "Share your best hidden tips for winning solo or squad matches in PUBG Mobile.",
        thumbnail: "Player aiming + glowing loot + red arrows"
      },
      cooking: {
        title: "5 Easy Recipes You Can Cook in 15 Minutes",
        keywords: "easy recipes, cooking hacks, quick meals, home chef",
        prompt: "Show how to cook 5 tasty meals under 15 minutes using basic ingredients.",
        thumbnail: "Colorful dishes with bold text: '5 RECIPES - 15 MINS'"
      },
      tech: {
        title: "Top 3 Budget Smartphones in 2025 (Under $300)",
        keywords: "budget smartphones, tech review, mobile 2025, best phone",
        prompt: "Review and compare the best affordable smartphones with pros and cons.",
        thumbnail: "Phones lined up with rating stars and prices"
      }
    };

    function generateIdeas() {
      const input = document.getElementById('topicInput').value.toLowerCase();
      const topic = input.includes("game") ? "gaming" :
                    input.includes("cook") || input.includes("food") ? "cooking" :
                    input.includes("fit") || input.includes("gym") ? "fitness" :
                    input.includes("tech") || input.includes("phone") ? "tech" : null;

      if (!topic) {
        alert("Please enter a valid topic like fitness, gaming, cooking, or tech.");
        return;
      }

      document.getElementById("titleOut").textContent = data[topic].title;
      document.getElementById("keywordsOut").textContent = data[topic].keywords;
      document.getElementById("promptOut").textContent = data[topic].prompt;
      document.getElementById("thumbOut").textContent = data[topic].thumbnail;
      document.getElementById("resultBox").style.display = "block";
    }
  </script>

</body>
</html>
"""

# Save the new HTML to a file and zip it
project_dir = "/mnt/data/yt-ai-idea-generator"
os.makedirs(project_dir, exist_ok=True)
html_file = f"{project_dir}/index.html"

with open(html_file, "w") as f:
    f.write(html_ai_tool)

# Zip the folder
zip_output = "/mnt/data/yt-ai-idea-generator.zip"
with ZipFile(zip_output, "w") as zipf:
    zipf.write(html_file, arcname="index.html")

zip_output
