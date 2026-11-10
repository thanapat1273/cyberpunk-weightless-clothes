# Weightless Clothing

Every clothing item in Cyberpunk 2077 weighs 0. It's a data-only mod: one TweakXL YAML file, no scripts and no archives.

Built 2026-11-10 for game 2.x with Phantom Liberty, against the game's own `tweakdb_ep1.bin`.

## What it changes

Clothing weight is a `BaseStats.Weight` stat modifier in each clothing record's `statModifiers` list. The game doesn't give each item its own number; it shares a few modifiers:

| Layer | Example | Value |
|---|---|---|
| The slot's base record | `Items.OuterChestClothingBase_inline3` (all outer-torso clothing) | +0.5 |
| The garment type | `Items.Jacket_inline0` (all jackets) | +2.5 |

So a jacket weighs 0.5 + 2.5 = 3.0. Across all **2,074 clothing records**, there are only **48 non-zero `Additive` weight modifiers**. The mod sets each of them to 0.

From the game data:
- **45 clothing records** already have no weight modifier.
- **5 quest outfits** already use a vanilla `Multiplier` 0 on weight: the Militech blazer, pants and shoes from The Heist, and the diving suits. That's the game's own way of making clothing weightless.
- **The 48 edited modifiers are used by clothing records only,** so no weapon, cyberware or other item changes.

`tools/generate.py` checks both of these every time it writes the file.

## Files

| Path | What it is |
|---|---|
| `r6/tweaks/zzWeightlessClothing/weightless_clothing.yaml` | The mod: 48 entries like `Items.Jacket_inline0: { value: 0.0 }` |
| `tools/generate.py` | Rebuilds the YAML from the game's TweakDB and checks the result. Rerun it after a game patch: `python -I tools/generate.py`. It needs a TweakDB reader (`tweakdb.py`, not in this repo); set `TWEAKDB_READER` to its folder. |

## Install

Needs **RED4ext** and **TweakXL**.

Copy the `r6` folder into the game folder (`F:\SteamLibrary\steamapps\common\Cyberpunk 2077`), so the file ends up at:

`r6/tweaks/zzWeightlessClothing/weightless_clothing.yaml`

The `zz` prefix makes it load after other tweak mods.

**Uninstall:** delete that folder. Nothing is written into saves: TweakXL applies the change each time the game starts, so clothing goes back to its normal weight.

## Check that it works

1. **TweakXL log** (`red4ext/plugins/TweakXL/TweakXL-*.log`): a "Reading …weightless_clothing.yaml" line, then "Import completed" with no warnings.
2. **CET console** (one line; `error("flush")` makes the output reach `scripting.log`):
   ```lua
   print(TweakDB:GetFlat("Items.Jacket_inline0.value"), TweakDB:GetFlat("Items.OuterChestClothingBase_inline3.value"), TweakDB:GetFlat("Items.Pants_inline0.value")) error("flush")
   ```
   Expected: `0 0 0` (vanilla: `2.5 0.5 0.5`).
3. **In game:** open the inventory and hover a jacket you already own. The tooltip weight should be 0, and the carry weight shouldn't change when you pick up or drop clothing.

## Limits

- **Clothing from other mods** weighs 0 only if it reuses these vanilla modifiers. Clothing with its own weight modifier keeps its weight.
- **A game patch** could add new clothing types with new modifiers. Rerun `tools/generate.py`, then reinstall the YAML.
