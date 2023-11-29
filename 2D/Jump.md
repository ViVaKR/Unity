# Jump

```csharp

public class BirdJump : MonoBehaviour
{
    Rigidbody2D _rb;
    
    public float jumpPower;

    private void Start()
    {
        _rb = GetComponent<Rigidbody2D>();
    }

    void Update()
    {
        if (Input.GetMouseButtonUp(0))
        {
            GetComponent<AudioSource>().Play();
            _rb.velocity = Vector2.up * jumpPower; // (0,1)
        }
    }

    private void OnCollisionEnter2D(Collision2D other)
    {
        Score.BestScore = Score.MyScore > Score.BestScore ? Score.MyScore : Score.BestScore;
        SceneManager.LoadScene(sceneName: $"GameOverScene");
    }
}

```
