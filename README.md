<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS Clone</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #0a0a0a; color: #eee; font-family: sans-serif; }
        .nav-icon { filter: grayscale(100%); transition: 0.3s; cursor: pointer; }
        .nav-icon:hover, .nav-icon.active { filter: grayscale(0%); background: #1a1a1a; border-bottom: 3px solid #00ff88; }
        .player-row:hover { background: #111; }
        .tier-badge { font-size: 10px; font-weight: bold; padding: 2px 4px; border-radius: 4px; margin-right: 4px; }
    </style>
</head>
<body>

    <nav class="flex justify-center bg-[#111] border-b border-white/10 overflow-x-auto py-2 px-4 gap-2">
        <div class="nav-icon active flex flex-col items-center p-2 rounded-t-lg min-w-[70px]">
            <img src="https://img.icons8.com/color/48/trophy.png" class="w-6 h-6 mb-1">
            <span class="text-[10px] uppercase font-bold text-green-400">Overall</span>
        </div>
        <div class="nav-icon flex flex-col items-center p-2 rounded-t-lg min-w-[70px]">
            <img src="https://img.icons8.com/color/48/sword.png" class="w-6 h-6 mb-1">
            <span class="text-[10px] uppercase font-bold">Sword</span>
        </div>
        <div class="nav-icon flex flex-col items-center p-2 rounded-t-lg min-w-[70px]">
            <img src="https://img.icons8.com/color/48/battle-axe.png" class="w-6 h-6 mb-1">
            <span class="text-[10px] uppercase font-bold">Axe</span>
        </div>
        <div class="nav-icon flex flex-col items-center p-2 rounded-t-lg min-w-[70px]">
            <img src="https://img.icons8.com/color/48/potions.png" class="w-6 h-6 mb-1">
            <span class="text-[10px] uppercase font-bold">Pot</span>
        </div>
        <div class="nav-icon flex flex-col items-center p-2 rounded-t-lg min-w-[70px]">
            <img src="https://img.icons8.com/color/48/shield.png" class="w-6 h-6 mb-1">
            <span class="text-[10px] uppercase font-bold">UHC</span>
        </div>
    </nav>

    <div class="max-w-5xl mx-auto mt-6 px-4">
        <input type="text" id="pSearch" onkeyup="filterPlayers()" placeholder="Search player..." 
               class="w-full bg-[#111] border border-white/10 rounded-lg py-3 px-5 focus:outline-none focus:border-green-500 text-sm">
        
        <h2 class="mt-6 text-xl font-bold uppercase tracking-tight">Overall Rankings</h2>

        <div class="mt-4 bg-[#111]/50 border border-white/5 rounded-xl overflow-hidden">
            <div class="grid grid-cols-12 gap-2 p-3 text-[10px] font-bold text-gray-500 uppercase border-b border-white/5">
                <div class="col-span-1">#</div>
                <div class="col-span-4">Player</div>
                <div class="col-span-2 text-center">Region</div>
                <div class="col-span-5 text-right">Modes</div>
            </div>

            <div id="playerContainer">
                <div class="player-row grid grid-cols-12 gap-2 p-4 items-center border-b border-white/5 transition">
                    <div class="col-span-1 font-bold text-gray-400">1</div>
                    <div class="col-span-4 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/Smitenesss/32" class="rounded shadow-md">
                        <span class="font-bold text-blue-400 playerName">Smitenesss</span>
                    </div>
                    <div class="col-span-2 text-center text-gray-400 text-sm font-bold">EU</div>
                    <div class="col-span-5 flex justify-end gap-1 flex-wrap">
                        <span class="tier-badge bg-blue-500/20 text-blue-400 border border-blue-500/30">⚔️ LT3</span>
                        <span class="tier-badge bg-purple-500/20 text-purple-400 border border-purple-500/30">🧪 LT3</span>
                        <span class="tier-badge bg-red-500/20 text-red-400 border border-red-500/30">🪓 LT3</span>
                    </div>
                </div>

                <div class="player-row grid grid-cols-12 gap-2 p-4 items-center border-b border-white/5 transition">
                    <div class="col-span-1 font-bold text-gray-400">2</div>
                    <div class="col-span-4 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/SaumyaXtreme/32" class="rounded shadow-md">
                        <span class="font-bold text-red-500 playerName">SaumyaXtreme</span>
                    </div>
                    <div class="col-span-2 text-center text-gray-400 text-sm font-bold">AS</div>
                    <div class="col-span-5 flex justify-end gap-1 flex-wrap">
                        <span class="tier-badge bg-purple-500/20 text-purple-400 border border-purple-500/30">💎 HT4</span>
                        <span class="tier-badge bg-green-500/20 text-green-400 border border-green-500/30">❤️ LT4</span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        function filterPlayers() {
            let input = document.getElementById('pSearch').value.toLowerCase();
            let rows = document.getElementsByClassName('player-row');
            
            for (let i = 0; i < rows.length; i++) {
                let name = rows[i].getElementsByClassName('playerName')[0].innerText.toLowerCase();
                rows[i].style.display = name.includes(input) ? "grid" : "none";
            }
        }
    </script>
</body>
</html>

