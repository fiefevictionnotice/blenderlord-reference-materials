# Bannerlord polycounts: LOD0 render meshes vs physics shapes (game 1.4.8 + Naval DLC)

Every PhysicsShape asset (7,871) and every metamesh (15,682) in Native + NavalDLC `EmAssetPackages`, read with TpacTool.
Triangle counts only; nothing here is a performance budget TaleWorlds published, it is what their own assets ship with.

Raw data:
- `Bannerlord-LOD0-vs-Physics-Polycounts.tsv` - one row per render mesh that has a physics shape of the same name
  (`bo_<mesh>`): LOD0 tris, LOD count, lowest-LOD tris, physics tris, capsule/sphere primitives, physics as % of LOD0,
  LOD0 bounding-box size in meters. 6,302 pairs (occluders `bo_occ_*` excluded).
- `Bannerlord-Physics-Shape-Polycounts.tsv` - every physics shape: manifolds, verts, faces, capsules, spheres, physics materials.

## Rules of thumb

- **Physics is about 5% of LOD0.** Median across all 6,302 pairs: 5.6% (90th percentile 29%). Buildings sit at 2-8%,
  rocks and cliffs at about 25%, because their silhouette *is* the collision.
- **Big single-mesh buildings:** LOD0 50k-155k tris (castle gatehouses, keeps, round towers), physics 300-8k. Examples: `empire_house_d` 59,099 / 1,875,
  `empire_castle_gatehouse_a_l2` 125,682 / 6,379, `khuzait_village_house_a` 16,547 / 1,664. Small houses: `stone_house_a` 1,308 / 160.
- **Rocks:** a few hundred LOD0 tris, 30-100 physics tris (`map_rock_big_b_snow` 245 / 57, `nord_mossy_forest_rock_big_b` 2,636 / 56).
  Cliffs: about 1k LOD0, 150-700 physics.
- **Trees:** 292 of 413 tree/flora colliders are capsules or spheres with no mesh at all; mesh colliders stay under ~300 tris.
- **Big interiors have no LODs.** Every keep, tavern and town-house interior over ~28k tris is a single LOD (keeps 30k-214k tris, houses
  30k-76k, physics up to 14.5k); most castle exteriors drop to 1k-7k tris at their lowest LOD.
- Physics and render mesh are the same triangle count only on tiny/handheld items (throwing knives, swords, scabbards)
  and a few odd cases such as `batteringram_b_wheels` and `m_cliff_a`.

## LOD0 vs physics by category (pairs only)

Categories are by mesh name. Castle prefabs are assembled from many numbered pieces (`..._l2_11`), so their medians describe
pieces, not whole buildings; see the next table for whole buildings.

| Category | Pairs | LOD0 tris: median | LOD0 75th pct | LOD0 max | Physics tris: median | Physics 75th pct | Physics max | Physics as % of LOD0 (median) | Median-ish example: LOD0 / physics |
|---|---|---|---|---|---|---|---|---|---|
| Siege engine | 158 | 1,013 | 7,071 | 102,653 | 32 | 122 | 2,314 | 5.3% | `trebuchet_old` 1,033 / 336 |
| City / castle gatehouse | 534 | 845 | 1,687 | 155,598 | 57 | 100 | 8,231 | 8.4% | `empire_castle_gatehouse_a_l3_tower_11` 848 / 26 |
| Castle gate (siege) | 88 | 201 | 456 | 17,785 | 14 | 24 | 320 | 7.5% | `portcullis_a` 206 / 8 |
| Keep | 345 | 3,174 | 10,452 | 213,992 | 72 | 321 | 14,526 | 2.9% | `empire_keep_d_dome_b` 3,174 / 40 |
| Tower | 377 | 1,048 | 1,813 | 66,802 | 71 | 157 | 4,682 | 6.7% | `sturgia_castle_tower_round_a_l3_10` 1,048 / 35 |
| Castle / town wall | 1331 | 903 | 1,999 | 71,364 | 52 | 89 | 3,406 | 5.9% | `empire_castle_corner_b_l3_05` 903 / 32 |
| Town / village house | 456 | 1,942 | 10,412 | 75,883 | 147 | 298 | 3,465 | 5.4% | `module_european_village_house_corner_90_rooftop_a` 1,922 / 68 |
| Workshop / barn / tavern / temple | 341 | 2,859 | 6,278 | 69,187 | 56 | 175 | 4,270 | 2.6% | `shop_prop_merchantpottery_e` 2,859 / 32 |
| Cliff | 72 | 1,039 | 2,065 | 3,199 | 275 | 431 | 2,065 | 26% | `terrain_cliff_a5` 1,033 / 689 |
| Rock / boulder | 133 | 252 | 780 | 2,712 | 48 | 85 | 945 | 24% | `rock1` 252 / 68 |
| Tree / flora | 413 | 1,544 | 9,237 | 30,990 | 0 | 18 | 308 | 0.0% | `tree_high_fall_7` 1,544 / 0 |
| Ships / boats / shipyards | 11 | 4,212 | 7,764 | 18,974 | 972 | 1,034 | 2,888 | 24% | `ship_d` 4,212 / 1,202 |
| Furniture / small prop | 311 | 1,124 | 2,160 | 28,709 | 32 | 72 | 2,036 | 3.2% | `fence_old_c1` 1,124 / 28 |
| Other | 1732 | 1,117 | 3,083 | 136,801 | 48 | 162 | 9,768 | 6.0% | `bd_incense_a` 1,117 / 34 |

