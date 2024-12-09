# BoneProp by aux-ihex

Simple VRCFury setup, just drag into Avi root, place prop in container (delete cube if desired), and done!

Stats:
- 4 Constraints - 1 parent & 3 position
- 1 Physbone

## Customization

FIRST: upack prefab so vrcfury is editable

- Set ResetPos to a different armature link, move the reset pos to desired position next to new armature.
- Rename Menu using menu prefix under BoneProp (can rename the whole prop if desired as well, vrcfury can be magic)


## How it works
(ab)uses VRC Physbone stretch to sync grabbing and moving the endpoint, a following object (DropPos) is constrained to the endpoint while it is being grabbed. On drop the physbone will disable itself, set its parent root and endpoint to where DropPos is at, then re-enable itself. Effectively setting the new world drop position! 

There is a bit of network shenanigans with constrains so we disable the container constraint until we are done messing around with physbone positions.

# Notes
Does NOT support rotation. The only way to get that from remote players as of 12/9/24 is to have 2 contact tracking bubbles and an aim constraint. If you need this consider using https://github.com/ThatFatKidsMom/Avatar-Prop instead.

FRCFury complains about animating phybone transforms, and its normally right, but we disable the physbone before we mess with any of the transforms.