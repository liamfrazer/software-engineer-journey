---
tags:
  - csharp
  - Unity
  - audio
---
# Audio Introduction


* Audio File - The sound that gets played
* Audio Source - To 'play' the audio
* Audio Listener - To 'hear' the audio


* Listener is normally always on the main camera

![[Pasted image 20240129174120.png]]
![[Pasted image 20240129174157.png]]


```c#
AudioSource audioSource;

void start()
{
	audioSource = GetComponent<AudioSource>();
}
```

```c#
 private void ProcessThrust()
 {
     if (Input.GetKey(KeyCode.Space))
     {
         rb.AddRelativeForce(Vector3.up * mainThrust * Time.deltaTime);
         if (!audioSource.isPlaying)
         {
             audioSource.Play();
         }

     }
     else
     {
         audioSource.Stop();
     }

 }
```







