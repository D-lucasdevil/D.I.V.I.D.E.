<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. – Task Force Profiles</title>
  <style>
    body {
      background-color: #111;
      color: white;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 950px;
      margin: auto;
      padding: 40px 20px;
    }

    h1, h2 {
      color: crimson;
      margin-bottom: 10px;
    }

    .task-force-container {
      margin-top: 30px;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
    }

    .task-force-card {
      background-color: #1c1c1c;
      border-radius: 8px;
      padding: 20px;
      color: white;
      border-left: 5px solid crimson;
      box-shadow: 0px 0px 10px rgba(255, 0, 0, 0.3);
      transition: transform 0.3s ease-in-out;
    }

    .task-force-card:hover {
      transform: translateY(-5px);
      box-shadow: 0px 10px 30px rgba(255, 0, 0, 0.6);
    }

    .task-force-title {
      font-size: 1.5em;
      color: crimson;
      margin-bottom: 10px;
    }

    .task-force-desc {
      font-size: 1.1em;
      color: #aaa;
    }

    .quote {
      color: #ccc;
      background-color: #1b1b1b;
      border-left: 4px solid #666;
      padding: 12px 18px;
      border-radius: 5px;
      margin-top: 20px;
      font-style: italic;
    }

    a.back-link {
      display: block;
      margin-top: 50px;
      text-align: center;
      color: crimson;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>⚔ Task Force Profiles</h1>

    <div class="task-force-container">
      <!-- Task Force: APA -->
      <div class="task-force-card">
        <div class="task-force-title">
          Codename: A.P.A.
        </div>
        <div class="task-force-desc">
          <strong>Full Name:</strong> Anomaly Pursuit Agent <br>
          <strong>Alternate Meaning (Classified):</strong> Adaptive Protocol Apex
        </div>

        <div class="quote">
          “We don’t send APA to clean up the mess. We send them to end it.”
        </div>

        <a href="apa.html" class="back-link">→ View Full Profile</a>
      </div>

      <!-- Add more task forces here -->
      <div class="task-force-card">
        <div class="task-force-title">
          Codename: ECHO-9
        </div>
        <div class="task-force-desc">
          <strong>Full Name:</strong> Echo Unit-9 <br>
          <strong>Mission Focus:</strong> Reconnaissance and Strategic Field Support
        </div>

        <div class="quote">
          “Silence is our weapon. When we strike, no one survives the echo.”
        </div>

        <a href="echo9.html" class="back-link">→ View Full Profile</a>
      </div>

      <!-- Add more task force entries here as needed -->
      
    </div>

    <a href="personal.html" class="back-link">← Back to Personnel</a>
  </div>
</body>
</html>
