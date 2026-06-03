import streamlit as st

# Set up page configuration
st.set_page_config(page_title="MCTiers Clone", page_icon="⚔️", layout="centered")

# Custom CSS for dark theme styling to match MCTiers
st.markdown("""
    <style>
    .main { background-color: #0f1319; color: #ffffff; }
    .player-card {
        background-color: #161c24;
        border-radius: 10px;
        padding: 15px;
        margin-bottom: 15px;
        border: 1px solid #232d3a;
    }
    .player-header { display: flex; align-items: center; justify-content: space-between; }
    .rank-name { display: flex; align-items: center; gap: 15px; }
    .rank { font-size: 24px; font-weight: bold; color: #ffb703; }
    .player-name { font-size: 22px; font-weight: bold; color: #ffffff; text-decoration: none; }
    .player-name:hover { color: #00b4d8; }
    .region { padding: 2px 8px; border-radius: 4px; font-weight: bold; font-size: 14px; }
    .region-na { background-color: #e63946; color: white; }
    .region-eu { background-color: #2a9d8f; color: white; }
    .tier-container { display: flex; flex-wrap: wrap; gap: 15px; margin-top: 15px; }
    .tier-box { text-align: center; background: #1c2530; padding: 8px; border-radius: 8px; width: 55px; }
    .tier-icon { width: 24px; height: 24px; }
    .tier-label { font-size: 11px; font-weight: bold; margin-top: 4px; }
    .ht { color: #f4a261; } /* High Tier color */
    .lt { color: #9a8c98; } /* Low Tier color */
    </style>
""", unsafe_allow_html=True)

# -------------------------------------------------------------------
# Mock Database with online icon URLs (Lucide SVGs used as standards)
# -------------------------------------------------------------------
icon_urls = {
    "sword": "https://unpkg.com/lucide-static@latest/icons/sword.svg",
    "netpot": "https://unpkg.com/lucide-static@latest/icons/shield.svg",  # Placeholder for netpot
    "pearl": "https://unpkg.com/lucide-static@latest/icons/orbit.svg",    # Placeholder for pearl
    "pot": "https://unpkg.com/lucide-static@latest/icons/flask-conical.svg",
    "mace": "https://unpkg.com/lucide-static@latest/icons/gavel.svg",
    "axe": "https://unpkg.com/lucide-static@latest/icons/axe.svg",
    "heart": "https://unpkg.com/lucide-static@latest/icons/heart.svg"
}

players_data = [
    {
        "rank": 1,
        "name": "ItzReal...",
        "region": "NA",
        "profile_url": "https://namemc.com/", # Replace with your documentation/stats link
        "tiers": [
            {"icon": icon_urls["sword"], "label": "HT3", "type": "ht"},
            {"icon": icon_urls["netpot"], "label": "HT1", "type": "ht"},
            {"icon": icon_urls["pearl"], "label": "HT1", "type": "ht"},
            {"icon": icon_urls["pot"], "label": "HT1", "type": "ht"},
            {"icon": icon_urls["mace"], "label": "LT2", "type": "lt"},
            {"icon": icon_urls["axe"], "label": "LT2", "type": "lt"},
            {"icon": icon_urls["heart"], "label": "LT2", "type": "lt"},
        ]
    },
    {
        "rank": 2,
        "name": "coldified",
        "region": "EU",
        "profile_url": "https://namemc.com/", # Replace with your documentation/stats link
        "tiers": [
            {"icon": icon_urls["mace"], "label": "LT1", "type": "lt"},
            {"icon": icon_urls["pot"], "label": "LT1", "type": "lt"},
            {"icon": icon_urls["netpot"], "label": "LT3", "type": "lt"},
            {"icon": icon_urls["heart"], "label": "HT1", "type": "ht"},
            {"icon": icon_urls["pearl"], "label": "HT1", "type": "ht"},
            {"icon": icon_urls["sword"], "label": "LT1", "type": "lt"},
            {"icon": icon_urls["axe"], "label": "LT1", "type": "lt"},
        ]
    }
]

# -------------------------------------------------------------------
# Web Layout
# -------------------------------------------------------------------
st.title("🛡️ MCTIERS LEADERBOARD")

# Search Bar Functionality
search_query = st.text_input("", placeholder="🔍 Search player...")

st.write("---")

# Filter and Render Players
filtered_players = [p for p in players_data if search_query.lower() in p["name"].lower()]

if not filtered_players:
    st.warning("No players found matches your search.")
else:
    for player in filtered_players:
        region_class = "region-na" if player["region"] == "NA" else "region-eu"
        
        # Start HTML Generation for Card
        card_html = f"""
        <div class="player-card">
            <div class="player-header">
                <div class="rank-name">
                    <span class="rank">{player['rank']}.</span>
                    <a class="player-name" href="{player['profile_url']}" target="_blank">{player['name']}</a>
                </div>
                <span class="region {region_class}">{player['region']}</span>
            </div>
            <div class="tier-container">
        """
        
        # Add Tiers / Items dynamically
        for tier in player["tiers"]:
            card_html += f"""
                <div class="tier-box">
                    <img src="{tier['icon']}" class="tier-icon" />
                    <div class="tier-label {tier['type']}">{tier['label']}</div>
                </div>
            """
            
        card_html += "</div></div>"
        
        # Render the custom HTML card into Streamlit
        st.markdown(card_html, unsafe_allow_html=True)
