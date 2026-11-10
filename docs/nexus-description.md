# Nexus Mods page: Weightless Clothing

## Brief overview (the short summary field)

Every clothing item weighs 0, so your outfits stop eating carry capacity. One small TweakXL file: no scripts, no archives, nothing saved into your saves.

## Description (BBCode: paste into the editor's source/BBCode view)

```
[size=4][b]Weightless Clothing[/b][/size]

Every clothing item in the game weighs [b]0[/b]. Hoard as many outfits as you like without them eating your carry capacity.

It's a single small TweakXL file: no scripts, no archives, and nothing is written into your saves.

[size=3][b]Main features[/b][/size]
[list]
[*][b]All vanilla clothing weighs 0:[/b] all 2,074 clothing items, including Phantom Liberty clothing.
[*][b]Clothing only:[/b] weapons, cyberware, consumables and everything else keep their normal weight.
[*][b]Nothing saved:[/b] the change is applied each time the game starts, so it's safe to remove at any time. Delete the file and clothing goes back to its normal weight.
[/list]

[size=3][b]Requirements[/b][/size]
[list]
[*][url=https://www.nexusmods.com/cyberpunk2077/mods/2380]RED4ext[/url]
[*][url=https://www.nexusmods.com/cyberpunk2077/mods/4197]TweakXL[/url]
[/list]
Made on game version 2.5. Phantom Liberty isn't required.

[size=3][b]Installation[/b][/size]
[list=1]
[*]Install RED4ext and TweakXL first.
[*]Install this mod with Vortex or Mod Organizer 2, [b]or[/b] manually: extract the archive into your Cyberpunk 2077 game folder. The file should end up at:
[code]Cyberpunk 2077\r6\tweaks\zzWeightlessClothing\weightless_clothing.yaml[/code]
[*]Start the game. Hover any piece of clothing in your inventory: its weight should read 0.
[/list]

[b]Uninstall:[/b] delete the [i]zzWeightlessClothing[/i] folder, or disable the mod in your mod manager.

[size=3][b]Compatibility[/b][/size]
[list]
[*][b]Modded clothing[/b] weighs 0 too if it reuses the game's own clothing weight values. If a clothing mod gives its items their own weight, that weight stays.
[*][b]Other mods that change clothing weight:[/b] the one that loads last wins. This mod's folder starts with [i]zz[/i], so it normally loads last.
[*][b]Everything else[/b] is untouched.
[/list]

[size=3][b]How it works[/b] (for the curious)[/size]
The game doesn't store a weight on each clothing item. Every item adds up two shared values:
[list]
[*]one for its slot, e.g. outer torso +0.5;
[*]one for its garment type, e.g. jacket +2.5.
[/list]
So a jacket weighs 3.0. There are only 48 of these shared values across all 2,074 clothing items, and this mod sets each of them to 0.

The game itself already does the same for a few quest outfits, such as the Militech suit in The Heist and the diving suit.

The file is generated from the game's own database, with checks that every clothing item ends up at 0 and that nothing outside clothing is affected.

[size=3][b]Source[/b][/size]
Source and generator script: [url=https://github.com/thanapat1273/cyberpunk-weightless-clothes]github.com/thanapat1273/cyberpunk-weightless-clothes[/url] (MIT licence).

[size=3][b]Shout outs[/b][/size]
[list]
[*][b]psiberx[/b] for TweakXL (and ArchiveXL and Codeware)
[*][b]WopsS[/b] for RED4ext
[*]The [b]WolvenKit[/b] team and the [url=https://wiki.redmodding.org/cyberpunk-2077-modding]RED Modding wiki[/url] community, whose tools and docs made reading the game's data possible
[/list]

[i]Unofficial fan mod, not approved or endorsed by CD PROJEKT RED.[/i]
```

## Upload notes

- **The file to upload** is a zip whose root holds the `r6` folder:
  `r6\tweaks\zzWeightlessClothing\weightless_clothing.yaml`.
  That layout installs correctly with Vortex, MO2, or a manual extract.
- **Requirements tab:** add RED4ext (2380) and TweakXL (4197).
- **Permissions tab:** MIT, matching the GitHub repo.
