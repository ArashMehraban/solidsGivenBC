# Adding Givens BC to solids

![Beam with 6 sideset](test.png)

(999 : left, 998 : right, 997 : front, 996 : back, 995 : top, 994: bottom) 

How to run with Givens rotation (10 radians):

degree 1:

`./elasticity -problem hyperFS -mesh ./meshes/test.exo -degree 1 -nu 0.3 -E 6.9e10 -bc_clamp 999,998,997,996,995,994 -bc_clamp_999_givens 1,0,0,0.174533 -bc_clamp_998_givens 1,0,0,0.174533 -bc_clamp_997_givens 1,0,0,0.174533 -bc_clamp_996_givens 1,0,0,0.174533 -bc_clamp_995_givens 1,0,0,0.174533 -bc_clamp_994_givens 1,0,0,0.174533 -num_steps 10 -snes_linesearch_type cp -snes_rtol 1e-7`

degree 2 and above divereges:

`./elasticity -problem hyperFS -mesh ./meshes/test.exo -degree 2 -nu 0.3 -E 6.9e10 -bc_clamp 999,998,997,996,995,994 -bc_clamp_999_givens 1,0,0,0.174533 -bc_clamp_998_givens 1,0,0,0.174533 -bc_clamp_997_givens 1,0,0,0.174533 -bc_clamp_996_givens 1,0,0,0.174533 -bc_clamp_995_givens 1,0,0,0.174533 -bc_clamp_994_givens 1,0,0,0.174533 -num_steps 10 -snes_linesearch_type cp -snes_rtol 1e-7`

Modification to the Code:

`solids/elasticity.h`: line 127

from `PetscScalar   bcClampMax[16][7];` to `PetscScalar   bcClampMax[16][11];`

`solids/src/cloptions.c` : line 98

from `for (PetscInt j = 0; j < 7; j++)` to `for (PetscInt j = 0; j < 11; j++)`

and added lines 127 - 134

and modified `solids/src/boundary.c`
