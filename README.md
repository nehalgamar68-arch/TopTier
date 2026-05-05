<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS | Rankings</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #000000; color: #ffffff; font-family: sans-serif; }
        
        /* Navigation Styling */
        .nav-active { border-bottom: 3px solid #00ff88; background: #0a0a0a; }
        .nav-item { cursor: pointer; transition: 0.2s; }

        /* Card Design (Screenshot jaisa) */
        .player-card { 
            background-color: #0a0c10; 
            border: 1px solid #1a1c20; 
            border-radius: 16px; 
            margin-bottom: 12px;
            padding: 16px;
        }
        
        .rank-box {
            background: linear-gradient(135deg, #facc15 0%, #ca8a04 100%);
            color: black;
            font-weight: 900;
            font-style: italic;
            padding: 4px 12px;
            border-radius: 4px;
            transform: skewX(-10deg);
        }

        .region-tag {
            background: #1a1a1a;
            color: #ef4444; /* NA is Red in your screenshot */
            font-weight: bold;
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 12px;
        }

        .tier-icon-circle {
            background: #111;
            border: 1px solid #333;
            border-radius: 50%;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tier-label { font-size: 10px; font-weight: bold; text-align: center; margin-top: 4px; }
        
        /* Hide Scrollbar */
        ::-webkit-scrollbar { display: none; }
    </style>
</head>
<body class="p-4">

    <nav class="flex justify-center gap-2 mb-6 overflow-x-auto pb-2 border-b border-white/5">
        <div class="nav-item nav-active flex flex-col items-center p-3 min-w-[80px] rounded-t-lg">
            <img src="https://mctiers.com/tier_icons/overall.svg" class="w-6 h-6">
            <span class="text-[10px] font-bold mt-1 uppercase">Overall</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/sword.svg" class="w-6 h-6">
            <span class="text-[10px] font-bold mt-1 uppercase">LTMs</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/vanilla.svg" class="w-6 h-6">
            <span class="text-[10px] font-bold mt-1 uppercase">Vanilla</span>
        </div>
    </nav>

    <input type="text" id="pSearch" onkeyup="search()" placeholder="Search player..." 
           class="w-full bg-[#0a0a0a] border border-white/10 rounded-xl py-3 px-4 text-sm mb-6 outline-none focus:border-green-500">

    <div id="playerList">
        </div>

    <script>
        const list = document.getElementById('playerList');
        const names = ["ItzReal...", "coldified", "Smitenesss", "SaumyaXtreme", "Dream", "Techno"];
        const regs = ["NA", "EU", "AS"];

        for (let i = 1; i <= 50; i++) {
            let name = names[i % names.length] + (i > 6 ? i : "");
            let reg = regs[i % 3];
            let regColor = reg === "NA" ? "text-red-500" : (reg === "EU" ? "text-green-500" : "text-blue-500");

            list.innerHTML += `
                <div class="player-card" onclick="console.log('Clicked ${name}')">
                    <div class="flex justify-between items-start mb-4">
                        <div class="flex items-center gap-4">
                            <div class="rank-box text-lg">${i}.</div>
                            <img src="https://mc-heads.net/avatar/${name}/40" class="rounded-md">
                            <div>
                                <h2 class="text-xl font-bold tracking-tight">${name}</h2>
                                <p class="text-[10px] text-gray-500">Combat Participant</p>
                            </div>
                        </div>
                        <div class="region-tag ${regColor}">${reg}</div>
                    </div>

                    <p class="text-[10px] font-bold text-gray-500 uppercase mb-3">Tiers</p>
                    
                    <div class="flex gap-3 flex-wrap">
                        <div class="flex flex-col items-center">
                            <div class="tier-icon-circle"><img src="https://mctiers.com/tier_icons/sword.svg" class="w-4"></div>
                            <span class="tier-label text-orange-400">HT3</span>
                        </div>
                        <div class="flex flex-col items-center">
                            <div class="tier-icon-circle"><img src="https://mctiers.com/tier_icons/vanilla.svg" class="w-4"></div>
                            <span class="tier-label text-yellow-400">HT1</span>
                        </div>
                        <div class="flex flex-col items-center">
                            <div class="tier-icon-circle"><img src="https://mctiers.com/tier_icons/pot.svg" class="w-4"></div>
                            <span class="tier-label text-yellow-400">HT1</span>
                        </div>
                        <div class="flex flex-col items-center">
                            <div class="tier-icon-circle"><img src="https://mctiers.com/tier_icons/uhc.svg" class="w-4"></div>
                            <span class="tier-label text-gray-400">LT2</span>
                        </div>
                    </div>
                </div>
            `;
        }

        function search() {
            let filter = document.getElementById('pSearch').value.toLowerCase();
            let cards = document.querySelectorAll('.player-card');
            cards.forEach(card => {
                let name = card.querySelector('h2').innerText.toLowerCase();
                card.style.display = name.includes(filter) ? "block" : "none";
            });
        }
    </script>
</body>
</html>
