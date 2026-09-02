# TDS Stats

Extracts complete player profile, progression, inventory, and game data in Tower Defense Simulator.

---

## Usage

```lua
local stats = loadstring(game:HttpGet("https://raw.githubusercontent.com/avtryxz/TDS-Stats/main/GetStats.lua"))()
```

> **Note:** Skill tree extraction only works while in the **Lobby**.

---

## Data Extracted

| Category | Description | Fields |
| :--- | :--- | :--- |
| **Player Profile** | Username, display name, user ID, and account age | `player.name`, `player.displayName`, `player.userId`, `player.accountAge` |
| **Membership** | VIP, VIP+, and Legacy VIP ownership | `membership.vip`, `membership.vipPlus`, `membership.legacyVip` |
| **Currencies** | Coins, gems, timescale tickets, revive tickets, and spin tickets | `currencies.coins`, `currencies.gems`, `currencies.timescaleTickets`, `currencies.reviveTickets`, `currencies.spinTickets` |
| **Game Modes** | Unlock status, min level, waves, boss, estimated time, and engine lock requirements | `gameModes.<modeName>.unlocked`, `gameModes.<modeName>.minLevel`, `gameModes.<modeName>.levelsNeeded`, `gameModes.<modeName>.waves`, `gameModes.<modeName>.boss`, `gameModes.<modeName>.estimatedTime`, `gameModes.<modeName>.specialRequirement` |
| **Spin Wheel** | Spin eligibility | `spinWheel.canSpin` |
| **Daily Login** | Login streak, claim status, and 7-day reward schedule | `dailyLogin.loginStreak`, `dailyLogin.currentDay`, `dailyLogin.claimedDay`, `dailyLogin.canClaimDaily`, `dailyLogin.schedule` |
| **Progression** | Level, XP, XP to next level, triumphs, wins, losses, total matches, win ratio, rank, tutorial, and medals | `progression.level`, `progression.experience`, `progression.requiredExp`, `progression.remainingExp`, `progression.triumphs`, `progression.wins`, `progression.loses`, `progression.totalMatches`, `progression.winRatio`, `progression.rank`, `progression.tutorial`, `progression.medals` |
| **Owned Towers** | Owned towers, equipped skins, golden variants, and evolved tower ownership | `ownedTowers`, `totalTowersOwned`, `goldenTowersOwned`, `evolvedTowersOwned` |
| **Inventory & Cosmetics** | Crates, consumables, flairs, stickers, equipped totem, nametag, and flair | `inventory.consumables`, `inventory.crates`, `inventory.flairs`, `inventory.stickers`, `inventory.equippedTotem`, `inventory.equippedTag`, `inventory.equippedFlair` |
| **Tower Purchases** | Tower shop prices, unlock levels, purchase requirements, and coins/gems needed | `towerPurchases.<towerName>.owned`, `towerPurchases.<towerName>.canPurchase`, `towerPurchases.<towerName>.price`, `towerPurchases.<towerName>.currency`, `towerPurchases.<towerName>.minLevel`, `towerPurchases.<towerName>.levelsNeeded`, `towerPurchases.<towerName>.currencyNeeded`, `towerPurchases.<towerName>.specialRequirement` |
| **Skill Tree** | Skill tree unlock status and unlocked skill node levels (lobby only) | `skills.skillTreeUnlocked`, `skills.skillsEnabled`, `skills.unlockedSkills` |
| **Evolution Progress** | Base tower XP, current level, XP needed to evolve, and evolved tower ownership | `evolvedProgression.<evolvedTowerName>.baseTower`, `evolvedProgression.<evolvedTowerName>.level`, `evolvedProgression.<evolvedTowerName>.experience`, `evolvedProgression.<evolvedTowerName>.requiredExp`, `evolvedProgression.<evolvedTowerName>.remainingExp`, `evolvedProgression.<evolvedTowerName>.owned` |
| **Trial & Modifier** | Active trial name, map, time remaining, next upcoming trial, rotation interval, and elevator modifier | `trials.unlocked`, `trials.minLevel`, `trials.levelsNeeded`, `trials.current.id`, `trials.current.modifier`, `trials.current.timeRemaining`, `trials.upcoming.id`, `trials.upcoming.modifier`, `trials.rotationIntervalHours`, `trials.modifiers` |
| **PVP & Loadout** | Equipped match towers and consumables, PVP stats, streak, cash, and tower pets | `pvpAndMatch.unlocked`, `pvpAndMatch.minLevel`, `pvpAndMatch.pvpWins`, `pvpAndMatch.streak`, `pvpAndMatch.equippedPvpTowers`, `pvpAndMatch.equippedTowerPets`, `loadout.equippedTowers`, `loadout.equippedConsumables`, `loadout.pets` |
| **Quests & Missions** | Daily quests, weekly quests, rotation missions, and active challenge event | `quests.daily`, `quests.weekly`, `quests.missions`, `challenge.name`, `challenge.map`, `challenge.expires` |
| **Logbook** | Discovered enemy count, total enemy count, and list of unlocked enemies | `logbook.enemiesFound`, `logbook.enemiesTotal`, `logbook.unlockedEnemies` |
| **Achievements** | Categorized achievements with titles, descriptions, objectives, and rewards | `achievements.Gamemodes`, `achievements.Hardcore`, `achievements.Damage`, `achievements.Towers`, `achievements.Triumph`, `achievements.Logbooks`, `achievements.Missions` |
| **Playtime Rewards** | Playtime gift claim status, next gift countdown, and video ad gift offers | `freePlaytimeRewards.canClaimAny`, `freePlaytimeRewards.readyToClaimCount`, `freePlaytimeRewards.nextRewardTimer`, `freePlaytimeRewards.gifts`, `freePlaytimeRewards.giftAds.canClaimAny`, `freePlaytimeRewards.giftAds.resetTimer`, `freePlaytimeRewards.giftAds.offers` |
| **Leaderboards** | Monthly top 50 triumphs and XP rank, score, minimum to enter, and score difference | `leaderboards.monthlyTriumphs.onLeaderboard`, `leaderboards.monthlyTriumphs.rank`, `leaderboards.monthlyTriumphs.currentScore`, `leaderboards.monthlyTriumphs.minimumToEnter`, `leaderboards.monthlyTriumphs.difference`, `leaderboards.monthlyExperience.onLeaderboard`, `leaderboards.monthlyExperience.rank`, `leaderboards.monthlyExperience.currentScore`, `leaderboards.monthlyExperience.minimumToEnter`, `leaderboards.monthlyExperience.difference` |
| **Max Account** | Maxed status, coins/gems tower ownership, missing towers, and max skill tree | `maxAccount.isMaxed`, `maxAccount.allTowersOwned`, `maxAccount.missingTowers`, `maxAccount.maxSkillTree` |

