
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Timeline of Events</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background-color: #080808;
      color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace;
      min-height: 100vh;
    }

    .warning-bar {
      background-color: #8b0000;
      color: #fff;
      text-align: center;
      padding: 6px;
      font-size: 11px;
      letter-spacing: 3px;
      text-transform: uppercase;
      border-bottom: 1px solid #ff0000;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 40px 20px;
    }

    .back-link {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      color: #555;
      text-decoration: none;
      font-size: 11px;
      letter-spacing: 2px;
      margin-bottom: 20px;
      transition: color 0.2s;
    }
    .back-link:hover { color: #cc0000; }

    /* Header */
    .file-header {
      border: 1px solid #3a0000;
      padding: 30px;
      margin-bottom: 30px;
      position: relative;
      background: linear-gradient(180deg, #0f0000 0%, #080808 100%);
    }

    .file-header::before {
      content: '// CLASSIFIED RECORD //';
      position: absolute;
      top: -10px; left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #8b0000;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .file-header::after {
      content: '';
      position: absolute;
      top: 0; right: 0;
      width: 40px; height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .file-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 38px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(200,0,0,0.4);
      margin-bottom: 6px;
    }

    .file-designation {
      font-size: 11px;
      color: #555;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 16px;
    }

    .clearance-badge {
      display: inline-block;
      border: 1px solid #8b0000;
      color: #8b0000;
      font-size: 10px;
      letter-spacing: 3px;
      padding: 4px 12px;
      text-transform: uppercase;
    }

    /* Notice box */
    .notice-box {
      background: #0a0800;
      border: 1px solid #2a2000;
      border-left: 3px solid #ffd600;
      padding: 14px 18px;
      font-size: 11px;
      color: #776644;
      line-height: 1.7;
      margin-bottom: 30px;
      letter-spacing: 0.5px;
    }

    .notice-box strong { color: #ffd600; }

    /* Timeline */
    .timeline {
      position: relative;
      padding-left: 0;
    }

    /* Vertical line */
    .timeline::before {
      content: '';
      position: absolute;
      left: 110px;
      top: 0;
      bottom: 0;
      width: 1px;
      background: linear-gradient(180deg, #3a0000, #1a0000 80%, transparent);
    }

    .timeline-entry {
      display: flex;
      gap: 0;
      margin-bottom: 0;
      position: relative;
    }

    /* Year column */
    .year-col {
      width: 110px;
      flex-shrink: 0;
      padding-top: 22px;
      padding-right: 20px;
      text-align: right;
    }

    .year-label {
      font-family: 'Rajdhani', sans-serif;
      font-size: 20px;
      font-weight: 700;
      letter-spacing: 2px;
      line-height: 1;
    }

    /* Node on the line */
    .timeline-node {
      flex-shrink: 0;
      width: 0;
      position: relative;
      margin-top: 24px;
    }

    .timeline-node::before {
      content: '';
      position: absolute;
      left: -5px;
      top: 4px;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      border: 2px solid;
      background: #080808;
    }

    /* Content column */
    .entry-content {
      flex: 1;
      padding: 16px 0 30px 28px;
      border-left: none;
    }

    .entry-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 17px;
      font-weight: 700;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 10px;
      line-height: 1.3;
    }

    .entry-body {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid;
      padding: 14px 16px;
      font-size: 12px;
      line-height: 1.9;
      color: #777;
    }

    /* Year-specific colors */
    .entry-2005 .year-label { color: #4fc3f7; }
    .entry-2005 .timeline-node::before { border-color: #4fc3f7; }
    .entry-2005 .entry-title { color: #4fc3f7; }
    .entry-2005 .entry-body { border-left-color: #1a4a6a; }

    .entry-2022 .year-label { color: #4caf50; }
    .entry-2022 .timeline-node::before { border-color: #4caf50; }
    .entry-2022 .entry-title { color: #4caf50; }
    .entry-2022 .entry-body { border-left-color: #1a4a1a; }

    .entry-2023 .year-label { color: #ffd600; }
    .entry-2023 .timeline-node::before { border-color: #ffd600; }
    .entry-2023 .entry-title { color: #ffd600; }
    .entry-2023 .entry-body { border-left-color: #4a4000; }

    .entry-2025 .year-label { color: #f44336; }
    .entry-2025 .timeline-node::before { border-color: #f44336; box-shadow: 0 0 8px rgba(244,67,54,0.4); }
    .entry-2025 .entry-title { color: #f44336; }
    .entry-2025 .entry-body { border-left-color: #4a0000; }

    .entry-unknown .year-label { color: #555; font-size: 14px; letter-spacing: 1px; }
    .entry-unknown .timeline-node::before { border-color: #333; border-style: dashed; }
    .entry-unknown .entry-title { color: #444; }
    .entry-unknown .entry-body { border-left-color: #222; color: #444; font-style: italic; }

    /* Pulse badges on entries */
    .entry-tag {
      display: inline-block;
      font-size: 9px;
      letter-spacing: 2px;
      padding: 2px 8px;
      border: 1px solid;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-right: 6px;
    }

    .tag-blue { color: #4fc3f7; border-color: #1a4a6a; }
    .tag-green { color: #4caf50; border-color: #1a4a1a; }
    .tag-yellow { color: #ffd600; border-color: #4a4000; }
    .tag-red { color: #f44336; border-color: #4a0000; }
    .tag-gray { color: #444; border-color: #222; }

    /* Ongoing pulse indicator */
    .ongoing {
      display: flex;
      align-items: center;
      gap: 10px;
      margin-top: 12px;
      font-size: 10px;
      color: #444;
      letter-spacing: 2px;
    }

    .ongoing-dot {
      width: 6px; height: 6px;
      background: #cc0000;
      border-radius: 50%;
      animation: pulse 1.5s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.3; transform: scale(0.8); }
    }

    /* More to come */
    .more-entry {
      display: flex;
      gap: 0;
      position: relative;
      margin-top: 10px;
    }

    .more-col {
      width: 110px;
      flex-shrink: 0;
      padding-top: 14px;
      padding-right: 20px;
      text-align: right;
    }

    .more-dots {
      font-size: 20px;
      color: #333;
      letter-spacing: 2px;
    }

    .more-node {
      flex-shrink: 0;
      width: 0;
      position: relative;
      margin-top: 14px;
    }

    .more-node::before {
      content: '';
      position: absolute;
      left: -4px;
      top: 4px;
      width: 8px;
      height: 8px;
      border: 1px dashed #333;
      border-radius: 50%;
    }

    .more-content {
      flex: 1;
      padding: 10px 0 20px 28px;
      font-size: 11px;
      color: #333;
      letter-spacing: 2px;
      padding-top: 14px;
      font-style: italic;
    }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
      margin-top: 30px;
      font-size: 10px;
      color: #333;
      letter-spacing: 1px;
      line-height: 1.8;
      text-align: center;
    }
  </style>
</head>
<body>

  <div class="warning-bar">
    ⚠ RESTRICTED ACCESS — AUTHORIZED PERSONNEL ONLY — D.I.V.I.D.E. INTERNAL DATABASE ⚠
  </div>

  <div class="container">

    <a href="index.html" class="back-link">← RETURN TO DATABASE INDEX</a>

    <div class="file-header">
      <div class="file-title">TIMELINE OF EVENTS</div>
      <div class="file-designation">Chronological Record — D.I.V.I.D.E. Universe — Ongoing</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <div class="notice-box">
      <strong>NOTE:</strong> All anomalies have existed only since 2005. Any entity claiming origin before this date must be considered dimensional in nature. Current understanding of pre-2005 anomalous phenomena remains insufficient for classification. This record is updated as new data is collected and verified.
    </div>

    <div class="timeline">

      <!-- 2005 -->
      <div class="timeline-entry entry-2005">
        <div class="year-col">
          <div class="year-label">2005</div>
        </div>
        <div class="timeline-node"></div>
        <div class="entry-content">
          <div class="entry-tag tag-blue">Origin Event</div>
          <div class="entry-tag tag-blue">Foundation Established</div>
          <div class="entry-title">The First Anomaly Was Recorded</div>
          <div class="entry-body">
            The first anomaly was discovered in 2005, leading directly to the establishment of D.I.V.I.D.E. This marked the beginning of an unprecedented series of events that would permanently shape the future of humanity. All documented anomalies trace their existence to this year or later. Any entity claiming prior origin is considered dimensional in nature — originating from a reality separate from our own.
          </div>
        </div>
      </div>

      <!-- 2022 -->
      <div class="timeline-entry entry-2022">
        <div class="year-col">
          <div class="year-label">2022</div>
        </div>
        <div class="timeline-node"></div>
        <div class="entry-content">
          <div class="entry-tag tag-green">First Sighting</div>
          <div class="entry-tag tag-green">LD-002</div>
          <div class="entry-title">The Doro Entity Was First Sighted</div>
          <div class="entry-body">
            In 2022, the first documented sighting of the entity designated LD-002 — referred to internally as "Doro" — was reported. This event marked the emergence of an unsettling force that would become a cornerstone of D.I.V.I.D.E.'s ongoing research. The full scope of the entity's nature and capabilities remains classified above standard clearance levels.
          </div>
        </div>
      </div>

      <!-- 2023 -->
      <div class="timeline-entry entry-2023">
        <div class="year-col">
          <div class="year-label">2023</div>
        </div>
        <div class="timeline-node"></div>
        <div class="entry-content">
          <div class="entry-tag tag-yellow">Reality Distortion</div>
          <div class="entry-tag tag-yellow">Escalation</div>
          <div class="entry-title">Glitches Begin to Appear in the Timeline</div>
          <div class="entry-body">
            As reality itself began to warp, anomaly frequency increased significantly. Glitches in the fabric of time and space became noticeable across multiple monitored regions. LD-002 sightings escalated, causing widespread confusion and fear in affected zones. D.I.V.I.D.E. response teams were placed on elevated alert status for the duration of this period.
          </div>
        </div>
      </div>

      <!-- 2025 -->
      <div class="timeline-entry entry-2025">
        <div class="year-col">
          <div class="year-label">2025</div>
        </div>
        <div class="timeline-node"></div>
        <div class="entry-content">
          <div class="entry-tag tag-red">Critical Event</div>
          <div class="entry-tag tag-red">LD-001 Correlation</div>
          <div class="entry-title">The D.I.V.I.D.E. Incident Escalates</div>
          <div class="entry-body">
            A surge in anomalous activity spread across the solar system. Reports of strange and dangerous phenomena increased exponentially across all monitored sectors. This escalation appears to correlate directly with ongoing research and developments surrounding LD-001. The connection between LD-001's activity and the wider anomalous surge remains under active investigation.
            <div class="ongoing">
              <div class="ongoing-dot"></div>
              SITUATION ONGOING — DATA COLLECTION ACTIVE
            </div>
          </div>
        </div>
      </div>

      <!-- More to come -->
      <div class="more-entry">
        <div class="more-col">
          <div class="more-dots">···</div>
        </div>
        <div class="more-node"></div>
        <div class="more-content">// More to come as data is collected and verified //</div>
      </div>

    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

</body>
</html>
