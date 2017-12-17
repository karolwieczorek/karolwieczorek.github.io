# Usage

Shift+Enter - new line <br/>
Enter - execute command


# Code example

```python

root = UnityEngine.SceneManagement.SceneManager.GetActiveScene().GetRootGameObjects()
for x in root:
	print x.name

triangle = GameObject.Find("Triangle")
moveSpeed = 1

def Move(direction):
	triangle.transform.position += direction * Time.deltaTime * moveSpeed

def Movement(*args):
    if Input.GetKey(KeyCode.LeftArrow):
        Move(Vector3.left)

    if Input.GetKey(KeyCode.RightArrow):
        Move(Vector3.right)


unityEvents.update += Movement


circle = GameObject.Find("Circle")
circles = [circle]
ballSpeed = 5

def Projectile(*args):
    if ballCurrentSpeed > 0:
        for circle in circles:
            circle.transform.position += Vector3(0, Time.deltaTime * ballSpeed, 0)

unityEvents.update += Projectile

def Shoot(*args):
    if Input.GetKeyDown(KeyCode.X):
        newCircle = unityEvents.Instantiate(circle)
        newCircle.transform.position = triangle.transform.position + Vector3.up
        circles.append(newCircle)
        newCircle.GetComponent("SpriteRenderer").color = Random.ColorHSV()

unityEvents.update += Shoot

circle.transform.localScale = Vector3(0.02,0.02,0.02)

```