### Dynamic Keys

| Placeholder | Target Table | Values / Examples |
| :--- | :--- | :--- |
| `<modeName>` | `stats.gameModes` | `Easy`, `Intermediate`, `Molten`, `Fallen`, `Hardcore`, `Voidcore`, `Sandbox`, `Badlands`, `PizzaParty`, `PollutedWasteland` |
| `<towerName>` | `stats.towerPurchases` | `Scout`, `Sniper`, `Minigunner`, `CrookBoss`, `DJBooth`, `Commander`, `Farm`, `Ranger`, `Rocketeer`, `Turret`, etc. |
| `<evolvedTowerName>` | `stats.evolvedProgression` | `Operator`, `Enforcer`, `Kingpin`, `Juggernaut` |

> [!NOTE]
> Lowercase is also supported.

---

## Formulas

### Level XP Formula

Player XP requirements scale by **25 XP per level** and cap at **1,150 XP**:

```math
\mathrm{RequiredXP} = \min\left(1150,\; (L + 1) \times 25\right)
```

```math
\mathrm{RemainingXP} = \max\left(0,\; \mathrm{RequiredXP} - \mathrm{XP}\right)
```

#### Example

For a player at **Level 100** with **400 XP**:

```math
\mathrm{RequiredXP} = \min\left(1150,\; (100 + 1) \times 25\right) = 1150
```

