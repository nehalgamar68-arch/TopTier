<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TopTier | Global Rankings</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Background ekdum black aur clean */
        body { background-color: #000000; color: #ffffff; font-family: 'Inter', sans-serif; }
        
        .nav-item { cursor: pointer; transition: 0.3s; border-bottom: 2px solid transparent; }
        .nav-item:hover, .nav-item.active { background: #0a0a0a; border-color: #00ff88; }
        
        /* Table styling without white backgrounds */
        .player-row { border-bottom: 1px solid #111; cursor: pointer; transition: 0.2s; }
        .player-row:hover { background-color: #080808; border-color: #222; }
        
        .tier-badge { 
            background: #111; 
            border: 1px solid #333; 
            padding: 2px 6px; 
            border-radius: 4px; 
            font-size: 10px; 
            display: flex; 
            align-items: center; 
            gap: 4px; 
        }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #000; }
        ::-webkit-scrollbar-thumb { background: #222; border-radius: 10px; }
    </style>
</head>
<body>

    <nav class="flex justify-center bg-[#050505] border-b border-white/5 py-4 gap-2 overflow-x-auto">
        <div class="nav-item active flex flex-col items-center p-3 rounded-t-xl min-w-[75px]">
            <img src="https://mctiers.com/tier_icons/overall.svg" class="w-5 h-5 mb-1">
            <span class="text-[9px] font-bold uppercase tracking-tighter">Overall</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[75px]">
            <img src="https://mctiers.com/tier_icons/sword.svg" class="w-5 h-5 mb-1">
            <span class="text-[9px] font-bold uppercase tracking-tighter">Sword</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[75px]">
            <img src="https://mctiers.com/tier_icons/axe.svg" class="w-5 h-5 mb-1">
            <span class="text-[9px] font-bold uppercase tracking-tighter">Axe</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[75px]">
            <img src="https://mctiers.com/tier_icons/pot.svg" class="w-5 h-5 mb-1">
            <span class="text-[9px] font-bold uppercase tracking-tighter">Pot</span>
        </div>
        <div class="nav-item flex flex-col items-center p-3 rounded-t-xl min-w-[75px]">
            <img src="https://mctiers.com/tier_icons/uhc.svg" class="w-5 h-5 mb-1">
            <span class="text-[9px] font-bold uppercase tracking-tighter">UHC</span>
        </div>
    </nav>

    <div class="max-w-4xl mx-auto px-4 py-8">
        <input type="text" id="pSearch" onkeyup="searchPlayers()" placeholder="Search player..." 
               class="w-full bg-[#080808] border border-white/10 rounded-lg py-3 px-5 text-sm focus:outline-none focus:border-green-500 mb-8">

        <h2 class="text-xs font-bold text-gray-600 uppercase mb-4 tracking-[0.2em]">Overall Rankings</h2>

        <div class="border border-white/5 rounded-xl overflow-hidden">
            <div class="grid grid-cols-12 p-4 text-[10px] font-black text-gray-600 uppercase bg-[#050505] border-b border-white/5">
                <div class="col-span-1">#</div>
                <div class="col-span-4">Player</div>
                <div class="col-span-2 text-center">Region</div>
                <div class="col-span-5 text-right">Modes</div>
            </div>

            <div id="playerListContainer">
                </div>
        </div>
    </div>

    <script>
        // Fake data generate karne ke liye loop
        const container = document.getElementById('playerListContainer');
        const sample
