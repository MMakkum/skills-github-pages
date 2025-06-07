<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Take a Selfie</title>
  <style>
    body { text-align: center; margin: 0; padding: 0; }
    video { width: 100%; height: auto; }
    canvas { display: none; }
    button { padding: 10px 20px; font-size: 16px; }
  </style>
</head>
<body>

  <h1>Scan the QR Code to receive the money</h1>

  <!-- Video Stream -->
  <video id="video" autoplay></video>

  <!-- Canvas to capture image -->
  <canvas id="canvas"></canvas>

  <!-- Capture Button -->
  <button id="captureButton">Capture money</button>
  <br>
  <h2>Your money:</h2>
  <img id="selfie" alt="Your money" style="width: 100%; max-width: 300px;">

  <script>
    const video = document.getElementById('video');
    const canvas = document.getElementById('canvas');
    const selfieImage = document.getElementById('selfie');
    const captureButton = document.getElementById('captureButton');

    // Access the camera
    navigator.mediaDevices.getUserMedia({ video: true })
      .then(stream => {
        video.srcObject = stream;
      })
      .catch(err => {
        alert("Camera access denied or unavailable.");
      });

    // Capture the selfie
    captureButton.addEventListener('click', () => {
      const context = canvas.getContext('2d');
      const width = video.videoWidth;
      const height = video.videoHeight;

      canvas.width = width;
      canvas.height = height;

      context.drawImage(video, 0, 0, width, height);
      selfieImage.src = canvas.toDataURL('image/png');  // Show the captured image
    });
  </script>

</body>
</html>