```math
\mathrm{RemainingXP} = 1150 - 400 = 750 \quad (\text{XP needed for Level 101})
```

### Win Ratio Formula

Win ratio is calculated using the official TDS client formula:

```math
\mathrm{WinRatio} = \frac{\mathrm{Triumphs}}{\max(1,\; \mathrm{Loses})}
```

#### Example

For a player with **4 Triumphs** and **2 Losses**:

```math
\mathrm{WinRatio} = \frac{4}{\max(1,\; 2)} = \frac{4}{2} = 2.00
```

### Evolved Tower XP Formula

Experience required for each level of an evolved tower scales exponentially using static constants (`BaseExp` and `GrowthRate`) defined in the game files for each tower:

```math
\mathrm{LevelCost}(i) = \left\lfloor \mathrm{BaseExp} \times \left(\mathrm{GrowthRate}\right)^{i - 1} \right\rfloor
```

```math
\mathrm{TotalRequiredXP} = \sum_{i=1}^{\mathrm{MaxLevel}} \mathrm{LevelCost}(i)
```

Where:
- $i$ is the evolution level number (from 1 to $\mathrm{MaxLevel}$).
- $\mathrm{BaseExp}$ is the base experience required for Level 1 ($50\text{ XP}$).
- $\mathrm{GrowthRate}$ is the compound scaling multiplier per level ($1.09$).
- $\mathrm{MaxLevel}$ is the maximum evolution level ($20$).
- $\mathrm{LevelCost}(i)$ is the individual XP required to advance through level $i$.
- $\mathrm{TotalRequiredXP}$ is the cumulative XP needed from Level 0 to max evolution ($2549\text{ XP}$).

#### Example

For an evolved tower with $\mathrm{BaseExp} = 50$, $\mathrm{GrowthRate} = 1.09$, and $\mathrm{MaxLevel} = 20$:

1. **Level 1 Cost**:
```math
\mathrm{LevelCost}(1) = \lfloor 50 \times 1.09^0 \rfloor = 50\text{ XP}
```

2. **Level 2 Cost**:
```math
\mathrm{LevelCost}(2) = \lfloor 50 \times 1.09^1 \rfloor = 54\text{ XP}
```

3. **Total XP Needed to Reach Max Level (Level 20)**:
```math
\mathrm{TotalRequiredXP} = 50 + 54 + 59 + \dots + 257 = 2549\text{ XP}
```

### Trial Elevator Rotation Formula

The active trial modifier and countdown rotate deterministically across global 3-hour (10,800 seconds) UTC intervals:

```math
\mathrm{EndsAt} = \left(\left\lfloor \frac{\mathrm{UnixTime}}{10800} \right\rfloor + 1\right) \times 10800
```

```math
\mathrm{SecondsRemaining} = \max\left(0,\; \mathrm{EndsAt} - \mathrm{UnixTime}\right)
```

```math
\mathrm{RotationIndex} = \left(\left\lfloor \frac{\mathrm{UnixTime}}{10800} \right\rfloor \bmod N\right) + 1
```

Where:
- $\mathrm{UnixTime}$ is the current timestamp in seconds.
- $N$ is the total number of trial modifiers in the rotation pool ($N = 13$).
- $\mathrm{RotationIndex}$ is the 1-based index pointing to the active modifier.

#### Rotation Order Pool ($N = 13$)

TDS sorts all trial definitions alphabetically to form the global rotation pool:

| Index | Identifier | Title | Map |
| :---: | :--- | :--- | :--- |
| **1** | `Broke` | Broke | Medieval Times |
| **2** | `Committed` | Committed | Retro Zone |
| **3** | `ExplodingEnemies` | Exploding Enemies | Wrecked Battlefield II |
| **4** | `FlyingEnemies` | Flying Enemies | Sacred Mountains |
| **5** | `Fog` | Fog | Winter Abyss |
| **6** | `Glass` | Glass | Stained Temple |
| **7** | `HealthyEnemies` | Healthy Enemies | Four Seasons |
| **8** | `HiddenEnemies` | Hidden Enemies | Forgetten Docks |
| **9** | `Inflation` | Inflation | Cyber City |
| **10** | `Jailed` | Jailed | Night Station |
| **11** | `Limitation` | Limitation | Coral Deep |
| **12** | `Quarantine` | Quarantine | Dusty Bridges |
| **13** | `SpeedyEnemies` | Speedy Enemies | Wrecked Battlefield |

