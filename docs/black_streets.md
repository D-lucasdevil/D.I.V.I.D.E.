
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>D.I.V.I.D.E. — Black Streets</title>
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

    .file-header {
      border: 1px solid #3a0000;
      padding: 30px;
      margin-bottom: 24px;
      position: relative;
      background: linear-gradient(180deg, #0f0000 0%, #080808 100%);
    }

    .file-header::before {
      content: '// CLASSIFIED FILE //';
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
      font-size: 42px;
      font-weight: 700;
      color: #ffd600;
      letter-spacing: 6px;
      text-shadow: 0 0 20px rgba(255,214,0,0.2);
      margin-bottom: 6px;
    }

    .file-designation {
      font-size: 11px;
      color: #666;
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    .meta-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
    }

    @media (max-width: 600px) { .meta-grid { grid-template-columns: 1fr; } }

    .meta-item {
      display: flex;
      gap: 10px;
      padding: 8px 12px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      font-size: 11px;
    }

    .meta-label { color: #555; letter-spacing: 1px; white-space: nowrap; }
    .meta-value { color: #aaa; letter-spacing: 1px; }
    .meta-value.yellow { color: #ffd600; }
    .meta-value.red { color: #cc0000; }
    .meta-value.green { color: #4caf50; }

    .section-label {
      font-size: 10px;
      letter-spacing: 4px;
      color: #8b0000;
      text-transform: uppercase;
      margin-bottom: 10px;
      margin-top: 28px;
      padding-bottom: 6px;
      border-bottom: 1px solid #1a0000;
    }

    .content-block {
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      padding: 16px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      line-height: 1.9;
      color: #888;
    }

    .content-block p { margin-bottom: 8px; }
    .content-block p:last-child { margin-bottom: 0; }

    .trade-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .trade-grid { grid-template-columns: 1fr; } }

    .trade-item {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #2a2a00;
      font-size: 12px;
      color: #888;
    }

    .trade-item .dot {
      width: 6px; height: 6px;
      background: #ffd600;
      border-radius: 50%;
      flex-shrink: 0;
    }

    .market-table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 8px;
    }

    .market-table th {
      background: #111;
      color: #555;
      font-size: 10px;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 8px 14px;
      text-align: left;
      border: 1px solid #1a1a1a;
    }

    .market-table td {
      padding: 10px 14px;
      border: 1px solid #1a1a1a;
      font-size: 12px;
      color: #888;
      background: #0d0d0d;
    }

    .market-table tr:hover td { background: #111; }

    .tier-i   { color: #4fc3f7; }
    .tier-ii  { color: #4caf50; }
    .tier-iii { color: #ffd600; }

    .protocol-item {
      display: flex;
      align-items: flex-start;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      border-left: 3px solid #3a0000;
      font-size: 12px;
      color: #888;
      margin-bottom: 5px;
      line-height: 1.6;
    }

    .protocol-item .arrow { color: #8b0000; flex-shrink: 0; margin-top: 2px; }

    .forbidden-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 10px 14px;
      background: #0d0d0d;
      border: 1px solid #1a0000;
      border-left: 3px solid #8b0000;
      font-size: 12px;
      color: #cc4444;
      margin-bottom: 5px;
    }

    .forbidden-item .x { color: #cc0000; font-size: 14px; }

    .punishment-block {
      background: #0d0000;
      border: 1px solid #3a0000;
      border-left: 3px solid #cc0000;
      padding: 14px 18px;
      margin-bottom: 8px;
      font-size: 12px;
      color: #cc4444;
      line-height: 1.8;
    }

    .protector-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-bottom: 8px;
    }

    @media (max-width: 600px) { .protector-grid { grid-template-columns: 1fr; } }

    .protector-card {
      padding: 16px;
      background: #0d0d0d;
      border: 1px solid #1a1a1a;
      font-size: 12px;
    }

    .protector-card.standard { border-top: 3px solid #ffd600; }
    .protector-card.elite { border-top: 3px solid #e65100; }

    .protector-title {
      font-family: 'Rajdhani', sans-serif;
      font-size: 14px;
      font-weight: 600;
      letter-spacing: 2px;
      margin-bottom: 8px;
      text-transform: uppercase;
    }

    .protector-card.standard .protector-title { color: #ffd600; }
    .protector-card.elite .protector-title { color: #e65100; }
    .protector-card p { color: #666; line-height: 1.6; }

    .transaction-box {
      background: #0d0d0d;
      border: 1px solid #2a2a00;
      border-left: 4px solid #ffd600;
      padding: 18px;
      margin-bottom: 8px;
    }

    .transaction-box .amount {
      font-family: 'Rajdhani', sans-serif;
      font-size: 28px;
      font-weight: 700;
      color: #ffd600;
      letter-spacing: 2px;
      margin-bottom: 4px;
    }

    .transaction-box .item { font-size: 12px; color: #aaa; letter-spacing: 1px; margin-bottom: 8px; }
    .transaction-box .detail { font-size: 11px; color: #555; letter-spacing: 1px; }

    .internal-quote {
      background: #080808;
      border: 1px solid #1a1a1a;
      border-left: 4px solid #ffd600;
      padding: 20px 24px;
      margin: 20px 0;
      position: relative;
    }

    .internal-quote::before {
      content: '"';
      position: absolute;
      top: -10px; left: 16px;
      background: #080808;
      padding: 0 6px;
      color: #ffd600;
      font-size: 30px;
      font-family: serif;
      line-height: 1;
    }

    .internal-quote p { font-size: 14px; color: #aaa; line-height: 1.8; font-style: italic; }
    .internal-quote .attribution { margin-top: 10px; font-size: 10px; color: #555; letter-spacing: 2px; text-transform: uppercase; font-style: normal; }

    .notice-box {
      background: #0d0800;
      border: 1px solid #2a1a00;
      border-left: 3px solid #e65100;
      padding: 14px 18px;
      font-size: 11px;
      color: #887766;
      line-height: 1.7;
      margin-top: 20px;
    }

    .notice-box strong { color: #e65100; }

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
      <div class="file-title">BLACK STREETS</div>
      <div class="file-designation">Illicit Trade Zone / Anomalous Market Hub — Active File</div>
      <div class="meta-grid">
        <div class="meta-item">
          <span class="meta-label">THREAT LEVEL</span>
          <span class="meta-value yellow">Class III — Localized</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">CLEARANCE</span>
          <span class="meta-value red">DIVIDE Level 1+</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">STATUS</span>
          <span class="meta-value green">Monitored / Indirectly Controlled</span>
        </div>
        <div class="meta-item">
          <span class="meta-label">LOCATION</span>
          <span class="meta-value red">[REDACTED] — Czech Republic</span>
        </div>
      </div>
    </div>

    <div class="section-label">// Overview //</div>
    <div class="content-block">
      <p>Black Street is a highly secured, underground trade zone located within the Czech Republic at [REDACTED]. It functions as a global marketplace for illegal, restricted, and anomalous goods, operating beyond conventional law enforcement and partially tolerated by D.I.V.I.D.E.</p>
      <p>The location is considered the <strong style="color:#aaa">second most protected area in the world</strong>, surpassed only by D.I.V.I.D.E. central command infrastructure.</p>
      <p>Black Street is widely known among criminal networks, private collectors, rogue researchers, and certain government contacts. Despite its illegal nature, it operates under strict internal order and enforcement.</p>
    </div>

    <div class="section-label">// Trade & Economy //</div>
    <div class="trade-grid">
      <div class="trade-item"><div class="dot"></div>Anomalies — Primary Commodity</div>
      <div class="trade-item"><div class="dot"></div>Military-Grade Weapons</div>
      <div class="trade-item"><div class="dot"></div>Controlled Substances</div>
      <div class="trade-item"><div class="dot"></div>Human Organs — On-Site Surgical Staff</div>
      <div class="trade-item"><div class="dot"></div>Classified Documents</div>
      <div class="trade-item"><div class="dot"></div>Restricted Technology</div>
    </div>

    <div class="section-label">// Anomaly Market Values (Estimated) //</div>
    <table class="market-table">
      <thead>
        <tr>
          <th>Class</th>
          <th>Threat Level</th>
          <th>Estimated Value</th>
          <th>Notes</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="tier-i">Class I</td>
          <td>Low</td>
          <td class="tier-i">$20M – $50M</td>
          <td>Stable, low-risk items</td>
        </tr>
        <tr>
          <td class="tier-ii">Class II</td>
          <td>Moderate</td>
          <td class="tier-ii">$100M – $500M</td>
          <td>Manageable with containment</td>
        </tr>
        <tr>
          <td class="tier-iii">Class III</td>
          <td>High</td>
          <td class="tier-iii">Rare — up to $2B+</td>
          <td>Extreme demand, low availability</td>
        </tr>
      </tbody>
    </table>

    <div class="content-block">
      <p><strong style="color:#aaa">Item-type anomalies</strong> are significantly more valuable than living entities due to their stability, ease of transport, and controllability.</p>
      <p><strong style="color:#aaa">Living anomalies</strong> are rarely sold unless deceased, heavily contained, or deemed genuinely low-risk to the buyer.</p>
    </div>

    <div class="section-label">// D.I.V.I.D.E. Involvement //</div>
    <div class="content-block">
      <p>Despite its nature, D.I.V.I.D.E. does not shut down Black Street. The organization views it as a centralized anomaly funnel, a live tracking system for high-risk artifacts, and an active acquisition opportunity.</p>
    </div>
    <div class="protocol-item"><span class="arrow">▶</span>Any discovered anomaly may be purchased, temporarily confiscated, or permanently seized — with fair market compensation offered.</div>
    <div class="protocol-item"><span class="arrow">▶</span>If an individual resists and weaponizes an anomaly: immediate termination is authorized. The artifact is recovered without negotiation.</div>
    <div class="protocol-item"><span class="arrow">▶</span>Nuclear weapon transactions are strictly monitored. Unauthorized buyers are executed without warning.</div>

    <div class="section-label">// Internal Law — Strictly Forbidden //</div>
    <div class="forbidden-item"><span class="x">✕</span>Murder</div>
    <div class="forbidden-item"><span class="x">✕</span>Assault</div>
    <div class="forbidden-item"><span class="x">✕</span>Sexual Violence</div>
    <div class="forbidden-item"><span class="x">✕</span>Theft</div>

    <div class="punishment-block">
      <strong style="color:#ff4444">PUNISHMENT:</strong> Immediate execution followed by public skinning of the offender.<br>
      Punishments are carried out publicly to maintain order and deter disruption. No exceptions. No appeals.
    </div>

    <div class="section-label">// Security & Protection //</div>
    <div class="protector-grid">
      <div class="protector-card standard">
        <div class="protector-title">Standard Protectors</div>
        <p>Enforcement entities comparable to Class III anomalies. Deployed throughout the trading floor. Zero conflict tolerance. Rapid neutralization of any threat to market stability.</p>
      </div>
      <div class="protector-card elite">
        <div class="protector-title">Elite Protectors</div>
        <p>Comparable to low Class IV anomalies. Reserved for high-value zones and direct enforcement. Total control of all activity. Their presence alone deters most threats.</p>
      </div>
    </div>

    <div class="section-label">// Residency //</div>
    <div class="content-block">
      <p>Permanent residence within Black Street is possible but extremely expensive, restricted to high-value individuals, and subject to constant monitoring.</p>
      <p>Known resident categories include: black market traders, rogue scientists, and wealthy anomaly collectors.</p>
    </div>

    <div class="section-label">// Notable Transaction //</div>
    <div class="transaction-box">
      <div class="amount">$220,000,000 USD</div>
      <div class="item">LD-016 — "Andy's Revolver"</div>
      <div class="detail">Transaction included an additional agreement: D.I.V.I.D.E. protection contract for the buyer. Terms classified.</div>
    </div>

    <div class="internal-quote">
      <p>You don't shut down Black Street.<br>You watch it… and make sure the wrong people don't walk out with the wrong things.</p>
      <div class="attribution">— D.I.V.I.D.E. Oversight Command</div>
    </div>

    <div class="section-label">// Risk Assessment //</div>
    <div class="content-block">
      <p>While dangerous, Black Street is considered more stable than decentralized black markets, significantly easier to monitor than global anomaly smuggling networks, and a necessary evil within the current containment system.</p>
    </div>

    <div class="notice-box">
      <strong>Classification Notice:</strong> This file is accessible to Level 1 personnel due to the widespread awareness of Black Street within both civilian and underground networks. Operational details remain classified at higher clearance levels.
    </div>

    <div class="footer">
      <p>&copy; 2025 Lucas Devil. All rights reserved.</p>
      <p>D.I.V.I.D.E.™ and all related characters, storylines, and assets are original creations of Lucas Devil.</p>
      <p>Unauthorized use, reproduction, or redistribution strictly prohibited. First created: 2026-03-24</p>
    </div>

  </div>

</body>
</html>
