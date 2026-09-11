# Squirrel Variety Pack — where the content comes from, and what had to be changed

Everything in this mod is **SirTalis's** work: the six animals, their stats, their textures, their
biomes. This repository holds the port to RimWorld 1.6 and nothing else.

## The source

| | |
|---|---|
| Mod | Squirrel Variety Pack |
| Author | SirTalis |
| Workshop | [2737993245](https://steamcommunity.com/sharedfiles/filedetails/?id=2737993245) |
| Last version supported | 1.3 |
| Last updated | 10 February 2022 |
| Licence | none stated |

**Abandoned, not withdrawn.** The item is still on the Workshop and still downloadable; it stopped
at 1.3, missing 1.4, 1.5 and 1.6. Nobody else has picked it up: Mlie has no continuation of it, a
Workshop search filtered on the 1.6 tag returns nothing related, and no installed mod declares
`NAGraySquirrel`, `FlyingSquirrel` or `Groundhog`.

## The licence, looked for in four places

"None stated" is a verdict, not an absence of checking. A refusal never presents itself as a
licence, so each place was searched for the refusal rather than for the permission — `prohibit`,
`forbid`, `do not redistribute`, `no reupload`, `all rights reserved`, `without permission`, and
the Japanese and Chinese forms 禁止, 転載, 無断, 二次配布, 不得.

| Where | What it says |
|---|---|
| A `LICENSE` or `COPYING` file in the mod | there is none |
| The `<description>` of its `About.xml` | nothing about reuse |
| A linked repository | there is none |
| The Workshop page description | nothing about reuse |

Silence grants nothing and forbids nothing. This port rests on the Workshop's own custom for
abandoned mods: named credit, and a takedown on request.

## What the port changed

Three things, one of which is the reason this mod could not simply be re-tagged for 1.6.

- **`wildness` moved to `<Wildness>` under `statBases`, on all six animals.** It stopped being a
  field of `RaceProperties` in 1.6 and became a StatDef. The old form does not error: nothing reads
  it, and the stat's own default is `-1`, which Core's comment describes as deliberately out of range
  "so we can catch missing wildness stats on animals".
- **The gray squirrel's three coats left a dead DLL for vanilla.** They came from
  `AnimalVariations.dll` — `thingClass AnimalMultiSkins` plus a `NAGraySquirrel_SkinSet.xml` under
  `Textures/` — a library shipped with no sources that does not survive the render tree RimWorld
  moved to in 1.5. Vanilla has done the same job natively since 1.4, so the coats are declared as
  `alternateGraphics` with `alternateGraphicChance` 1 and the draw weights the SkinSet used: grey
  1.0, black 0.4, albino 0.005. **The assembly is not carried over at all**, which is the whole
  point: nothing here needs it.
- **The Nocturnal Animals patch fires for the first time.** It guarded on `[XND] Nocturnal Animals`,
  the mod's title from before Mlie took it over, so it matched nothing; and it added its extension
  directly under `<ThingDef>` rather than under `<modExtensions>`, which would not have worked had it
  matched. Both names are listed now, and the operation is `PatchOperationAddModExtension`.

A diff against the original files shows those changes and nothing else.

## What was left alone, and why

- **The biomes are the author's.** Each animal sits in one or two: boreal forest for the Douglas
  squirrel, arid shrubland for the southwestern red, temperate forest and swamp for the groundhog.
  The groundhog's own biome patch is carried as written.
- **The flying squirrel's 11.1 move speed and 250 silver** are not a mistake to correct. Neither is
  the groundhog's 1.2, which makes it slower than a walking colonist.
- **Their dessicated corpses use the base game's squirrel texture**, as the author wrote them.
- **No balance value was touched**, the coat weights included.

## Where this came from

The port was done inside a private pack that had gathered two dozen abandoned animal mods, where
these six were one source among them. They leave the pack to stand on their own, because the rule
that pack follows is that a mod which is dead **and** states nothing gets republished with credit
rather than kept back. The pack keeps only what cannot be published: sources that are alive in 1.6,
and the one whose author refuses redistribution.