#### Example

If the current time is **11:48:49 UTC** (`1788421729`) with all **13 trial modifiers** ($N = 13$):

1. **Next Rotation Timestamp**:
```math
\mathrm{EndsAt} = \left(\left\lfloor \frac{1788421729}{10800} \right\rfloor + 1\right) \times 10800 = 1788426000 \quad (13:00:00\text{ UTC})
```

2. **Time Remaining Until Next Trial**:
```math
\mathrm{SecondsRemaining} = 1788426000 - 1788421729 = 4271\text{ seconds} \quad (\text{01:11:11})
```

3. **Active Trial Selection**:
```math
\mathrm{RotationIndex} = (165594 \bmod 13) + 1 = 0 + 1 = 1 \quad (\text{Index 1: Broke is active})
```

4. **Next Upcoming Trial**:
```math
\mathrm{UpcomingIndex} = (1 \bmod 13) + 1 = 2 \quad (\text{Index 2: Committed is upcoming})
```

---

## Examples

<details>
<summary><b>1. Player Profile & Membership</b></summary>

```lua
print("Name:", stats.player.name, "DisplayName:", stats.player.displayName)
print("UserId:", stats.player.userId, "AccountAge:", stats.player.accountAge)
print("VIP:", stats.membership.vip, "VIP+:", stats.membership.vipPlus, "Legacy VIP:", stats.membership.legacyVip)
```
</details>

<details>
<summary><b>2. Game Modes & Unlock Requirements</b></summary>

```lua
local hardcore = stats.gameModes.Hardcore
if hardcore.unlocked then
    print("Hardcore is unlocked! Waves:", hardcore.waves, "Boss:", hardcore.boss)
else
    print("Hardcore locked, needs:", hardcore.levelsNeeded, "levels")
end

for modeName, gameMode in pairs(stats.gameModes) do
    if gameMode.unlocked then
        local waveText = tostring(gameMode.waves)
        local bossText = tostring(gameMode.boss)
        print(modeName, "is unlocked (level " .. gameMode.minLevel .. ", waves " .. waveText .. ", boss " .. bossText .. ")")
    else
        local requirementText = gameMode.specialRequirement and (", requires " .. gameMode.specialRequirement) or ""
        print(modeName, "is locked (level " .. gameMode.minLevel .. ", needs " .. gameMode.levelsNeeded .. " levels" .. requirementText .. ")")
    end
end
```
</details>

<details>
<summary><b>3. Spin Wheel & Daily Login Rewards</b></summary>

```lua
print("Can spin wheel:", stats.spinWheel.canSpin)
print("Login streak:", stats.dailyLogin.loginStreak, "days")
print("Current day:", stats.dailyLogin.currentDay, "claimed day:", stats.dailyLogin.claimedDay, "can claim:", stats.dailyLogin.canClaimDaily)

for _, reward in ipairs(stats.dailyLogin.schedule) do
    local status = reward.canClaim and "ready to claim" or (reward.claimed and "claimed" or "upcoming")
    print("Day " .. reward.day .. " (" .. status .. "): " .. reward.amount .. " " .. reward.name .. " (" .. reward.type .. ")")
end
```
</details>

<details>
<summary><b>4. Currencies & Progression</b></summary>

