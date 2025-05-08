<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. – Special Individuals Profiles</title>
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

    .special-individual-container {
      margin-top: 30px;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
    }

    .special-individual-card {
      background-color: #1c1c1c;
      border-radius: 8px;
      padding: 20px;
      color: white;
      border-left: 5px solid crimson;
      box-shadow: 0px 0px 10px rgba(255, 0, 0, 0.3);
      transition: transform 0.3s ease-in-out;
    }

    .special-individual-card:hover {
      transform: translateY(-5px);
      box-shadow: 0px 10px 30px rgba(255, 0, 0, 0.6);
    }

    .special-individual-title {
      font-size: 1.5em;
      color: crimson;
      margin-bottom: 10px;
    }

    .special-individual-desc {
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
    <h1>🧬 Special Individuals Profiles</h1>

    <div class="special-individual-container">
      <!-- Special Individual: Dr. Connor -->
      <div class="special-individual-card">
        <div class="special-individual-title">
          Codename: Dr. Connor
        </div>
        <div class="special-individual-desc">
          <strong>Full Name:</strong> Dr. Connor <br>
          <strong>Clearance Level:</strong> D.I.V.I.D.E. <br>
          <strong>Assigned Division:</strong> LD-Anomaly Containment
        </div>

        <div class="quote">
          “I don’t want to understand it. I want to bury it so deep reality forgets it existed.”
        </div>

        <a href="dr_connor_profile.html" class="back-link">→ View Full Profile</a>
      </div>

      <!-- Add more special individuals here -->
      <div class="special-individual-card">
        <div class="special-individual-title">
          Codename: [Name/Designation]
        </div>
        <div class="special-individual-desc">
          <strong>Full Name:</strong> [Full Name]<br>
          <strong>Role:</strong> [Role in Organization]<br>
          <strong>Specialization:</strong> [Specialization]
        </div>

        <div class="quote">
          “[Famous quote or important line from the individual]”
        </div>

        <a href="[full_profile_link].html" class="back-link">→ View Full Profile</a>
      </div>

      <!-- Add more special individuals as needed -->
    </div>

    <a href="personal.html" class="back-link">← Back to Personnel</a>
  </div>
</body>
</html>
