<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS Pro</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #050505; color: #eee; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        .nav-item { cursor: pointer; border-bottom: 2px solid transparent; transition: 0.2s; }
        .nav-item:hover, .nav-item.active { background: #111; border-color: #00ff88; color: #00ff88; }
        .player-row { cursor: pointer; transition: 0.2s; border-bottom: 1px solid #111; }
        .player-row:hover { background-color: #0f0f0f; border-color: #333; }
        .mode-icon { height: 16px; width: 16px; display: inline-block; }
    </style>
</head>
<body>

    <nav class="flex justify-center bg-[#0a0a0a] border-b border-white/5 py-3 gap-4 overflow-x-auto">
        <div class="nav-item active flex flex-col items-center p-3 rounded-t-xl min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/overall.svg" class="w-6 h-6 mb-1">
            <span class="text-[10px] font-bold uppercase">Overall</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/sword.svg" class="w-6 h-6 mb-1">
            <span class="text-[10px] font-bold uppercase">Sword</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/axe.svg" class="w-6 h-6 mb-1">
            <span class="text-[10px] font-bold uppercase">Axe</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[80px]">
            <img src="https://mctiers.com/tier_icons/pot.svg" class="w-6 h-6 mb-1">
            <span class="text-[10px] font-bold uppercase">Pot</span>
        </div>
    </nav>

    <div class="max-w-4xl mx-auto px-4 mt-8">
        <div class="relative mb-8">
            <input type="text" id="searchInput" onkeyup="search()" placeholder="Search player..." 
                   class="w-full bg-[#111] border border-white/10 py-3 px-5 rounded-xl focus:outline-none focus:border-green-500 transition">
        </div>

        <h2 class="text-sm font-black text-gray-500 uppercase mb-4 tracking-widest">Overall Rankings</h2>

        <div class="bg-[#0a0a0a] border border-white/5 rounded-2xl overflow-hidden shadow-2xl">
            <div class="grid grid-cols-12 p-4 text-[11px] font-bold text-gray-600 uppercase border-b border-white/5 bg-white/[0.02]">
                <div class="col-span-1">#</div>
                <div class="col-span-4">Player</div>
                <div class="col-span-2 text-center">Region</div>
                <div class="col-span-5 text-right">Modes</div>
            </div>

            <div id="list">
                <div class="player-row grid grid-cols-12 p-5 items-center" onclick="window.location.href='/profile/Smitenesss'">
                    <div class="col-span-1 font-bold text-gray-500 text-sm">1</div>
                    <div class="col-span-4 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/Smitenesss/30" class="rounded shadow-sm">
                        <span class="font-bold text-blue-400 name">Smitenesss</span>
                    </div>
                    <div class="col-span-2 text-center text-gray-400 font-bold text-xs">EU</div>
                    <div class="col-span-5 flex justify-end gap-1">
                        <span class="bg-[#111] border border-white/10 px-2 py-1 rounded text-[10px] flex items-center gap-1">
                            <img src="https://mctiers.com/tier_icons/sword.svg" class="mode-icon"> LT3
                        </span>
                        <span class="bg-[#111] border border-white/10 px-2 py-1 rounded text-[10px] flex items-center gap-1">
                            <img src="https://mctiers.com/tier_icons/pot.svg" class="mode-icon"> LT3
                        </span>
                    </div>
                </div>

                <div class="player-row grid grid-cols-12 p-5 items-center" onclick="window.location.href='/profile/SaumyaXtreme'">
                    <div class="col-span-1 font-bold text-gray-500 text-sm">2</div>
                    <div class="col-span-4 flex items-center gap-3">
                        <img src="https://mc-heads.net/avatar/SaumyaXtreme/30" class="rounded shadow-sm">
                        <span class="font-bold text-red-500 name">SaumyaXtreme</span>
                    </div>
                    <div class="col-span-2 text-center text-gray-400 font-bold text-xs">AS</div>
                    <div class="col-span-5 flex justify-end gap-1">
                        <span class="bg-[#111] border border-white/10 px-2 py-1 rounded text-[10px] flex items-center gap-1">
                            <img src="https://mctiers.com/tier_icons/vanilla.svg" class="mode-icon"> HT4
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Search Function
        function search() {
            let filter = document.getElementById('searchInput').value.toLowerCase();
            let rows = document.querySelectorAll('.player-row');
            rows.forEach(row => {
                let name = row.querySelector('.name').innerText.toLowerCase();
                row.style.display = name.includes(filter) ? "grid" : "none";
            });
        }
    </script>
</body>
</html>