```lua
print("Coins:", stats.currencies.coins, "Gems:", stats.currencies.gems)
print("Tickets (Timescale/Revive/Spin):", stats.currencies.timescaleTickets, stats.currencies.reviveTickets, stats.currencies.spinTickets)
print("Level:", stats.progression.level, "XP:", stats.progression.experience, "/", stats.progression.requiredExp, "(Remaining:", stats.progression.remainingExp, ")")
print("Wins:", stats.progression.wins, "Losses:", stats.progression.loses, "Triumphs:", stats.progression.triumphs, "Rank:", stats.progression.rank)
print("Total Matches:", stats.progression.totalMatches, "Win Ratio:", stats.progression.winRatio)
print("Tutorial:", stats.progression.tutorial)
print("Medals (Normal/Easy/Insane):", stats.progression.medals.normal, stats.progression.medals.easy, stats.progression.medals.insane)
```
</details>

<details>
<summary><b>5. Towers & Variants</b></summary>

```lua
print("Total Towers:", stats.totalTowersOwned)
print("Golden Towers:", table.concat(stats.goldenTowersOwned, ", "))
print("Evolved Towers:", table.concat(stats.evolvedTowersOwned, ", "))
for towerName, towerInfo in pairs(stats.ownedTowers) do
    print(towerName, towerInfo.skin, towerInfo.golden, towerInfo.evolved, towerInfo.equipped)
end
```
</details>

<details>
<summary><b>6. Tower Shop & Purchase Status</b></summary>

```lua
local minigunner = stats.towerPurchases.Minigunner
if minigunner.owned then
    print("Minigunner is owned")
elseif minigunner.canPurchase then
    print("Minigunner can be purchased for", minigunner.price, minigunner.currency)
else
    print("Minigunner needs", minigunner.currencyNeeded, minigunner.currency, "and", minigunner.levelsNeeded, "levels")
end

for towerName, towerPurchase in pairs(stats.towerPurchases) do
    if towerPurchase.owned then
        print(towerName, "is already owned")
    elseif towerPurchase.canPurchase then
        print(towerName, "can be purchased for", towerPurchase.price, towerPurchase.currency)
    else
        print(towerName, "cannot be purchased (needs", towerPurchase.currencyNeeded, towerPurchase.currency, "and", towerPurchase.levelsNeeded, "levels)")
    end
end
```
</details>

<details>
<summary><b>7. Inventory, Crates, Stickers & Flairs</b></summary>

```lua
print("Equipped Totem:", stats.inventory.equippedTotem, "Equipped Tag:", stats.inventory.equippedTag, "Equipped Flair:", stats.inventory.equippedFlair)
print("Flairs:", table.concat(stats.inventory.flairs, ", "))
for consumableName, consumableCount in pairs(stats.inventory.consumables) do
    print("Consumable:", consumableName, consumableCount)
end
for crateName, crateCount in pairs(stats.inventory.crates) do
    if crateCount > 0 then
        print("Crate:", crateName, crateCount)
    end
end
for stickerName, stickerInfo in pairs(stats.inventory.stickers) do
    print("Sticker:", stickerName, stickerInfo.Equipped, stickerInfo.Sorting)
end
```
</details>

<details>
<summary><b>8. Skill Tree (Lobby Only)</b></summary>

```lua
print("Skill Tree Unlocked:", stats.skills.skillTreeUnlocked, "Skills Enabled:", stats.skills.skillsEnabled)
for skillName, skillLevel in pairs(stats.skills.unlockedSkills) do
    print(skillName, skillLevel)
end
```
</details>

<details>
<summary><b>9. Evolved Tower Progression</b></summary>

```lua
local operator = stats.evolvedProgression.Operator
if operator then
    print("Operator Level:", operator.level .. "/" .. operator.maxLevel, "XP Needed:", operator.remainingExp)
end

for evolvedTowerName, progressionInfo in pairs(stats.evolvedProgression) do
    print(
        evolvedTowerName,
        progressionInfo.baseTower,
        "Level:", progressionInfo.level .. "/" .. progressionInfo.maxLevel,
        "XP:", progressionInfo.experience .. "/" .. progressionInfo.requiredExp,
        "Owned:", progressionInfo.owned
    )
end
```
</details>

<details>
<summary><b>10. Trials Rotation & Modifiers</b></summary>

