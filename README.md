<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCTIERS | Pro Rankings</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        body { background-color: #000000; color: #ffffff; font-family: sans-serif; }

        /* Card Style */
        .player-card { 
            background-color: #0d0d0d; 
            border: 1px solid #1a1a1a; 
            border-radius: 20px; 
            padding: 24px;
            max-width: 450px;
            margin: 40px auto;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* Rank Box */
        .rank-box {
            background: linear-gradient(135deg, #facc15 0%, #ca8a04 100%);
            color: black;
            font-weight: 900;
            font-style: italic;
            padding: 4px 12px;
            border-radius: 6px;
            transform: skewX(-12deg);
        }

        /* Icon Container */
        .tier-circle {
            background: #151515;
            border: 1px solid #222;
            border-radius: 50%;
            width: 42px;
            height: 42px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: 0.3s;
        }

        /* Icon Image Fix */
        .tier-circle img {
            width: 22px;
            height: 22px;
            object-fit: contain;
            /* Isse white background transparent feel hota hai */
            filter: drop-shadow(0 0 2px rgba(255,255,255,0.1));
        }

        .tier-label { font-size: 11px; font-weight: bold; margin-top: 6px; }
        .line-sep { border: 0; border-top: 1px solid #1a1a1a; margin: 20px 0; }
    </style>
</head>
<body class="p-6">

    <div class="player-card">
        <div class="flex items-center gap-4 mb-2">
            <div class="rank-box text-lg">1.</div>
            <img src="https://mc-heads.net/avatar/ItzReal/45" class="rounded-lg shadow-lg">
            <div>
                <h2 class="text-2xl font-bold tracking-tight">ItzReal...</h2>
                <p class="text-[10px] text-gray-600 font-black uppercase tracking-widest">Combat Participant</p>
            </div>
        </div>

        <div class="line-sep"></div>

        <p class="text-[10px] font-bold text-gray-700 uppercase mb-5 tracking-widest">Current Tiers</p>

        <div class="flex gap-4 flex-wrap">
            <div class="flex flex-col items-center">
                <div class="tier-circle">
                    <img src="https://mctiers.com/tier_icons/sword.svg" alt="sword">
                </div>
                <span class="tier-label text-orange-500">HT3</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="tier-circle">
                    <img src="https://mctiers.com/tier_icons/vanilla.svg" alt="vanilla">
                </div>
                <span class="tier-label text-yellow-400">HT1</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="tier-circle">
                    <img src="https://mctiers.com/tier_icons/pot.svg" alt="pot">
                </div>
                <span class="tier-label text-yellow-400">HT1</span>
            </div>

            <div class="flex flex-col items-center">
                <div class="tier-circle">
                    <img src="https://mctiers.com/tier_icons/uhc.svg" alt="uhc">
                </div>
                <span class="tier-label text-red-500">LT2</span>
            </div>
        </div>
    </div>

</body>
</html>
