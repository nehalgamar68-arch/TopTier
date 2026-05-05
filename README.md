<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS | Pro Rankings</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #000000; color: #ffffff; font-family: sans-serif; }

        /* Card Container */
        .player-card { 
            background-color: #0a0a0a; 
            border: 1px solid #151515; 
            border-radius: 20px; 
            padding: 24px;
            max-width: 450px;
            margin: 40px auto;
        }

        /* Rank Badge */
        .rank-badge {
            background: linear-gradient(135deg, #facc15 0%, #ca8a04 100%);
            color: black;
            font-weight: 900;
            font-style: italic;
            padding: 4px 12px;
            border-radius: 6px;
            transform: skewX(-12deg);
        }

        /* Icon Fix - Using Masks to remove white background */
        .mc-icon {
            width: 20px;
            height: 20px;
            display: inline-block;
            background-color: currentColor; /* Yeh color tier ke hisaab se badlega */
            -webkit-mask-size: contain;
            mask-size: contain;
            -webkit-mask-repeat: no-repeat;
            mask-repeat: no-repeat;
            -webkit-mask-position: center;
            mask-position: center;
        }

        /* Specific Masks */
        .icon-sword { -webkit-mask-image: url('https://mctiers.com/tier_icons/sword.svg'); }
        .icon-vanilla { -webkit-mask-image: url('https://mctiers.com/tier_icons/vanilla.svg'); }
        .icon-pot { -webkit-mask-image: url('https://mctiers.com/tier_icons/pot.svg'); }
        .icon-uhc { -webkit-mask-image: url('https://mctiers.com/tier_icons/uhc.svg'); }

        .icon-circle {
            background: #111;
            border: 1px solid #222;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .line-sep { border: 0; border-top: 1px solid #1a1a1a; margin: 20px 0; }
    </style>
</head>
<body class="p-6">

    <div class="player-card">
        <div class="flex items-center gap-4 mb-4">
            <div class="rank-badge text-lg">1.</div>
            <img src="https://mc-heads.net/avatar/ItzReal/45" class="rounded-lg">
            <div>
                <h2 class="text-2xl font-bold tracking-tight">ItzReal...</h2>
                <p class="text-[10px] text-gray-600 font-bold uppercase tracking-widest">Combat Participant</p>
            </div>
        </div>

        <div class="line-sep"></div>

        <p class="text-[10px] font-black text-gray-700 uppercase mb-5 tracking-[0.2em]">Current Tiers</p>

        <div class="flex gap-5">
            <div class="flex flex-col items-center">
                <div class="icon-circle">
                    <span class="mc-icon icon-sword text-blue-400"></span>
                </div>
                <span class="text-[11px] font-bold mt-2 text-orange-500">HT3</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="icon-circle">
                    <span class="mc-icon icon-vanilla text-purple-400"></span>
                </div>
                <span class="text-[11px] font-bold mt-2 text-yellow-400">HT1</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="icon-circle">
                    <span class="mc-icon icon-pot text-pink-400"></span>
                </div>
                <span class="text-[11px] font-bold mt-2 text-yellow-400">HT1</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="icon-circle">
                    <span class="mc-icon icon-uhc text-red-500"></span>
                </div>
                <span class="text-[11px] font-bold mt-2 text-red-500">LT2</span>
            </div>
        </div>
    </div>

</body>
</html>