```lua
print("Trials unlocked:", stats.trials.unlocked, "(min level:", stats.trials.minLevel, "needs:", tostring(stats.trials.levelsNeeded) .. ")")
print("Current:", stats.trials.current.id, stats.trials.current.modifier, stats.trials.current.map, stats.trials.current.timeRemaining)
print("Upcoming:", stats.trials.upcoming.id, stats.trials.upcoming.modifier, stats.trials.upcoming.map)
for modifierName, modifierValue in pairs(stats.trials.modifiers) do
    print("Modifier:", modifierName, modifierValue)
end
```
</details>

<details>
<summary><b>11. Loadout & PVP Match Stats</b></summary>

```lua
print("PVP unlocked:", stats.pvpAndMatch.unlocked, "(min level:", stats.pvpAndMatch.minLevel, "needs:", stats.pvpAndMatch.levelsNeeded .. ")")
print("Equipped Towers:", table.concat(stats.loadout.equippedTowers, ", "))
print("Equipped Consumables:", table.concat(stats.loadout.equippedConsumables, ", "))
print("PVP Wins:", stats.pvpAndMatch.pvpWins, "Losses:", stats.pvpAndMatch.pvpLosses)
print("PVP Equipped:", table.concat(stats.pvpAndMatch.equippedPvpTowers, ", "))
print("PVP Consumables:", table.concat(stats.pvpAndMatch.equippedPvpConsumables, ", "))
print("Maps Cleared:", stats.pvpAndMatch.mapsCleared, "Streak:", stats.pvpAndMatch.streak, "Cash:", stats.pvpAndMatch.cash)
```
</details>

<details>
<summary><b>12. Quests, Missions & Challenge</b></summary>

```lua
if stats.challenge then
    print("Challenge:", stats.challenge.name, stats.challenge.map, stats.challenge.completed, stats.challenge.expires)
end
for _, dailyQuest in ipairs(stats.quests.daily) do
    print("Daily:", dailyQuest.id, dailyQuest.name, dailyQuest.description, dailyQuest.objectiveMode)
    for _, reward in ipairs(dailyQuest.rewards) do
        print("  Reward:", reward.type, reward.amount or reward.skin or reward.crate)
    end
end
for _, weeklyQuest in ipairs(stats.quests.weekly) do
    print("Weekly:", weeklyQuest.id, weeklyQuest.name, weeklyQuest.description, weeklyQuest.objectiveMode)
    for _, reward in ipairs(weeklyQuest.rewards) do
        print("  Reward:", reward.type, reward.amount or reward.skin or reward.crate)
    end
end
for _, missionQuest in ipairs(stats.quests.missions) do
    print("Mission:", missionQuest.id, missionQuest.name, missionQuest.price, missionQuest.currency, missionQuest.description)
    for _, reward in ipairs(missionQuest.rewards) do
        print("  Reward:", reward.type, reward.amount or reward.skin or reward.crate)
    end
end
```
</details>

<details>
<summary><b>13. Logbook & Bestiary</b></summary>

```lua
print("Enemies Found:", stats.logbook.enemiesFound, "/", stats.logbook.enemiesTotal)
print("Unlocked Enemies:", table.concat(stats.logbook.unlockedEnemies, ", "))
```
</details>

<details>
<summary><b>14. Achievements & Rewards</b></summary>

```lua
for categoryName, categoryList in pairs(stats.achievements) do
    print("Category:", categoryName)
    for achievementIdentifier, achievement in pairs(categoryList) do
        print("  Achievement:", achievement.title, "-", achievement.description)
        for _, reward in ipairs(achievement.rewards) do
            print("    Reward:", reward.type, reward.amount or reward.name)
        end
    end
end
```
</details>

<details>
<summary><b>15. Free Playtime Rewards & Timers</b></summary>

