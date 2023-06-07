# Animal-Feeding-Phase-II

## Aim:
To develop a animal feeding game Phase-2 using unity.
## Algorithm:
### Random Animal Stampede
### Step 1:
 In the Hierarchy, create an Empty object called “SpawnManager”
### Step 2:
 Create a new script called “SpawnManager”, drag the script and attach it to the Spawn Manager in the hierarchy , and open it
### Step 3: 
Declare new public GameObject[ ] animalPrefabs;
### Step 4: 
In the inspector assign the size as 3 , for each element drag the animals from prefabs folder into the array

### Collision Decisions
### Step 1: 
Double-click on one of the animal prefabs, then Add Component > Box Collider
### Step 2:
 Click Edit Collider, then drag the collider handles to encompass the object
### Step 3: 
Check the “Is Trigger” checkbox
### Step 4:
 Repeat this process for each of the animals and the projectile
### Step 5:
 Add a RigidBody component to the (pizza)projectile and uncheck “use gravity”.
### Step 6: 
Create a new DetectCollisions.cs script, then drag the scripts and add it to each animal prefab and pizza, then open it and check it.
### Step 7:
 For all the animal prefabs and food in th inspector (below the  layer ) drop down the override option and choose apply all.

## Program:
```
Developed by: Senthil Kumar S
Register number: 212221230091
```
## SPAWN MANAGER:
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class SpawnManager : MonoBehaviour
{
    public GameObject[] animalPrefabs;
    private float spawnRangex = 20;
    private float spawnPosZ = 20;
    private float startDelay = 2;
    public float spawnInterval=1.5f;
    void Start()
    {
        InvokeRepeating("SpawnRandomAnimal", startDelay, spawnInterval);
    }
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.S))
            SpawnRandomAnimal();
    }
    void SpawnRandomAnimal()
    {
        int animalIndex = Random.Range(0, animalPrefabs.Length);
        Vector3 spawnPos=new Vector3(Random.Range(-spawnRangex,spawnRangex),0,spawnPosZ);
        Instantiate(animalPrefabs[animalIndex], spawnPos, 
                    animalPrefabs[animalIndex].transform.rotation);
    }
}

```
## DETECT COLLISION
```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class DetectCollider : MonoBehaviour
{
    void Start(){}
    void Update(){}
    private void OnTriggerEnter(Collider other)
    {
        Destroy(gameObject);
        Destroy(other.gameObject);
    }
}
```
## Output:
![243413943-c3530b83-5537-42f4-aef3-be3161e7f74b](https://github.com/Senthil-Kumar-710/demo/assets/93860256/246c7145-9bf6-43f6-88e8-143456cc831f)



## Result:
Thus, Animal feeding game Phase-2 using unity is developed successfully.
