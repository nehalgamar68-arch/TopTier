<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTiers Leaderboard</title>
    <style>
        /* Base Styling & Theme Colors matched from Screenshot_20260604_005305.jpg */
        body {
            background-color: #0d1117;
            color: #ffffff;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        .container {
            width: 100%;
            max-width: 480px; /* Mobile responsive view layout */
        }

        /* Header & Search Engine */
        .header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #ffb703;
            letter-spacing: 1px;
        }

        .search-box {
            position: relative;
            width: 60%;
        }

        .search-box input {
            width: 100%;
            padding: 10px 15px;
            background-color: #161b22;
            border: 1px solid #30363d;
            border-radius: 8px;
            color: #fff;
            font-size: 14px;
            outline: none;
            box-sizing: border-box;
        }

        .search-box input:focus {
            border-color: #58a6ff;
        }

        /* Leaderboard Cards styling */
        .player-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .player-card {
            background-color: #161c24;
            border: 1px solid #21262d;
            border-radius: 12px;
            padding: 16px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        }

        .player-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .rank-name-box {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .rank {
            font-size: 22px;
            font-weight: 900;
            font-style: italic;
            color: #8b949e;
        }

        /* Clickable external player link styling */
        .player-link {
            font-size: 20px;
            font-weight: bold;
            color: #ffffff;
            text-decoration: none;
            transition: color 0.2s ease;
        }

        .player-link:hover {
            color: #58a6ff;
            text-decoration: underline;
        }

        .region-badge {
            font-size: 12px;
            font-weight: bold;
            padding: 4px 8px;
            border-radius: 6px;
        }

        .na { background-color: #da373c; color: #fff; }
        .eu { background-color: #1f6fed; color: #fff; }

        /* Tiers Matrix Grid */
        .tiers-title {
            font-size: 12px;
            color: #8b949e;
            font-weight: bold;
            margin-bottom: 8px;
            letter-spacing: 1px;
        }

        .tiers-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tier-badge {
            background-color: #0d1117;
            border: 1px solid #30363d;
            border-radius: 8px;
            width: 48px;
            padding: 6px 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .tier-icon {
            width: 20px;
            height: 20px;
            object-fit: contain;
            margin-bottom: 4px;
        }

        .tier-rank {
            font-size: 11px;
            font-weight: bold;
        }

        /* High Tier (HT) vs Low Tier (LT) Text styling */
        .ht { color: #ff9f43; }
        .lt { color: #8b949e; }
    </style>
</head>
<body>

<div class="container">
    <!-- Header Block mimicking Screenshot_20260604_005305.jpg -->
    <div class="header">
        <div class="logo">MCTIERS</div>
        <div class="search-box">
            <input type="text" id="playerSearch" placeholder="🔍 Search player..." onkeyup="filterPlayers()">
        </div>
    </div>

    <!-- Active Player Container Layout -->
    <div class="player-list" id="playerList">
        <!-- Live dynamic rendering from JavaScript engine -->
    </div>
</div>

<script>
    // Database Array Object detailing active paths
    // Note: SVG paths point locally to your system files (e.g., 'sword.svg'). 
    // If you host them on a server or GitHub, update the text to the online link.
    const playersData = [
        {
            rank: "1.",
            name: "ItzReal...",
            region: "NA",
            regionClass: "na",
            documentUrl: "https://namemc.com/profile/ItzReal", // The clickable document link
            tiers: [
                { icon: "sword.svg", rank: "HT3", class: "ht" },
                { icon: "netpot.svg", rank: "HT1", class: "ht" },
                { icon: "pearl.svg", rank: "HT1", class: "ht" },
                { icon: "pot.svg", rank: "HT1", class: "ht" },
                { icon: "mace.svg", rank: "LT2", class: "lt" },
                { icon: "axe.svg", rank: "LT2", class: "lt" }
            ]
        },
        {
            rank: "2.",
            name: "coldified",
            region: "EU",
            regionClass: "eu",
            documentUrl: "https://namemc.com/profile/coldified", // The clickable document link
            tiers: [
                { icon: "mace.svg", rank: "LT1", class: "lt" },
                { icon: "pot.svg", rank: "LT1", class: "lt" },
                { icon: "netpot.svg", rank: "LT3", class: "lt" },
                { icon: "pearl.svg", rank: "HT1", class: "ht" },
                { icon: "sword.svg", rank: "LT1", class: "lt" },
                { icon: "axe.svg", rank: "LT1", class: "lt" }
            ]
        }
    ];

    // Functions to inject and draw DOM elements onto screen 
    function renderLeaderboard(data) {
        const container = document.getElementById("playerList");
        container.innerHTML = ""; // Clear existing records

        data.forEach(player => {
            let tierItemsHTML = "";
            player.tiers.forEach(t => {
                tierItemsHTML += `
                    <div class="tier-badge">
                        <img src="${t.icon}" alt="icon" class="tier-icon" onerror="this.src='https://unpkg.com/lucide-static@latest/icons/help-circle.svg'">
                        <span class="tier-rank ${t.class}">${t.rank}</span>
                    </div>
                `;
            });

            const cardHTML = `
                <div class="player-card">
                    <div class="player-info">
                        <div class="rank-name-box">
                            <span class="rank">${player.rank}</span>
                            <!-- Dynamic clickable profile redirect doc -->
                            <a href="${player.documentUrl}" target="_blank" class="player-link">${player.name}</a>
                        </div>
                        <span class="region-badge ${player.regionClass}">${player.region}</span>
                    </div>
                    <div class="tiers-title">TIERS</div>
                    <div class="tiers-grid">
                        ${tierItemsHTML}
                    </div>
                </div>
            `;
            container.innerHTML += cardHTML;
        });
    }

    // Engine to check and execute input tracking search parameters
    function filterPlayers() {
        const query = document.getElementById("playerSearch").value.toLowerCase();
        const filtered = playersData.filter(player => 
            player.name.toLowerCase().includes(query)
        );
        renderLeaderboard(filtered);
    }

    // Run basic initialize sequence
    renderLeaderboard(playersData);
</script>
</body>
</html>
