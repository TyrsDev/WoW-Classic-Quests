# WoW-Classic-Quests

Base structure of the "quests" JSON file is as follows:

Key is QuestID

quests[x]["name"] = Quest Title

quests[x]["req"] = Minimum level required to pick up the quest

quests[x]["level"] = Quest level

quests[x]["objective"] = Text field with short objective explanation to finish quest

quests[x]["source"] = List of all possible sources, NPC, Game Object, Item. Contains tuple with following position. 0: Source type ("npc", "object", "item"), 1: Source ID, 2: Name of source, and (if NPC or Game Object and has known spawn point) 3: Spawn information.

quests[x]["source"] = List of all possible sources, NPC and Game Object. Contains tuple with following position. 0: Source type ("npc", "object"), 1: Source ID, 2: Name of source, and (if has known spawn point) 3: Spawn information.

quests[x]["type"] = Shows the quest type like: "Group", "Raid", "Dungeon", "Escort, "World Event" (if nothing, it's a Solo quest)

quests[x]["classes"] = Array with all eligible classes (for functions like "if myclass in quests[x]["classes"]:")

quests[x]["races"] = Array with all eligible races (for functions like "if myrace in quests[x]["races"]:") (Use this to control Faction as well)

quests[x]["sort"] = Name of the Quest Tab the quest will appear under in the Quest Log. Most often Zone, but also Event, Class or Profession

quests[x]["prev"] = Previous quest in Quest Chain

quests[x]["next"] = Next quest in Quest Chain

quests[x]["followup"] = Possible quest that opens up after finishing current quest (Like "The Hunt Completed (247)" after all Ashenvale Hunt quests)

quests[x]["reward"] = ItemIDs for rewards (includes both choices and guaranteed rewards, does not include gold reward)

quests[x]["repgain"] = {factionID: reputation gained}

quests[x]["gather"] = ItemIDs needed to deliver the quest (objective)

quests[x]["kill"] = CreatureIDs that need to be killed to complete the quest (objective)

quests[x]["interact"] = GameObjectIDs that need to be interacted with to complete the quest (objective)

Example:
    
    "893": # Quest ID 893
    {'name': 'Weapons of Choice', # Name of quest
     'req': '17', # Minimum level: 17
     'level': '24', # Quest level: 24
     'objective': 'Bring a Razormane Backstabber, a Charred Razormane Wand and a Razormane War Shield to Tatternack Steelforge at Camp Taurajo in the Barrens.', # Ingame objective explanation
     'source': [('npc', # Source is an NPC
       '3433', # Source NPC ID
       'Tatternack Steelforge', # Source NPC Name
       {'map': 'Kalimdor', # Map name of first point this NPC spawns at (only one in this case)
        'positions': [{'mapid': '1', # Map ID for Kalimdor
          'x': '-2284.69', # X-coordinate for this spawn in Kalimdor
          'y': '-1947.39', # Y-coordinate for this spawn in Kalimdor
          'z': '96.0461'}]})], # Z-coordinate for this spawn in Kalimdor
     'deliver': [('npc', # Delivers to an NPC
       '3433', # ID of NPC to deliver to
       'Tatternack Steelforge', # Name of NPC to deliver to
       {'map': 'Kalimdor', # Map name of first point this NPC spawns at (only one in this case)
        'positions': [{'mapid': '1', # Map ID for Kalimdor
          'x': '-2284.69', # X-coordinate for this spawn in Kalimdor
          'y': '-1947.39', # Y-coordinate for this spawn in Kalimdor
          'z': '96.0461'}]})], # Z-coordinate for this spawn in Kalimdor
     'races': ['Troll', 'Tauren', 'Undead', 'Orc'], # Available for all Horde races!
     'sort': 'The Barrens', # Zone tab in Quest Log
     'reward': ['5322', '5323'], # Rewards: Demolition Hammer (5322) / Everglow Lantern (5323)
                                 # (Does not specify whether this is a choice or if both are gained.)
                                 # Used for "which quest can I get this item from" inquiries.
     'repgain': {'76': '250'} # 250 Orgrimmar (76) rep gained,
     'gather': ['5093', '5092', '5094']} # ItemID for a Razormane Backstabber, a Charred Razormane Wand and a Razormane War Shield
     
For reference, use "https://classic.wowhead.com/" followed by "item=123" for items, "quest=123" for quests, "npc=123" for NPCs, "faction=123" for factions, "object=123" for game objects.

_____________________________________________________________________

Base structure of the "questlocales" JSON file is as follows:

Key is QuestID

quests[x]["title_" + lang] = Localized Quest Title, change lang to "koKR", "frFR", "deDE", "zhCN", "esES", "esMX" or "ruRU".

quests[x]["objective_" + lang] = Localized Quest Objective, change lang to "koKR", "frFR", "deDE", "zhCN", "esES", "esMX" or "ruRU".

Languages: "koKR" (Korean), "frFR" (French), "deDE" (German), "zhCN" (Chinese), "esES" (Spanish, Spain), "esMX" (Spanish, Mexican) or "ruRU" (Russian).

Example:

    {'title_koKR': '최고의 무기', # Korean title
     'objective_koKR': None, # Korean objective
     'title_frFR': 'Des armes de choix', # French title
     'objective_frFR': 'Apporter un Eustache tranchecrin, une Baguette tranchecrin carbonisée et un Bouclier tranchecrin à Tatternack Forgacier au camp Taurajo dans les Tarides.', # French objective
     'title_deDE': 'Ausgewählte Waffen', # German title
     'objective_deDE': 'Bringt Tatternack Stahlformer im Camp Taurajo im Brachland einen Klingenmähnenrückenstecher, einen verkohlten Klingenmähnenzauberstab und einen Klingenmähnenkriegsschild.', # German objective
     'title_zhCN': '野猪人的武器', # Chinese title
     'objective_zhCN': '给陶拉祖营地的塔特纳克·钢炉带去一把钢鬃背刺匕首、一根烧焦的钢鬃魔杖和一面钢鬃大盾。', # Chinese objective
     'title_esES': 'Una selección de armas', # Spanish (Spain) title
     'objective_esES': 'Llévale 1 puñal Crines de Acero, 1 varita Crines de Acero carbonizada y 1 escudo de guerra Crines de Acero a Jironack Forjacero en Campamento Taurajo en Los Baldíos.', # Spanish (Spain) objective
     'title_esMX': 'Una selección de armas', # Spanish (Mexico) title
     'objective_esMX': 'Llévale 1 puñal Crines de Acero, 1 varita Crines de Acero carbonizada y 1 escudo de guerra Crines de Acero a Jironack Forjacero en Campamento Taurajo en Los Baldíos.', # Spanish (Mexico) objective
     'title_ruRU': 'Предпочитаемое оружие', # Russian title
     'objective_ruRU': 'Принесите стилет Иглогривых, обгоревший жезл Иглогривых и боевой щит Иглогривых Таттернаку Стальному Горну в Лагерь Таурахо в Степях.'} # Russian objective
