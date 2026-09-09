# Patch Notes

## Blender 5.2 Compatibility Fix

### Problem

Blender 5.2 changed the Geometry Nodes modifier Python API.

Modular Tree 5.5.2 was using the older modifier assignment method when setting Geometry Nodes inputs.

This caused the following error when adding leaves:

TypeError: bpy_struct[key] = val: id properties not supported for this type

### Original Code

modifier[socket_id] = value

### Modified Code

getattr(modifier.properties.inputs, socket_id).value = value

### Affected Function

distribute_leaves()

### Changes Made

Updated Geometry Nodes modifier input assignments to use Blender 5.2's modifier.properties.inputs API.

Affected parameters include:

- Leaf Object
- Distribution Mode
- Phyllotaxis Angle
- LOD 1 Object
- Other Geometry Nodes inputs using the same assignment method

### Tested With

Blender: 5.2.1
Modular Tree: 5.5.2

### Tested Features

- Tree generation
- Branch generation
- Leaf distribution
- Custom leaf object

### Result

Leaf distribution works correctly in Blender 5.2.1 after applying the compatibility changes.

### Purpose

This patch is maintained as a personal compatibility backup for Blender 5.2.1.

Original project:
https://github.com/GoodPie/modular_tree

Original project and its licensing remain the property of their respective authors.
