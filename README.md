<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS | Pro Rankings</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; background-color: #050505; }
        .glass { background: rgba(20, 20, 20, 0.8); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1); }
        .tier-card:hover { transform: translateY(-2px); transition: all 0.2s; border-color: #3b82f6; }
    </style>
</head>
<body class="text-gray-200">

    <header class="w-full max-w-6xl mx-auto py-8 px-4">
        <div class="flex justify-between items-center bg-[#111] p-4 rounded-2xl border border-white/5 shadow-2xl">
            <div class="flex items-center gap-4">
                <div class="h-10 w-10 bg-blue-600 rounded-lg flex items-center justify-center font-bold text-white">MC</div>
                <h1 class="text-xl font-extrabold uppercase tracking-widest">Rankings</h1>
            </div>
            
            <div class="relative w-1/3">
                <input type="text" id="playerSearch" onkeyup="searchPlayer()" placeholder="Search player..." 
                       class="w-full bg-black/50 border border-white/10 rounded-xl py-2 px-4 focus:outline-none focus:border-blue-500 transition">
            </div>
        </div>
    </header>

    <main class="max-w-6xl mx-auto px-4">
        
        <div class="flex gap-2 overflow-x-auto pb-4 no-scrollbar">
            <button class="bg-blue-600 text-white px-6 py-2 rounded-full text-sm font-bold shadow-lg shadow-blue-900/20">Overall</button>
            <button class="bg-[#111] hover:bg-[#222] px-6 py-2 rounded-full text-sm font-bold border border-white/5">Vanilla</button>
            <button class="bg-[#111] hover:bg-[#222] px-6 py-2 rounded-full text-sm font-bold border border-white/5">Axe</button>
            <button class="bg-[#111] hover:bg-[#222] px-6 py-2 rounded-full text-sm font-bold border border-white/5">UHC</button>
        </div>

        <div class="glass rounded-3xl overflow-hidden mt-4">
            <div class="grid grid-cols-5 bg-white/5 p-4 text-xs font-black uppercase tracking-wider text-gray-500">
                <div class="col-span-1"># Rank</div>
                <div class="col-span-2">Player</div>
                <div class="col-span-1 text-center">Region</div>
                <div class="col-span-1 text-right">Tier Status</div>
            </div>

            <div id="playerList" class="divide-y divide-white/5">
                <div class="player-row grid grid-cols-5 p-4 items-center hover:bg-white/[0.02] transition">
                    <div class="text-blue-500 font-black text-lg">01</div>
                    <div class="col-span-2 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/Technoblade/40" class="rounded-lg shadow-lg" alt="skin">
                        <div>
                            <p class="font-bold text-white playerName">Technoblade</p>
                            <p class="text-[10px] text-gray-500 italic">Legendary Status</p>
                        </div>
                    </div>
                    <div class="text-center font-semibold text-gray-400">US</div>
                    <div class="text-right">
                        <span class="bg-red-500/20 text-red-500 border border-red-500/50 px-3 py-1 rounded-md text-xs font-black">HIGH TIER 1</span>
                    </div>
                </div>

                <div class="player-row grid grid-cols-5 p-4 items-center hover:bg-white/[0.02] transition">
                    <div class="text-gray-500 font-black text-lg">02</div>
                    <div class="col-span-2 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/Dream/40" class="rounded-lg shadow-lg" alt="skin">
                        <div>
                            <p class="font-bold text-white playerName">Dream</p>
                            <p class="text-[10px] text-gray-500 italic">Speedrunner</p>
                        </div>
                    </div>
                    <div class="text-center font-semibold text-gray-400">NA</div>
                    <div class="text-right">
                        <span class="bg-orange-500/20 text-orange-500 border border-orange-500/50 px-3 py-1 rounded-md text-xs font-black">MID TIER 1</span>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <script>
        function searchPlayer() {
            let input = document.getElementById('playerSearch').value.toLowerCase();
            let rows = document.getElementsByClassName('player-row');
            
            for (let i = 0; i < rows.length; i++) {
                let name = rows[i].getElementsByClassName('playerName')[0].innerText.toLowerCase();
                if (name.includes(input)) {
                    rows[i].style.display = "grid";
                } else {
                    rows[i].style.display = "none";
                }
            }
        }
    </script>

</body>
</html>
