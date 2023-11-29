# Movement

```csharp

public class Move : MonoBehaviour
{
    public float speed;

    // 처음 시작 여부 판정 변수
    private bool _isStart;

    // 초기화
    private void Start()
    {
        _isStart = true;
    }

    void Update()
    {
        if (_isStart)
        {
            StartCoroutine(LazyStart());
            StopCoroutine(LazyStart());
        }
        else
        {
            transform.position += speed * Vector3.left * Time.deltaTime;
        }
    }

    IEnumerator LazyStart()
    {
        yield return new WaitForSeconds(2);
        _isStart = false;
    }
}
// 프레임당 m : 6FPS = 1초에 6m, 3FPS = 1초에 3m
// 프레임을 맞춰주어야 함
// Time.deltaTime 을 사용하여 FPS 를 보정하여 줌
// 1초에 6m * 1/6 (delta time) => 1초에 1m
// 1초에 3m * 1/3 (delta time) => 1초에 1m
```