```lua
print("Can claim playtime gifts:", stats.freePlaytimeRewards.canClaimAny, "(ready:", stats.freePlaytimeRewards.readyToClaimCount .. ")")
if stats.freePlaytimeRewards.nextRewardTimer then
    print("Next gift in:", stats.freePlaytimeRewards.nextRewardTimer)
end
for _, gift in ipairs(stats.freePlaytimeRewards.gifts) do
    if gift.canClaim then
        print("Gift " .. gift.index .. " (" .. gift.quantity .. "): ready to claim")
    elseif gift.claimed then
        print("Gift " .. gift.index .. " (" .. gift.quantity .. "): already claimed")
    else
        print("Gift " .. gift.index .. " (" .. gift.quantity .. "): unlocks in " .. (gift.timeRemaining or "n/a"))
    end
end

local giftAds = stats.freePlaytimeRewards.giftAds
print("Gift ads can claim:", giftAds.canClaimAny, "(ready:", giftAds.readyToClaimCount .. ")", "reset in:", giftAds.resetTimer)
for _, giftOffer in ipairs(giftAds.offers) do
    print("Gift ad offer " .. giftOffer.offer .. ":", giftOffer.status:lower(), "(can claim:", giftOffer.canClaim .. ")")
end
```
</details>

<details>
<summary><b>16. Monthly Leaderboards & Rank Cutoff</b></summary>

```lua
local monthlyTriumphs = stats.leaderboards.monthlyTriumphs
print("Triumphs on leaderboard:", monthlyTriumphs.onLeaderboard, "Rank:", monthlyTriumphs.rank)
print("Current score:", monthlyTriumphs.currentScore, "Top 50 score:", monthlyTriumphs.minimumToEnter, "Difference:", monthlyTriumphs.difference)

local monthlyExperience = stats.leaderboards.monthlyExperience
print("Experience on leaderboard:", monthlyExperience.onLeaderboard, "Rank:", monthlyExperience.rank)
print("Current score:", monthlyExperience.currentScore, "Top 50 score:", monthlyExperience.minimumToEnter, "Difference:", monthlyExperience.difference)
```
</details>

<details>
<summary><b>17. Max Account Status</b></summary>

```lua
local maxAccount = stats.maxAccount
print("Is Maxed Account:", maxAccount.isMaxed)
print("All Shop Towers Owned:", maxAccount.allTowersOwned)
if not maxAccount.allTowersOwned then
    print("Missing (" .. #maxAccount.missingTowers .. "):", table.concat(maxAccount.missingTowers, ", "))
end
print("Max Skill Tree:", maxAccount.maxSkillTree)
```
</details>

---

## Data Structure

