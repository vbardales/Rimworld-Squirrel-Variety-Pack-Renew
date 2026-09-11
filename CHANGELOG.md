# Changelog

Format inspired by [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
This file serves the repository and the writing of Steam patch notes; RimWorld does not display it
in game.

## [1.0.0] — unreleased

On release: add `Mod/About/ModIcon.png` and `Mod/About/Preview.png`, create the `v1.0.0` tag and
the matching GitHub release, then publish to the Workshop.

First release of the 1.6 update of **Squirrel Variety Pack**, by SirTalis.

### Fixed

- **The Nocturnal Animals patch fires for the first time.** It guarded on `[XND] Nocturnal Animals`,
  the mod's title from before Mlie took it over, so it matched nothing — and it added its extension
  directly under `<ThingDef>` instead of under `<modExtensions>`, which would not have worked had it
  matched. Both names are guarded on now, through `PatchOperationAddModExtension`.

### Changed

- **`wildness` moved to `<Wildness>` under `statBases`, on all six animals.** It stopped being a
  field of `RaceProperties` in 1.6 and became a StatDef. The old form is not an error, it is simply
  never read, and the stat's default is `-1` — outside the range the game uses, so all six tamed for
  almost nothing.
- **The gray squirrel's three coats are vanilla `alternateGraphics` now.** They came from
  `AnimalVariations.dll` — `thingClass AnimalMultiSkins` and a `NAGraySquirrel_SkinSet.xml` under
  `Textures/` — a library shipped with no sources, which does not survive the render tree RimWorld
  moved to in 1.5. The same weighted draw is preserved: grey 1.0, black 0.4, albino 0.005.

### Removed

- **`Assemblies/AnimalVariations.dll`.** Nothing in this mod needs it any more, and it could not have
  worked on 1.6 in any case.

### Notes

No balance value was changed, the coat weights included. The biomes, the flying squirrel's 11.1 move
speed and 250 silver, and the groundhog's 1.2 are all the author's.