## Heaviest buildings (LOD0)

| Mesh | LOD0 tris | LODs | Lowest LOD tris | Physics tris | LOD0 size (m) |
|---|---|---|---|---|---|
| `empire_castle_keep_a_l2_interior` | 213,992 | 1 | 213,992 | 11,322 | 38.95 x 34.43 x 23.88 |
| `sturgia_castle_keep_a_l3_interior` | 181,122 | 1 | 181,122 | 4,025 | 43.57 x 45.32 x 13.51 |
| `european_castle_gatehouse_a_l2` | 155,598 | 4 | 2,533 | 1,933 | 25.36 x 19.3 x 22.49 |
| `european_castle_gatehouse_b_l3` | 132,909 | 3 | 36,144 | 8,231 | 30.19 x 21.23 x 38.97 |
| `aserai_castle_keep_a_l2_interior` | 130,987 | 1 | 130,987 | 14,526 | 36.43 x 29.66 x 29.09 |
| `empire_castle_gatehouse_a_l2` | 125,682 | 4 | 3,469 | 6,379 | 25.99 x 15.6 x 20.47 |
| `vlandia_keep_interior_b` | 122,723 | 1 | 122,723 | 3,622 | 35.93 x 34.22 x 15.13 |
| `sturgia_castle_keep_a_l3` | 114,072 | 4 | 3,137 | 620 | 35.62 x 35.43 x 47.08 |
| `aserai_castle_gatehouse_a_l3` | 107,711 | 4 | 3,057 | 5,246 | 26.28 x 17.04 x 27.44 |
| `khuzait_castle_gatehouse_a_l3` | 98,632 | 4 | 17,350 | 5,318 | 26.17 x 19.01 x 21.43 |
| `sturgia_castle_keep_a_l2_interior` | 89,676 | 1 | 89,676 | 4,533 | 37.91 x 50.19 x 25.23 |
| `battania_keep_lvl1_interior` | 89,673 | 1 | 89,673 | 4,815 | 40.21 x 30.23 x 27.62 |
| `battania_castle_keep_a_l1` | 86,711 | 3 | 5,836 | 332 | 37.14 x 35.08 x 31.71 |
| `battania_castle_keep_a_l3` | 84,919 | 4 | 3,712 | 1,758 | 40.76 x 37.24 x 46.22 |
| `vlandia_keep_interior` | 84,425 | 1 | 84,425 | 685 | 68.02 x 52.21 x 20.51 |

## Physics shapes on their own: whole objects (occluders bo_occ_*, barriers, numbered sub-pieces and empty flora colliders excluded)

| Category (whole shapes only) | Shapes | Median faces | 25th | 75th | 90th | Max | Median verts | Median-ish example |
|---|---|---|---|---|---|---|---|---|
| City / castle gatehouse (whole) | 102 | 170 | 50 | 1055 | 2276 | 8231 | 140 | `bo_aserai_castle_gatehouse_a_l1_stairs` 172 |
| Keep (whole, incl. interiors) | 337 | 73 | 28 | 321 | 1099 | 14526 | 50 | `bo_empire_keep_a_main_building` 73 |
| Tower (whole) | 135 | 200 | 74 | 578 | 1794 | 4682 | 117 | `bo_khuzait_castle_tower_round_a_l2_stairs4` 200 |
| Castle wall segment | 293 | 291 | 160 | 609 | 1014 | 3406 | 174 | `bo_european_castle_wall_gate_l1` 291 |
| Town / village house | 459 | 160 | 84 | 310 | 701 | 3465 | 100 | `bo_stone_house_a` 160 |
| Workshop / barn / tavern / temple | 297 | 56 | 20 | 168 | 412 | 4270 | 35 | `bo_aserai_grandbazaar_corner_shop_door` 56 |
| Rock / boulder | 129 | 57 | 32 | 198 | 460 | 1423 | 36 | `bo_map_rock_big_b_snow` 57 |
| Cliff | 35 | 316 | 163 | 400 | 752 | 2065 | 172 | `bo_mainmap_cliff_c` 316 |
| Tree trunk / flora collider | 112 | 43 | 22 | 60 | 92 | 260 | 25 | `bo_log_pine_d` 42 |
| Furniture / small prop | 355 | 32 | 18 | 72 | 162 | 2036 | 20 | `bo_curtain_battania_bed_c` 32 |

