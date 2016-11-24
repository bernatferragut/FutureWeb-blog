---
layout: post
title: "VR - Google VR Interaction part5"
description: "Advanced Interaction: WayPoints & Teleport"
date: 2016-11-24
tags: [design, virtual reality, googleVR]
comments: true
share: true
---

## Advanced VR Interaction

> We have seen so far:

1. GAZE ( In/Out/Trigger )
2. AUTOWALK ( Stopping OnTilt )

> We take a look to:

3. WAYPOINTS
4. TELEPORT

### WAYPOINTS

![interaction](https://cloud.githubusercontent.com/assets/17754060/20390726/822801fa-aca6-11e6-94d4-781800a38f9b.jpg)

1. They represent the bes way to move in VR in a simple way from Point to Point in the same scene.
2. Easy to customize, they provide a clickable geometry surface to move between points.
3. Once Mastered they can work in any VR environment as a driving mechanism.
4. A little bit complex to implement.


Here an example of Code that achieves the results of moving through WayPoints in a scene:

‘’’

    sing UnityEngine;
    using System.Collections;

    public class Waypoint : MonoBehaviour
    {
      private enum State
      {
        Idle,
        Focused,
        (...)
      }

      [SerializeField]
      private State  		_state				= State.Idle;
      private Color		_color_origional		= new Color(0.0f, 1.0f, 0.0f, 0.5f);
      private Color		_color					= Color.white;
      private float 		_scale				= 1.0f;
      private float 		_animated_lerp		= 1.0f;
      private AudioSource _audio_source			= null;
      private Material	_material				= null;

      [Header("Material")]
      public Material	material				= null;
      public Color color_hilight				= new Color(0.8f, 0.8f, 1.0f, 0.125f);	

      [Header("State Blend Speeds")]
      public float lerp_idle 					= 0.0f;
      public float lerp_focus 					= 0.0f;
      public float lerp_hide					= 0.0f;
      public float lerp_clicked					= 0.0f;

      [Header("State Animation Scales")]
      public float scale_clicked_max			= 0.0f;
      public float scale_animation				= 3.0f;	
      public float scale_idle_min 				= 0.0f;
      public float scale_idle_max 				= 0.0f;
      public float scale_focus_min				= 0.0f;
      public float scale_focus_max				= 0.0f;

      [Header("Sounds")]
      public AudioClip clip_click				= null;				

      [Header("Hide Distance")]
      public float threshold					= 0.125f;

      void Awake()
      {		
        _material					            = Instantiate(material);
        _color_origional			            = _material.color;
        _color						            = _color_origional;
        _audio_source				            = gameObject.GetComponent<AudioSource>();	
        _audio_source.clip		 	            = clip_click;
        _audio_source.playOnAwake 	            = false;
      }


      void Update()
      {
        bool occupied 	= Camera.main.transform.position == gameObject.transform.position;

        switch(_state)
        {
          case State.Idle:
            Idle();

            _state 		= occupied ? State.Occupied : _state;
            break;

          case State.Focused:
            Focus();
            break;

          case State.Clicked:
            Clicked();

            bool scaled = _scale >= scale_clicked_max * .95f;
            _state 		= scaled ? State.Approaching : _state;
            break;

          case State.Approaching:
            Hide();	

            _state 		= occupied ? State.Occupied : _state;
            break;
          case State.Occupied:
            Hide();

            _state = !occupied ? State.Idle : _state;
            break;

          case State.Hidden:
            Hide();
            break;

          default:
            break;
        }

        gameObject.GetComponentInChildren<MeshRenderer>().material.color 	= _color;
        gameObject.transform.localScale 									= Vector3.one * _scale;

        _animated_lerp														=Mathf.Abs(Mathf.Cos(Time.timescale_animation));
      }


      public void Enter()
      {
        _state = _state == State.Idle ? State.Focused : _state;
      }


      public void Exit()
      {
        _state = State.Idle;
      }


      public void Click()
      {
        _state = _state == State.Focused ? State.Clicked : _state;

        _audio_source.Play();

        Camera.main.transform.position 	= gameObject.transform.position;
      }


      private void Idle()
      {
        float scale				= Mathf.Lerp(scale_idle_min, scale_idle_max, _animated_lerp);
        Color color				= Color.Lerp(_color_origional, 	  color_hilight, _animated_lerp);

        _scale					= Mathf.Lerp(_scale, scale, lerp_idle);
        _color					= Color.Lerp(_color, color, lerp_idle);
      }


      public void Focus()
      {
        float scale				= Mathf.Lerp(scale_focus_min, scale_focus_max, _animated_lerp);
        Color color				= Color.Lerp(   _color_origional,   color_hilight, _animated_lerp);

        _scale					= Mathf.Lerp(_scale, scale, lerp_focus);
        _color					= Color.Lerp(_color, color,	lerp_focus);
      }


      public void Clicked()
      {	
        _scale					= Mathf.Lerp(_scale, scale_clicked_max, lerp_clicked);
        _color					= Color.Lerp(_color,     color_hilight, lerp_clicked);
      }


      public void Hide()
      {
        _scale					= Mathf.Lerp(_scale, 		0.0f, lerp_hide);
        _color					= Color.Lerp(_color, Color.clear, lerp_hide);
      }
    }

‘’’

## Advanced VR Interaction

### TELEPORT

![interaction](https://cloud.githubusercontent.com/assets/17754060/20390726/822801fa-aca6-11e6-94d4-781800a38f9b.jpg)

1. A way to move to another point of the Scene with simple code. ( Normally in a Spherical Random way ).
2. Easy to customize, they provide a clickable geometry surface to move between points.
3. They can work in any VR environment as a driving mechanism.
4. Easy to implement.


Here an example of Code that achieves the results of a Random Teleport Object:

    using UnityEngine;
    using System.Collections;

    [RequireComponent(typeof(Collider))]
    public class Teleport : MonoBehaviour 
    {

      private CardboardHead head;
      private Vector3 startingPosition;
      private float delay = 0.0f; 

      void Start() 
      {
        head = Camera.main.GetComponent<StereoController>().Head;
        startingPosition = transform.localPosition;
      }

      void Update() 
      {
        RaycastHit hit;
        bool isLookedAt = GetComponent<Collider>().Raycast(head.Gaze, out hit, Mathf.Infinity);
        GetComponent<Renderer>().material.color = isLookedAt ? Color.green : Color.red;
        if (!isLookedAt) 
        { 
        delay = Time.time + 2.0f; 
        }
        if ((Cardboard.SDK.CardboardTriggered && isLookedAt) || (isLookedAt && Time.time>delay)) 
        {
          // Teleport randomly
          Vector3 direction = Random.onUnitSphere;
          direction.y = Mathf.Clamp(direction.y, 0.5f, 1f);
          float distance = 2 * Random.value + 1.5f;
          transform.localPosition = direction * distance;
        }
      }

    }

