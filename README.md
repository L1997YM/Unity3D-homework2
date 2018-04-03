# Unity3D-homework2

1.简答题
* *游戏对象运动的本质是什么？*<br/>
  游戏对象运动的本质是在每帧中改变运动对象的position，rotation，scale等属性。
***
* *请用三种方法以上方法，实现物体的抛物线运动。（如，修改Transform属性，使用向量Vector3的方法…）*<br/>
   1.改变position
   ~~~
   using System.Collections;
   using System.Collections.Generic;
   using UnityEngine;

   public class NewBehaviourScript : MonoBehaviour {
	   public float speed;
	   public float speed_down = 0f;
	   private void Start()
	   {
  
	   }
	   private void Update()
	   {
		   speed = 1f;
		   speed_down += 0.01f;
		   transform.position += Vector3.right * speed * Time.deltaTime;
		   transform.position += Vector3.down * speed_down * Time.deltaTime;
	   }
   }
   ~~~
   2.使用transform.Translate
   ~~~
           public float speed;
	   public float speed_down = 0f;
	   private void Start()
	   {
     
           }
	   private void Update()
	   {
		   speed = 1f;
		   speed_down += 0.01f;
		   transform.Translate(Vector3.right * speed * Time.deltaTime);
		   transform.Translate(Vector3.down * speed_down * Time.deltaTime);
	   }
   ~~~
   3.使用Vector3建立增量
   ~~~
           public float speed;
           public float speed_down = 0f;
           void Start()
           {
     
           }
           void Update()
           {
 	          speed = 1f;
	          speed_down += 0.01f;
	          Vector3 temp = new Vector3 (speed * Time.deltaTime, -speed_down * Time.deltaTime, 0);  
	          transform.position += temp;  
           }
   ~~~
***
* *编写一个代码，使用 debug 语句来验证 MonoBehaviour 基本行为或事件触发的条件*
~~~
      using System.Collections;
      using System.Collections.Generic;
      using UnityEngine;

      public class NewBehaviourScript : MonoBehaviour {

        void Awake()
        {
           Debug.Log("Awake");
        }
        void Start () 
        {
           Debug.Log("Start");
        }
        void Update () 
        {
           Debug.Log("Update");
        }
        void FixedUpdate()
        {
           Debug.Log("FixedUpdate");
        }
        void LateUpdate()
        {
           Debug.Log("LateUpdate");
        }

        void OnGUI()
        {
           Debug.Log("OnGUI");
        }
        void OnDisable()
        {
           Debug.Log("OnDisable");
        }
        void OnEnable()
        {
           Debug.Log("OnEnable");
        }
      }
~~~
***
* *查找脚本手册，了解 GameObject，Transform，Component 对象*
  1. *分别翻译官方对三个对象的描述（Description）*<br/>
    GameObject: Unity场景中所有实体的基类。<br/>
    Transform：对象的位置，旋转和缩放。<br/>
    Component：所有附加在游戏对象上的物品的基类。<br/>
  2. *描述下图中 table 对象（实体）的属性、table 的 Transform 的属性、 table 的部件*<br/>
    (1)table的对象属性 <br/>
      Tag: Untagged <br/>
      Layer: Default <br/>
    (2)Transform的属性 <br/>
      Position: (0, 0, 0) <br/>
      Rotation: (0, 0, 0) <br/>
      Scale: (1, 1, 1) <br/>
    (3)table的部件: <br/>
      Transform, Cube(Mesh Renderer), Box Collider <br/>
  3.  *用 UML 图描述 三者的关系（请使用 UMLet 14.1.1 stand-alone版本出图）*
  ![](https://github.com/L1997YM/Unity3D-homework1/blob/master/hw_.jpg)<br/>
  ![](https://github.com/L1997YM/Unity3D-homework1/blob/master/UML_.png)<br/>
***
* *资源预设（Prefabs）与 对象克隆 (clone)*
  1. *预设（Prefabs）有什么好处？*<br/>
  资源预设可以大大降低资源占用，同时可以添加预设属性，当预设属性需要修改时，能更方便地做出修改。<br/>
  2. *预设与对象克隆 (clone or copy or Instantiate of Unity Object) 关系？*<br/>
  克隆对象是将原有的对象克隆一个新对象，新对象独立于原对象，修改原对象属性不会对克隆的新对象属性造成影响。
***
* *尝试解释组合模式（Composite Pattern / 一种设计模式）。*<br/>
组合模式是将对象组合成树形结构以表示"部分-整体"的层次结构，因此又叫部分-整体模式。组合模式使得用户对单个对象和组合对象的使用具有一致性，可以让客户端像修改配置文件一样简单的完成本来需要流程控制语句来完成的功能。
