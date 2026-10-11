# BL 3D-art channel pins: link index

An index of the pinned messages in the **#bl-3d-art** channel of the Bannerlord modding Discord (as of 2026-10-10), with credit to each author and a pointer to where that topic is documented today.

The main written reference for this material is the community wiki **[docs.bannerlordmodding.lt](https://docs.bannerlordmodding.lt/)** (maintained by Litauen; source at [Litauen/docs.bannerlordmodding.lt](https://github.com/Litauen/docs.bannerlordmodding.lt)). Its 3D section already absorbed much of these pins. A full Wayback Machine snapshot of the wiki was taken on 2026-10-10: [web.archive.org/web/2026/https://docs.bannerlordmodding.lt/](https://web.archive.org/web/2026/https://docs.bannerlordmodding.lt/).

Nothing below is my work. If you are one of the authors and want an entry changed, open an issue.

## Guides and documents

| Pin | Author / shared by | Original | Now covered on the wiki |
|---|---|---|---|
| Bannerlord 3D Asset Workflow (Google Doc) | Major Roy [HoT], 2021-07-04 | [Google Doc](https://docs.google.com/document/d/1aHBsO3mzkT0JsbCt9aCOh6CWAFATXwKtSaVb__TYIoo/edit) | [3D Workflow](https://docs.bannerlordmodding.lt/3d/workflow/), [Polycount](https://docs.bannerlordmodding.lt/3d/polycount/), [Shields](https://docs.bannerlordmodding.lt/3d/shields/), [Cloth Physics](https://docs.bannerlordmodding.lt/3d/cloth_physics/), [Create LODs](https://docs.bannerlordmodding.lt/3d/create_lods/) |
| Importing Assets into BL Editor (Google Doc) | Major Roy [HoT], 2021-07-04 | [Google Doc](https://docs.google.com/document/d/1ZnkRjNu6wUx3UM0exMiC8WhE8iDXPJKqYcbZdRh_q0o/edit) | [FBX import into Editor](https://docs.bannerlordmodding.lt/3d/editor_fbx_import/), [Material](https://docs.bannerlordmodding.lt/3d/material/), [Collision Body](https://docs.bannerlordmodding.lt/3d/collision_body/) |
| Banners on armour pieces (checklist) | MRay6000, 2023-01-15 | Discord pin | [Sigil](https://docs.bannerlordmodding.lt/3d/sigil/) |
| Helmet rigging in Blender (step list) | PlebeianKilo [ER], 2020-10-11 | Discord pin | [Armature/Skeleton](https://docs.bannerlordmodding.lt/3d/armature_skeleton/), [Weight Painting](https://docs.bannerlordmodding.lt/3d/weight_painting/), [Export to FBX](https://docs.bannerlordmodding.lt/3d/export_to_fbx/) |
| Specular map channel packing and `use_specular` | gkx (TaleWorlds), 2020-10-02 | Discord pin | [Material](https://docs.bannerlordmodding.lt/3d/material/) (partly: the `seperate_displacement_map` flag for parallax is not on the wiki yet) |
| Texture suffix naming (`_d` `_n` `_s` `_h`) and compression | gkx (TaleWorlds), 2020-10-07 | Discord pin | not on the wiki yet |
| Block-compression sizes | Swyter, 2020-07-30 | Discord pin | not on the wiki yet |
| Weapon-part and armour triangle budgets | John.M (TaleWorlds), quoted by Earendil, 2020-04-07 | Discord pin | [Polycount](https://docs.bannerlordmodding.lt/3d/polycount/) (measured averages; the TaleWorlds per-part ranges are not on the wiki yet) |

## Tools

| Pin | Author / shared by | Link | Wiki page |
|---|---|---|---|
| Avto: Data/LODs Blender add-on (weight transfer + LOD generation) | GulagEnabler [ɢᴀ㎜ᴀ], 2024-03 | Discord attachment | [Gulag's Avto script](https://docs.bannerlordmodding.lt/editor/gulags_avto_weightlods_script/) (current download) |
| TpacTool, unofficial asset explorer | Marko, 2020-04-30 | [TaleWorlds forum](https://forums.taleworlds.com/index.php?threads/tool-tpactool-an-unofficial-asset-explorer.420848/) | [TpacTool](https://docs.bannerlordmodding.lt/resources/tpactool/) |
| Hand Morphing Tool and Tutorial (3ds Max and Blender), by Enpremi | shared by John_M, 2022-04-04 | [TaleWorlds forum](https://forums.taleworlds.com/index.php?threads/hand-morphing-tool-and-tutorial-3ds-max-and-blender.444631/) | not listed yet |
| `HandArmorMorphsOverview.zip` | DG, 2021-04-16 | Discord attachment | — |
| Bannerlord Crafting Tool v1.0 (weapon piece offset previewer) | shared by Earendil, 2026-06-11 | [haterade22/TAOM release](https://github.com/haterade22/TAOM/releases/tag/crafting-tool-v1.0) | not listed yet |
| BannerlordModding.LT wiki | shared by GulagEnabler [ɢᴀ㎜ᴀ], 2025-06-22 | [docs.bannerlordmodding.lt](https://docs.bannerlordmodding.lt/) | — |
| Google Drive resource folder | cyber [TOR], 2024-11-09 | [Drive folder](https://drive.google.com/drive/folders/1mi2y_sO-ctpqScMlT5zvU1r01L2810_V) | — |
| Blenderlord reference materials (this repo) | fiefevictionnotice | [GitHub](https://github.com/fiefevictionnotice/blenderlord-reference-materials), [archive.org](https://archive.org/details/bannerlord-reference-blender) | — |

## Skeleton and body reference meshes

Mirrored in [reference-meshes/](reference-meshes/) so they survive the original links going dead. The meshes are TaleWorlds game content (see [THIRD-PARTY-NOTICES.md](../THIRD-PARTY-NOTICES.md)). The credit goes to the people who extracted and shared them.

| File | Shared by | Original link | MD5 |
|---|---|---|---|
| [human_skeleton_with_male_body.fbx](reference-meshes/human_skeleton_with_male_body.fbx): human skeleton + male body, FBX 7.4 | docs.bannerlordmodding.lt, [Armature/Skeleton](https://docs.bannerlordmodding.lt/3d/armature_skeleton/) page | [Drive](https://drive.google.com/file/d/1Pasf8ZmngJGP5eKlTIG_JS8LlFG7u42Q/view) | `9989bd8a349ed7d3fb67e7e316d1e6f0` |
| [manBody_Bannerlord_original.obj](reference-meshes/manBody_Bannerlord_original.obj): default male body, 14,183 faces (Cinema 4D export) | Earendil, #bl-3d-art pin, 2020-04-07 | [Drive](https://drive.google.com/open?id=1B_-SrRyW4F6vY39mijgK4vx9-AgY6jCA) | `c39f2b661172f454c6f57f8a9928970a` |
| [M&B2-FEMALE.obj](reference-meshes/M&B2-FEMALE.obj): female body, 11,832 faces (Blender 2.79 export) | TH3WICK3D1, #bl-3d-art pin, 2020-04-09 | [Drive](https://drive.google.com/open?id=13oq_ni-a2eXTBlLF-8I7tI7s8tyfPvfk) | `a15a3aab30fa8c189c080f267d7fbcab` |
| Default male body, OBJ (Avelium) | quoted by Earendil, 2020-04-07 | [Drive](https://drive.google.com/open?id=1qWDJRntfn8gsQlCuCaN2-hJwi6doZkD7) | **dead link (404)**, not recovered |

Notes:
- For rigging, use the FBX. Follow the wiki Armature/Skeleton page: rename the armature to `human_skeleton_notused`, hide the body, and parent your mesh to the skeleton.
- The OBJs are static scale and shape references with no skeleton. Their `.mtl` files were never shared, so they import without materials. Compare their orientation and scale with the FBX before you model around them. Avelium noted that one body OBJ came out rotated 180° compared with TpacTool exports.
- You can export the native meshes yourself with [TpacTool](https://docs.bannerlordmodding.lt/resources/tpactool/).

For full guides on 3D art and scenes compiled from the whole #bl-3d-art and #bl-scenes history, see the [Scene Toolkit guides](https://github.com/fiefevictionnotice/BannerlordSceneToolkit/tree/main/guides).
