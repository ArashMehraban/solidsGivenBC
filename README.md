# Adding Givens BC to solids

How to run:

`./elasticity -problem hyperFS -mesh ./meshes/beam_4e_6ss.exo -degree 1 -nu 0.3 -E 6.9e10 -bc_clamp 999,998,997,996,995,994 -bc_clamp_999_givens 1,0,0,0.16667 -bc_clamp_998_givens 1,0,0,0.16667 -bc_clamp_997_givens 1,0,0,0.16667 -bc_clamp_996_givens 1,0,0,0.16667 -bc_clamp_995_givens 1,0,0,0.16667 -bc_clamp_994_givens 1,0,0,0.16667 -num_steps 1 -snes_linesearch_type cp -snes_rtol 1e-7`
