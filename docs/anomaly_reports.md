
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Anomaly Reports</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;600;700&display=swap');

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

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

    .header {
      border: 1px solid #3a0000;
      padding: 30px;
      margin-bottom: 30px;
      position: relative;
      background: linear-gradient(180deg, #0f0000 0%, #080808 100%);
    }

    .header::before {
      content: '// CLASSIFIED //';
      position: absolute;
      top: -10px;
      left: 20px;
      background: #080808;
      padding: 0 10px;
      color: #8b0000;
      font-size: 11px;
      letter-spacing: 3px;
    }

    .header::after {
      content: '';
      position: absolute;
      top: 0;
      right: 0;
      width: 40px;
      height: 40px;
      border-top: 2px solid #8b0000;
      border-right: 2px solid #8b0000;
    }

    .site-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 36px;
      font-weight: 700;
      color: #cc0000;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(200, 0, 0, 0.4);
      margin-bottom: 6px;
    }

    .site-subtitle {
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

    .back-link:hover {
      color: #cc0000;
    }

    .status-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 16px;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      margin-bottom: 30px;
      font-size: 10px;
      color: #444;
      letter-spacing: 1px;
    }

    .status-dot {
      display: inline-block;
      width: 6px;
      height: 6px;
      background: #cc0000;
      border-radius: 50%;
      margin-right: 6px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #8b0000;
      text-transform: uppercase;
      margin-bottom: 12px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    /* Search bar */
    .search-bar {
      width: 100%;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      border-left: 3px solid #8b0000;
      color: #c0c0c0;
      font-family: 'Share Tech Mono', monospace;
      font-size: 13px;
      padding: 10px 14px;
      margin-bottom: 20px;
      outline: none;
      letter-spacing: 1px;
    }

    .search-bar::placeholder {
      color: #333;
    }

    .search-bar:focus {
      border-color: #cc0000;
    }

    /* Anomaly grid */
    .anomaly-grid {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 6px;
      margin-bottom: 30px;
    }

    @media (max-width: 600px) {
      .anomaly-grid {
        grid-template-columns: 1fr 1fr;
      }
    }

    .anomaly-link {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 10px 14px;
      background-color: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a0000;
      color: #888;
      text-decoration: none;
      font-size: 12px;
      letter-spacing: 1px;
      transition: all 0.15s ease;
      position: relative;
      overflow: hidden;
    }

    .anomaly-link.redacted {
      border-left-color: #8b0000;
      color: #cc0000;
    }

    .anomaly-link:hover {
      border-left-color: #cc0000;
      color: #fff;
      border-color: #3a0000;
      background: #110000;
    }

    .anomaly-link .link-icon {
      font-size: 9px;
      color: #2a0000;
      transition: color 0.15s;
    }

    .anomaly-link:hover .link-icon {
      color: #8b0000;
    }

    /* Count badge */
    .count-badge {
      display: inline-block;
      background: #1a0000;
      border: 1px solid #3a0000;
      color: #8b0000;
      font-size: 10px;
      padding: 2px 8px;
      margin-left: 10px;
      letter-spacing: 1px;
    }

    .footer {
      border-top: 1px solid #1a0000;
      padding-top: 20px;
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

    <div class="header">
      <div class="site-title">ANOMALY REPORTS</div>
      <div class="site-subtitle">Liminal Division — Active Case Files</div>
      <div class="clearance-badge">Clearance Level 1+ Required</div>
    </div>

    <div class="status-bar">
      <span><span class="status-dot"></span>DATABASE ONLINE</span>
      <span>TOTAL DOCUMENTED ANOMALIES: 96 <span class="count-badge">+REDACTED</span></span>
      <span>LAST UPDATED: [CLASSIFIED]</span>
    </div>

    <input class="search-bar" type="text" placeholder="// SEARCH ANOMALY FILES..." id="searchInput" onkeyup="filterAnomalies()" />

    <div class="section-label">// Active Case Files — LD Series //</div>

    <div class="anomaly-grid" id="anomalyGrid">
      <a href="LD-000.html" class="anomaly-link redacted"><span class="link-icon">▶</span> LD-000 — [REDACTED]</a>
      <a href="LD-001.html" class="anomaly-link"><span class="link-icon">▶</span> LD-001</a>
      <a href="LD-002.html" class="anomaly-link"><span class="link-icon">▶</span> LD-002</a>
      <a href="LD-003.html" class="anomaly-link"><span class="link-icon">▶</span> LD-003</a>
      <a href="LD-004.html" class="anomaly-link"><span class="link-icon">▶</span> LD-004</a>
      <a href="LD-005.html" class="anomaly-link"><span class="link-icon">▶</span> LD-005</a>
      <a href="LD-006.html" class="anomaly-link"><span class="link-icon">▶</span> LD-006</a>
      <a href="LD-007.html" class="anomaly-link"><span class="link-icon">▶</span> LD-007</a>
      <a href="LD-008.html" class="anomaly-link"><span class="link-icon">▶</span> LD-008</a>
      <a href="LD-009.html" class="anomaly-link"><span class="link-icon">▶</span> LD-009</a>
      <a href="LD-009.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-009.5</a>
      <a href="LD-010.html" class="anomaly-link"><span class="link-icon">▶</span> LD-010</a>
      <a href="LD-011.html" class="anomaly-link"><span class="link-icon">▶</span> LD-011</a>
      <a href="LD-012.html" class="anomaly-link"><span class="link-icon">▶</span> LD-012</a>
      <a href="LD-013.html" class="anomaly-link"><span class="link-icon">▶</span> LD-013</a>
      <a href="LD-014.html" class="anomaly-link"><span class="link-icon">▶</span> LD-014</a>
      <a href="LD-015.html" class="anomaly-link"><span class="link-icon">▶</span> LD-015</a>
      <a href="LD-016.html" class="anomaly-link"><span class="link-icon">▶</span> LD-016</a>
      <a href="LD-017.html" class="anomaly-link"><span class="link-icon">▶</span> LD-017</a>
      <a href="LD-018.html" class="anomaly-link"><span class="link-icon">▶</span> LD-018</a>
      <a href="LD-019.html" class="anomaly-link"><span class="link-icon">▶</span> LD-019</a>
      <a href="LD-020.html" class="anomaly-link"><span class="link-icon">▶</span> LD-020</a>
      <a href="LD-021.html" class="anomaly-link"><span class="link-icon">▶</span> LD-021</a>
      <a href="LD-021.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-021.5</a>
      <a href="LD-022.html" class="anomaly-link"><span class="link-icon">▶</span> LD-022</a>
      <a href="LD-023.html" class="anomaly-link"><span class="link-icon">▶</span> LD-023</a>
      <a href="LD-023.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-023.5</a>
      <a href="LD-024.html" class="anomaly-link"><span class="link-icon">▶</span> LD-024</a>
      <a href="LD-025.html" class="anomaly-link"><span class="link-icon">▶</span> LD-025</a>
      <a href="LD-026.html" class="anomaly-link"><span class="link-icon">▶</span> LD-026</a>
      <a href="LD-027.html" class="anomaly-link"><span class="link-icon">▶</span> LD-027</a>
      <a href="LD-028.html" class="anomaly-link"><span class="link-icon">▶</span> LD-028</a>
      <a href="LD-029.html" class="anomaly-link"><span class="link-icon">▶</span> LD-029</a>
      <a href="LD-030.html" class="anomaly-link"><span class="link-icon">▶</span> LD-030</a>
      <a href="LD-031.html" class="anomaly-link"><span class="link-icon">▶</span> LD-031</a>
      <a href="LD-032.html" class="anomaly-link"><span class="link-icon">▶</span> LD-032</a>
      <a href="LD-033.html" class="anomaly-link"><span class="link-icon">▶</span> LD-033</a>
      <a href="LD-034.html" class="anomaly-link"><span class="link-icon">▶</span> LD-034</a>
      <a href="LD-035.html" class="anomaly-link"><span class="link-icon">▶</span> LD-035</a>
      <a href="LD-035.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-035.5</a>
      <a href="LD-036.html" class="anomaly-link"><span class="link-icon">▶</span> LD-036</a>
      <a href="LD-036.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-036.5</a>
      <a href="LD-037.html" class="anomaly-link"><span class="link-icon">▶</span> LD-037</a>
      <a href="LD-037.5.html" class="anomaly-link"><span class="link-icon">▶</span> LD-037.5</a>
      <a href="LD-038.html" class="anomaly-link"><span class="link-icon">▶</span> LD-038</a>
      <a href="LD-039.html" class="anomaly-link"><span class="link-icon">▶</span> LD-039</a>
      <a href="LD-040.html" class="anomaly-link"><span class="link-icon">▶</span> LD-040</a>
      <a href="LD-041.html" class="anomaly-link"><span class="link-icon">▶</span> LD-041</a>
      <a href="LD-042.html" class="anomaly-link"><span class="link-icon">▶</span> LD-042</a>
      <a href="LD-043.html" class="anomaly-link"><span class="link-icon">▶</span> LD-043</a>
      <a href="LD-044.html" class="anomaly-link"><span class="link-icon">▶</span> LD-044</a>
      <a href="LD-045.html" class="anomaly-link"><span class="link-icon">▶</span> LD-045</a>
      <a href="LD-046.html" class="anomaly-link"><span class="link-icon">▶</span> LD-046</a>
      <a href="LD-047.html" class="anomaly-link"><span class="link-icon">▶</span> LD-047</a>
      <a href="LD-048.html" class="anomaly-link"><span class="link-icon">▶</span> LD-048</a>
      <a href="LD-049.html" class="anomaly-link"><span class="link-icon">▶</span> LD-049</a>
      <a href="LD-050.html" class="anomaly-link"><span class="link-icon">▶</span> LD-050</a>
      <a href="LD-051.html" class="anomaly-link"><span class="link-icon">▶</span> LD-051</a>
      <a href="LD-052.html" class="anomaly-link"><span class="link-icon">▶</span> LD-052</a>
      <a href="LD-053.html" class="anomaly-link"><span class="link-icon">▶</span> LD-053</a>
      <a href="LD-054.html" class="anomaly-link"><span class="link-icon">▶</span> LD-054</a>
      <a href="LD-055.html" class="anomaly-link"><span class="link-icon">▶</span> LD-055</a>
      <a href="LD-056.html" class="anomaly-link"><span class="link-icon">▶</span> LD-056</a>
      <a href="LD-057.html" class="anomaly-link"><span class="link-icon">▶</span> LD-057</a>
      <a href="LD-058.html" class="anomaly-link"><span class="link-icon">▶</span> LD-058</a>
      <a href="LD-059.html" class="anomaly-link"><span class="link-icon">▶</span> LD-059</a>
      <a href="LD-060.html" class="anomaly-link"><span class="link-icon">▶</span> LD-060</a>
      <a href="LD-061.html" class="anomaly-link"><span class="link-icon">▶</span> LD-061</a>
      <a href="LD-062.html" class="anomaly-link"><span class="link-icon">▶</span> LD-062</a>
      <a href="LD-063.html" class="anomaly-link"><span class="link-icon">▶</span> LD-063</a>
      <a href="LD-064.html" class="anomaly-link"><span class="link-icon">▶</span> LD-064</a>
      <a href="LD-065.html" class="anomaly-link"><span class="link-icon">▶</span> LD-065</a>
      <a href="LD-066.html" class="anomaly-link"><span class="link-icon">▶</span> LD-066</a>
      <a href="LD-067.html" class="anomaly-link"><span class="link-icon">▶</span> LD-067</a>
      <a href="LD-068.html" class="anomaly-link"><span class="link-icon">▶</span> LD-068</a>
      <a href="LD-069.html" class="anomaly-link"><span class="link-icon">▶</span> LD-069</a>
      <a href="LD-070.html" class="anomaly-link"><span class="link-icon">▶</span> LD-070</a>
      <a href="LD-071.html" class="anomaly-link"><span class="link-icon">▶</span> LD-071</a>
      <a href="LD-072.html" class="anomaly-link"><span class="link-icon">▶</span> LD-072</a>
      <a href="LD-073.html" class="anomaly-link"><span class="link-icon">▶</span> LD-073</a>
      <a href="LD-074.html" class="anomaly-link"><span class="link-icon">▶</span> LD-074</a>
      <a href="LD-075.html" class="anomaly-link"><span class="link-icon">▶</span> LD-075</a>
      <a href="LD-076.html" class="anomaly-link"><span class="link-icon">▶</span> LD-076</a>
      <a href="LD-077.html" class="anomaly-link"><span class="link-icon">▶</span> LD-077</a>
      <a href="LD-078.html" class="anomaly-link"><span class="link-icon">▶</span> LD-078</a>
      <a href="LD-079.html" class="anomaly-link"><span class="link-icon">▶</span> LD-079</a>
      <a href="LD-080.html" class="anomaly-link"><span class="link-icon">▶</span> LD-080</a>
      <a href="LD-081.html" class="anomaly-link"><span class="link-icon">▶</span> LD-081</a>
      <a href="LD-082.html" class="anomaly-link"><span class="link-icon">▶</span> LD-082</a>
      <a href="LD-083.html" class="anomaly-link"><span class="link-icon">▶</span> LD-083</a>
      <a href="LD-084.html" class="anomaly-link"><span class="link-icon">▶</span> LD-084</a>
      <a href="LD-085.html" class="anomaly-link"><span class="link-icon">▶</span> LD-085</a>
      <a href="LD-086.html" class="anomaly-link"><span class="link-icon">▶</span> LD-086</a>
      <a href="LD-087.html" class="anomaly-link"><span class="link-icon">▶</span> LD-087</a>
      <a href="LD-088.html" class="anomaly-link"><span class="link-icon">▶</span> LD-088</a>
      <a href="LD-089.html" class="anomaly-link"><span class="link-icon">▶</span> LD-089</a>
      <a href="LD-090.html" class="anomaly-link"><span class="link-icon">▶</span> LD-090</a>
      <a href="LD-091.html" class="anomaly-link"><span class="link-icon">▶</span> LD-091</a>
      <a href="LD-092.html" class="anomaly-link"><span class="link-icon">▶</span> LD-092</a>
      <a href="LD-093.html" class="anomaly-link"><span class="link-icon">▶</span> LD-093</a>
      <a href="LD-094.html" class="anomaly-link"><span class="link-icon">▶</span> LD-094</a>
      <a href="LD-095.html" class="anomaly-link"><span class="link-icon">▶</span> LD-095</a>
      <a href="LD-096.html" class="anomaly-link"><span class="link-icon">▶</span> LD-096</a>
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2025-05-07</p>
    </div>

  </div>

  <script>
    function filterAnomalies() {
      const input = document.getElementById('searchInput').value.toLowerCase();
      const links = document.querySelectorAll('.anomaly-link');
      links.forEach(link => {
        const text = link.textContent.toLowerCase();
        link.style.display = text.includes(input) ? 'flex' : 'none';
      });
    }
  </script>

</body>
</html>
