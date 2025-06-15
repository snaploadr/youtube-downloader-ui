# youtube-downloader-ui<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>YouTube Video Downloader</title>
  <style>
    body {
      background: #f7f7f7;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
    }
    h1 {
      color: #e62117;
      margin-bottom: 20px;
    }
    input {
      padding: 10px;
      width: 320px;
      font-size: 1rem;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    button {
      margin-top: 10px;
      padding: 10px 20px;
      font-size: 1rem;
      color: white;
      background-color: #e62117;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background-color: #c31412;
    }
    .note {
      margin-top: 20px;
      font-size: 0.9rem;
      color: #777;
      max-width: 300px;
      text-align: center;
    }
  </style>
</head>
<body>
  <h1>YouTube Downloader</h1>
  <input type="text" id="yturl" placeholder="Paste YouTube link here" />
  <button onclick="download()">Download</button>
  <div class="note">
    This tool redirects to a third-party site.<br>We do not host or download any content.
  </div>

  <script>
    function download() {
      const url = document.getElementById("yturl").value.trim();
      if (!url || !(url.includes("youtube.com") || url.includes("youtu.be"))) {
        alert("❌ Please enter a valid YouTube video URL.");
        return;
      }
      const encoded = encodeURIComponent(url);
      // Change this to whichever 3rd-party site you prefer
      window.location.href = `https://yt1s.ltd/?url=${encoded}`;
    }
  </script>
</body>
</html>
