sing System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float speed = 5f;
    public int health = 10;
    public int attackDamage = 1;
    public Color playerColor = new Color(0.137f, 0.953f, 0.129f); // RGB #253f21

    void Start()
    {
        GetComponent<SpriteRenderer>().color = playerColor;
    }

    void Update()
    {
        Move();
        if (Input.GetKeyDown(KeyCode.Space))
        {
            Attack();
        }
    }

    void Move()
    {
        float moveX = Input.GetAxis("Horizontal") * speed * Time.deltaTime;
        float moveY = Input.GetAxis("Vertical") * speed * Time.deltaTime;
        transform.Translate(new Vector3(moveX, moveY, 0));
    }

    void Attack()
    {
        Debug.Log("Player Attacks!");
        // Attack logic here
    }
}

public class Enemy : MonoBehaviour
{
    public int health = 10;
    public int damage = 1;

    public void TakeDamage(int damageAmount)
    {
        health -= damageAmount;
        Debug.Log("Enemy took damage! Current health: " + health);
        if (health <= 0)
        {
            Destroy(gameObject);
        }
    }
}
