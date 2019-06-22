# WoW-Classic-Quests

Base structure of the "quests" JSON file is as follows:

Key is QuestID

quests[x]["name"] = Quest Title

quests[x]["req"] = Minimum level required to pick up the quest

quests[x]["level"] = Quest level

quests[x]["objective"] = Text field with short objective explanation to finish quest

quests[x]["prev"] = Previous quest in Quest Chain

quests[x]["next"] = Next quest in Quest Chain

quests[x]["followup"] = Possible quest that opens up after finishing current quest (Like "The Hunt Completed (247)" after all Ashenvale Hunt quests)

quests[x]["reward"] = ItemIDs for rewards (includes both choices and guaranteed rewards, does not include gold reward)

quests[x]["repgain"] = {factionID: reputation gained}

Example:

    "893": # Quest ID 893
        {"name": "Weapons of Choice", # Name of quest

        "req": "17", # Minimum level: 17
        
        "level": "24", # Quest level: 24

        "objective": "Bring a Razormane Backstabber, a Charred Razormane Wand and a Razormane War Shield to Tatternack Steelforge at Camp Taurajo in the Barrens.", # Ingame objective explanation

        "reward": ["5322", "5323"], # Rewards: Demolition Hammer (5322) / Everglow Lantern (5323)

                                    # (Does not specify whether this is a choice or if both are gained.

                                    # Used for "which quest can I get this item from" inquiries.

        "repgain": {"76": "250"}} # 250 Orgrimmar rep gained

For reference, use "hettps://classic.wowhead.com/" followed by "item=123" for items, "quest=123" for quests, "faction=123" for factions.
