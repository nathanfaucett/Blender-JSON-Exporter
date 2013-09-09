Blender-JSON-Exporter
=====================

Blender JSON Exporter (.json)


### File Format

```
{   
    "vertices": [ 1,1,1, -1,-1,-1, 1.... ],

    "normals": [ 1,1,1, -1,-1,-1, 1.... ],

    "colors": [ 1,1,1 0,0,0, 0.... ],

    "uvs":[ 1,1, 0,0 0,1, 1.... ],

    "faces": [ 0,1,2,3,4... ],

    "bones": [
        {
            // parent -1 no parent, else index of parent in bones array
            "parent": -1,
            "name": "Bone-1,
            "bindPose": [1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1],
            
            // boolean whether has vertices attached or not
            "skinned": %(skinned)s,
        
            "position": [0,0,0],
            "rotation": [0,0,0,1],
            "scale": [1,1,1],
            
            "inheritRotation": %(inheritRotation)s,
            "inheritScale": %(inheritScale)s
        }
    ],
    
    // bones weights of vertex at that index
    "boneWeights": [ 0,0, 1,1, 0,1 ],

    // locations index in bones array
    "boneIndices": [ 0,0, 1,2, 3,4 ],

    "animations": {
        // action name in blender
        "idle": [
            //frame 1, each frame contains each bones position rotation and scale for that frame
            [
                // pos, rotation, scale
                
                /* bone at index 0 */[ 0,0,0, 0,0,0,1, 1,1,1 ],
                /* bone at index 1 */[ 0,0,0, 0,0,0,1, 1,1,1 ]
            ],
            //frame 2
            [
                [ 0,0,0, 0,0,0,1, 1,1,1 ],
                [ 0,0,0, 0,0,0,1, 1,1,1 ]
            ]
        ],
        "run": [
            [
                [ 0,0,0, 0,0,0,1, 1,1,1 ],
                [ 0,0,0, 0,0,0,1, 1,1,1 ]
            ],
            [
                [ 0,0,0, 0,0,0,1, 1,1,1 ],
                [ 0,0,0, 0,0,0,1, 1,1,1 ]
            ]
        ]
    }
}
```


###Exporting ( after adding and enabling the addon )

select the mesh to export go to File > Export > JSON (.json)

###Faces

exports vertices, normals, uvs and colors based on Object's polygons so faces are 0,1,2,3,4...

###Animation & Armature

only exports first armature in scene, all actions are exported