# Prefab

```csharp
public class MakePipe : MonoBehaviour
{
    public GameObject pipe;
    
    private float _timer;
    
    public float timeDiff;

    void Update()
    {
        _timer += Time.deltaTime; // e.g. 6FPS : + 1/6, 6프레임에서 1초가 됨
        
        if(_timer > timeDiff)
        {
            GameObject newPipe = Instantiate(pipe);
            newPipe.transform.position = new Vector3(6, Random.Range(0, 5.5f), 0);
            _timer = 0;
            Destroy(newPipe, 15.0f);
        }
    }
}


```