Whole-building physics is assembled from pieces in the big castle prefabs (40-60 child shapes of 20-100 tris each), so the
"whole" gatehouse/keep medians are low; the single-shape city buildings are the better guide: gatehouses 3,500-8,200 tris
(e.g. bo_empire_castle_gatehouse_a_l2 6,379), keeps interiors 8,000-14,500, towers 2,500-4,700, town houses 1,400-3,500
(bo_empire_house_d 1,875, bo_khuzait_village_house_a 1,664), village/stone houses 100-300, rocks 30-120 with big cliff rocks
700-1,400. Overall: median 46 tris, 90th percentile 342, max 14,526 (bo_aserai_castle_keep_a_l2_interior). 438 shapes use
capsule/sphere primitives instead of (or with) a mesh; only 2 have more than one manifold.

## Physics shapes on their own: all shapes by name pattern (includes occluders and sub-pieces)

| Category | Shapes | Faces: median | 25th pct | 75th pct | max | Verts: median | Typical example (faces) |
|---|---|---|---|---|---|---|---|
| Gatehouses | 662 | 50 | 29 | 95 | 8231 | 32 | `bo_aserai_castle_gatehouse_a_l2_11` (50) |
| Castle gates (siege) | 329 | 24 | 16 | 66 | 1259 | 16 | `bo_empire_castle_gate_inner_l2_state1_frame` (24) |
| Towers | 540 | 53 | 24 | 118 | 4682 | 34 | `bo_aserai_castle_tower_round_a_l1_11` (53) |
| Keeps | 444 | 48 | 14 | 204 | 14526 | 33 | `bo_battania_castle_keep_wood_stake_c` (48) |
| Castle walls / corners | 1663 | 48 | 28 | 80 | 3406 | 31 | `bo_aserai_castle_corner_c_l1_08` (48) |
| Houses (town/village) | 683 | 111 | 32 | 220 | 3465 | 68 | `bo_occ_house_f` (111) |
| Workshops / utility bldgs | 340 | 46 | 20 | 160 | 4270 | 32 | `bo_occ_battania_castle_barn_b_l3` (46) |
| Rocks / boulders | 195 | 56 | 32 | 120 | 1423 | 32 | `bo_nord_mossy_forest_rock_big_b` (56) |
| Cliffs | 64 | 149 | 68 | 367 | 2065 | 87 | `bo_cliff_i` (149) |
| Trees / flora | 428 | 0 | 0 | 18 | 308 | 0 | `bo_flora_shrub_fall_2` (0) |
| Furniture / small props | 379 | 32 | 12 | 68 | 2036 | 18 | `bo_curtain_battania_bed_c` (32) |
| Siege engines | 118 | 31 | 4 | 124 | 2314 | 18 | `bo_ballista_damaged_part_05` (30) |
| Ships / boats / shipyards | 11 | 972 | 188 | 1034 | 2888 | 542 | `bo_ship_c` (972) |
| Map icons | 31 | 54 | 37 | 76 | 496 | 32 | `bo_map_bridge_a` (54) |
| Characters / animals | 37 | 16 | 12 | 60 | 298 | 10 | `bo_merchandise_salt` (16) |
| Weapons / shields | 251 | 20 | 16 | 38 | 1810 | 18 | `bo_throwing_spear_quiver_3_2` (20) |
| Other | 1696 | 52 | 18 | 176 | 9768 | 32 | `bo_cap_battania_targe_b` (52) |

All shapes: 7,871, median 46 tris, 90th percentile 342, max 14,526 (`bo_aserai_castle_keep_a_l2_interior`).
438 shapes use capsule/sphere primitives; 2 have more than one manifold.

Generated 2026-09-20 (physics) and 2026-10-08 (LOD0 pairing) from game 1.4.8 with the TpacTool 0.4.2 fork.
