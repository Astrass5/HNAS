<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vimeo Video Embedder</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 20px;
    }
    #video-container {
      margin-top: 20px;
    }
    iframe {
      width: 80%;
      height: 400px;
      border: none;
    }
  </style>
</head>
<body>
  <h1>Vimeo Video Embedder</h1>
  <input type="text" id="vimeo-url" placeholder="Paste Vimeo video URL here" style="width: 60%;">
  <button onclick="embedVideo()">Play Video</button>
  <div id="video-container"></div>

  <script>
    function embedVideo() {
      const urlInput = document.getElementById('vimeo-url').value;
      const videoContainer = document.getElementById('video-container');
      const vimeoID = extractVimeoID(urlInput);

      if (vimeoID) {
        videoContainer.innerHTML = `<iframe src="https://player.vimeo.com/video/${vimeoID}" allow="autoplay; fullscreen" allowfullscreen></iframe>`;
      } else {
        alert("Invalid Vimeo URL. Please try again.");
      }
    }

    function extractVimeoID(url) {
      const regex = /vimeo\.com\/(?:.*#|.*/videos/)?([0-9]+)/;
      const match = url.match(regex);
      return match ? match[1] : null;
    }
  </script>
</body>
</html>
