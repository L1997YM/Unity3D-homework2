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
	   void Start()
	   {
  
	   }
	   void Update()
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
	   void Start()
	   {
     
           }
	   void Update()
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
* *写一个程序，实现一个完整的太阳系， 其他星球围绕太阳的转速必须不一样，且不在一个法平面上。*
~~~
//实现行星和月球的公转
using System.Collections.Generic;
using UnityEngine;

public class Roundsun : MonoBehaviour {
	public Transform sun;
	public Transform Mercury;
	public Transform Venus;
	public Transform earth;
	public Transform moon;
	public Transform Mars;
	public Transform Jupiter;
	public Transform Saturn;
	public Transform Uranus;
	public Transform Nepture;
	// Use this for initialization
	void Start () {
		sun.position = Vector3.zero;
		Mercury.position = new Vector3 (6, 0, 0);
		Venus.position = new Vector3 (10, 0, 1);
		earth.position = new Vector3 (14, 0, 0);
		moon.position = new Vector3 (16,0, 0);
		Mars.position = new Vector3 (18, 0, -1);
		Jupiter.position = new Vector3 (22, 0, 0);
		Saturn.position = new Vector3 (26, 0, 1);
		Uranus.position = new Vector3 (30, 0, 0);
		Nepture.position = new Vector3 (34, 0, -1);
	}
	
	// Update is called once per frame
	void Update () {
		Mercury.RotateAround (sun.position, Vector3.down, 20 * Time.deltaTime);
		Venus.RotateAround (sun.position, Vector3.up, 18 * Time.deltaTime);
		earth.RotateAround (sun.position, Vector3.down, 16 * Time.deltaTime);
		moon.transform.RotateAround (earth.position,Vector3.up,359 * Time.deltaTime);
		Mars.RotateAround (sun.position, Vector3.down, 14 * Time.deltaTime);
		Jupiter.RotateAround (sun.position, Vector3.down, 12 * Time.deltaTime);
		Saturn.RotateAround (sun.position, Vector3.down, 10 * Time.deltaTime);
		Uranus.RotateAround (sun.position, Vector3.up, 8 * Time.deltaTime);
		Nepture.RotateAround (sun.position, Vector3.down, 6 * Time.deltaTime);
	}
}
~~~
~~~
//实现自转
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class test1 : MonoBehaviour {

	  // Use this for initialization
	  void Start () 
	  {
		this.transform.rotation = Quaternion.AngleAxis(30,Vector3.up);
	  }

	  void Update()
	  {
	  	this.transform.rotation *= Quaternion.AngleAxis (100 * Time.deltaTime, Vector3.up);
	  }
}
~~~
***

