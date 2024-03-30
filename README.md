# Path Finding
Using Unity and C#, we implemented a simple chasing situation, which includes players and multiple enemies that chase the the player. By using Navmes, all the agents can learn and find the best path to go to the target.

Click this YouTube link to see the simulation run in Unity. 
...

# Simulations (for those who do not want to use Unity)

**Figure 1.1.1: The Agent Model**

![image](https://github.com/harryhaido/PathFindingUnityAI/assets/114239084/6d6c3656-9670-46d5-9d1e-be9e388d8322)

**Figure 1.1.2: Testing the agent in different maps**

![image](https://github.com/harryhaido/PathFindingUnityAI/assets/114239084/0e74852c-1ada-465b-ad14-423455985d01)

**Figure 1.1.3: Dynamic maps**

![image](https://github.com/harryhaido/PathFindingUnityAI/assets/114239084/5b7867dc-fa26-4f73-b2dd-0cd4a5fd3650)


**Figure 1.2: The Simulation**

![image](https://github.com/harryhaido/PathFindingUnityAI/assets/114239084/3393d0f5-8497-4714-8b54-b5dacba6c2cb)

**Figure 1.3: In Action** <br/>

![0330-ezgif com-video-to-gif-converter](https://github.com/harryhaido/PathFindingUnityAI/assets/114239084/77fe1587-4e61-469c-a8fc-ebc8af7969b2)

# Implementation

The Player can move freely in the pre-build environment and the enemies will chase that player. Each enemy will have a different path when trying to chase the Player

This is the code for the Player to find an go to the destination by mouse click

```cpp
using UnityEngine;
using UnityEngine.AI;

public class PlayerController : MonoBehaviour
{

    public Camera cam;

    public NavMeshAgent agent;
    void Start()
    {
        agent = gameObject.GetComponent<NavMeshAgent>();
        cam = Camera.main;
    }
    // Update is called once per frame
    void Update()
    {
        if (Input.GetMouseButtonDown(0))
        {
            Ray ray = cam.ScreenPointToRay(Input.mousePosition);
            RaycastHit hit;

            if (Physics.Raycast(ray, out hit))
            {
                agent.SetDestination(hit.point);
            }
        }
    }
}
```
This code is for the enemy to chase the Player

```cpp

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class EnemyFollow : MonoBehaviour
{
    public UnityEngine.AI.NavMeshAgent enemy;
    public Transform Player;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        enemy.SetDestination(Player.position);
    }
}

```
