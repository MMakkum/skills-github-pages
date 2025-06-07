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

  <h1>Scan the QR Code to Take a Selfie!</h1>

  <!-- Video Stream -->
  <video id="video" autoplay></video>

  <!-- Canvas to capture image -->
  <canvas id="canvas"></canvas>

  <!-- Capture Button -->
  <button id="captureButton">Capture Selfie</button>
  <br>
  <h2>Your Selfie:</h2>
  <img id="selfie" alt="Your Selfie" style="width: 100%; max-width: 300px;">

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
This code uses getUserMedia to access the camera and display the video stream.

When you press the "Capture Selfie" button, it takes a snapshot from the video stream and shows it as an image below the video.

You can modify the design and functionalities as needed. You’ll then upload this HTML page to a server or hosting service.

2. Generate the QR Code
Once your webpage is live and accessible via a URL, you can generate a QR code that links to that page.

How to Generate a QR Code:
Use any QR code generator (there are plenty online) to create a QR code. For example, you can use this QR code generator.

Simply input the URL of the page where you uploaded the selfie-taking HTML file.

3. Testing
Scan the QR code using a mobile device. It should take you to the webpage you created.

Allow camera access when prompted by the browser.

Capture the selfie and it will display on the page.

Things to Consider
Browser Support: Some older browsers may not support getUserMedia. Ensure that users are using up-to-date browsers.

Hosting: If you want this to be public, you’ll need to host your HTML file on a server (like GitHub Pages, Netlify, or any other web hosting service).

Privacy and Security: Make sure your users are aware that the QR code accesses their camera, and they should allow it in their browser.

If you have any questions on setting this up or need help with the hosting or QR code generation, feel free to ask!



Je zei:
Okay what do I put in Github to make a selfie, easy short

ChatGPT zei:
To quickly set up a selfie-taking page using GitHub Pages, you just need to create a simple repository, add the HTML code, and then deploy it. Here’s how to do it in a few simple steps:

1. Create a New Repository on GitHub
Go to GitHub and log in.

Click the "+" in the upper right and choose "New repository".

Name it something like selfie-qr.

Select Public and check "Initialize this repository with a README".

Click Create repository.

2. Upload the HTML File
Inside your newly created repo, click the "Add file" button, then select "Create new file".

Name the file index.html.

Copy and paste the following code into the file:

html
Kopiëren
Bewerken
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

  <h1>Scan the QR Code to Take a Selfie!</h1>

  <!-- Video Stream -->
  <video id="video" autoplay></video>

  <!-- Canvas to capture image -->
  <canvas id="canvas"></canvas>

  <!-- Capture Button -->
  <button id="captureButton">Capture Selfie</button>
  <br>
  <h2>Your Selfie:</h2>
  <img id="selfie" alt="Your Selfie" style="width: 100%; max-width: 300px;">

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
