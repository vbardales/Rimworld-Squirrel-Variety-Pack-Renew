# Squirrel Variety Pack Renew

Six small woodland animals, brought forward to RimWorld 1.6.

**I am not the author of this mod.** All six are SirTalis's; all I did was the work needed to make
them run on 1.6. Credit goes to them, mistakes in the update are mine.

Original mod: https://steamcommunity.com/sharedfiles/filedetails/?id=2737993245 — last supporting
1.3, last updated in February 2022. Abandoned, not withdrawn.

## What the mod does

Six animals, each in its own biome rather than scattered everywhere.

| Animal | Where | Notable |
|---|---|---|
| North American gray squirrel | temperate and boreal forest | three coats: grey, black, white |
| Douglas squirrel | boreal forest | |
| Pine squirrel | boreal and temperate forest | |
| Southwestern red squirrel | arid shrubland | |
| Flying squirrel | temperate forest | 11.1 move speed, 250 silver |
| Groundhog | temperate forest and swamp | body size 0.3, fourteen years, move speed 1.2 |

The white gray squirrel is drawn at **half a percent**, against 1.0 for the grey and 0.4 for the
black: an albino is meant to be a surprise.

If **[XND] Nocturnal Animals** is installed, the flying squirrel hunts at night. Without it, nothing
happens and nothing complains.

No DLC required. No Harmony, no framework, no dependency of any kind — and, unlike the original, no
assembly either.

Content mod: removing it mid-save will lose any of these six animals already in play.

## What changed in the 1.6 update

- **`wildness` moved to `<Wildness>` under `statBases`, on all six.** It stopped being a field of
  `RaceProperties` in 1.6 and became a StatDef. The old form is not an error, it is simply never
  read, and the stat's default is `-1` — outside the range the game uses, so all six tamed for almost
  nothing.
- **The gray squirrel's three coats left a dead DLL for vanilla.** They came from
  `AnimalVariations.dll`, shipped without sources, which does not survive the render tree RimWorld
  moved to in 1.5. Vanilla has done the same job natively since 1.4: the coats are `alternateGraphics`
  now, with the weights the old SkinSet file used. The assembly is not carried over at all.
- **The Nocturnal Animals patch fires for the first time.** It guarded on the mod's title from before
  Mlie took it over, so it never matched; and it added its extension in the wrong place, which would
  not have worked had it matched.

No balance value was changed, coat weights included.

## Terms

The original **states no licence anywhere** — no file in the mod, nothing in its `About.xml`, no
linked repository, and nothing on its Workshop page, which was read looking for a refusal rather
than for a permission. Silence grants nothing and forbids nothing.

This port rests on the Workshop's own custom for abandoned mods: named credit, and a takedown on
request. If SirTalis comes back to it, or asks for this to be taken down, it comes down.

If I do not answer within a reasonable time after being contacted, anyone may freely update this or
any other of my mods, including publishing a continuation of it. All credit must be preserved.

## Credits

- **SirTalis** — the mod, all six animals, and their textures.
- 1.6 update by nelim. Written with the help of Claude (Anthropic).

See [ATTRIBUTION.md](ATTRIBUTION.md) for the licence check and the port in detail.