```lua
type Stats = {
    player: {
        name: string,
        displayName: string,
        userId: number,
        accountAge: number
    },
    membership: {
        vip: boolean,
        vipPlus: boolean,
        legacyVip: boolean
    },
    spinWheel: {
        canSpin: boolean
    },
    dailyLogin: {
        loginStreak: number,
        currentDay: number,
        claimedDay: number,
        canClaimDaily: boolean,
        schedule: {
            {
                day: number,
                type: string,
                name: string,
                amount: number,
                claimed: boolean,
                canClaim: boolean
            }
        }
    },
    gameModes: {
        [string]: {
            unlocked: boolean,
            minLevel: number,
            levelsNeeded: number,
            waves: number?,
            boss: string?,
            estimatedTime: number?,
            specialRequirement: string?
        }
    },
    currencies: {
        coins: number,
        gems: number,
        timescaleTickets: number,
        reviveTickets: number,
        spinTickets: number
    },
    progression: {
        level: number,
        experience: number,
        requiredExp: number,
        remainingExp: number,
        triumphs: number,
        wins: number,
        loses: number,
        totalMatches: number,
        winRatio: number,
        rank: number,
        tutorial: number,
        medals: {
            normal: number,
            easy: number,
            insane: number
        }
    },
    skills: {
        skillTreeUnlocked: boolean,
        skillsEnabled: boolean,
        note: string?,
        unlockedSkills: {
            [string]: number
        }
    },
    evolvedProgression: {
        [string]: {
            baseTower: string,
            level: number,
            experience: number,
            requiredExp: number,
            remainingExp: number,
            maxLevel: number,
            baseExp: number,
            growthRate: number,
            owned: boolean
        }
    },
    trials: {
        unlocked: boolean,
        minLevel: number,
        levelsNeeded: number,
        current: {
            id: string,
            modifier: string,
            title: string,
            map: string,
            description: string,
            timeRemaining: string
        },
        upcoming: {
            id: string,
            modifier: string,
            title: string,
            map: string,
            description: string
        },
        rotationIntervalHours: number,
        modifiers: { [string]: any }
    },
    pvpAndMatch: {
        unlocked: boolean,
        minLevel: number,
        levelsNeeded: number,
        pvpWins: number,
        pvpLosses: number,
        mapsCleared: number,
        streak: number,
        cash: number,
        econ: number,
        luck: number,
        equippedPvpTowers: { string },
        equippedPvpConsumables: { string },
        equippedTowerPets: { [string]: any }
    },
    loadout: {
        equippedTowers: { string },
        equippedConsumables: { string },
        pets: { [string]: any }
    },
    ownedTowers: {
        [string]: {
            skin: string,
            golden: boolean,
            evolved: boolean,
            equipped: boolean
        }
    },
    totalTowersOwned: number,
    goldenTowersOwned: { string },
    evolvedTowersOwned: { string },
    towerPurchases: {
        [string]: {
            owned: boolean,
            canPurchase: boolean,
            price: number,
            currency: string,
            minLevel: number,
            levelsNeeded: number,
            currencyNeeded: number,
            specialRequirement: string?
        }
    },
    inventory: {
        consumables: { [string]: number },
        crates: { [string]: number },
        flairs: { string },
        stickers: { [string]: { Equipped: boolean, Sorting: number } },
        equippedTotem: string,
        equippedTag: string,
        equippedFlair: string
    },
    challenge: {
        name: string,
        map: string,
        completed: boolean,
        expires: number
    }?,
    quests: {
        daily: {
            {
                id: string,
                name: string,
                description: string,
                objectiveMode: string,
                rewards: {
                    {
                        type: string,
                        amount: number?,
                        tower: string?,
                        skin: string?,
                        crate: string?
                    }
                }
            }
        },
        weekly: {
            {
                id: string,
                name: string,
                description: string,
                objectiveMode: string,
                rewards: {
                    {
                        type: string,
                        amount: number?,
                        tower: string?,
                        skin: string?,
                        crate: string?
                    }
                }
            }
        },
        missions: {
            {
                id: string,
                name: string,
                description: string,
                price: number,
                currency: string,
                rewards: {
                    {
                        type: string,
                        amount: number?,
                        tower: string?,
                        skin: string?,
                        crate: string?
                    }
                }
            }
        }
    },
    logbook: {
        enemiesFound: number,
        enemiesTotal: number,
        note: string?,
        unlockedEnemies: { string }
    },
    achievements: {
        [string]: {
            [string]: {
                id: string,
                title: string,
                description: string,
                hidden: boolean,
                flair: string?,
                lockedBehind: string?,
                objective: { [string]: any }?,
                rewards: {
                    {
                        type: string,
                        amount: number?,
                        name: string?
                    }
                }
            }
        }
    },
    freePlaytimeRewards: {
        canClaimAny: boolean,
        readyToClaimCount: number,
        nextRewardTimer: string?,
        note: string?,
        gifts: {
            {
                index: number,
                canClaim: boolean,
                claimed: boolean,
                timeRemaining: string?,
                quantity: string
            }
        },
        giftAds: {
            canClaimAny: boolean,
            readyToClaimCount: number,
            resetTimer: string?,
            offers: {
                {
                    offer: number,
                    canClaim: boolean,
                    claimed: boolean,
                    status: string
                }
            }
        }
    },
    leaderboards: {
        monthlyTriumphs: {
            onLeaderboard: boolean,
            rank: number?,
            currentScore: number,
            minimumToEnter: number,
            difference: number
        },
        monthlyExperience: {
            onLeaderboard: boolean,
            rank: number?,
            currentScore: number,
            minimumToEnter: number,
            difference: number
        }
    },
    maxAccount: {
        isMaxed: boolean,
        allTowersOwned: boolean,
        missingTowers: { string },
        maxSkillTree: boolean
    }
}
```
