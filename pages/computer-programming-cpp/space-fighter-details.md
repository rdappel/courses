---
title: Space Fighter Details
subtitle: Computer Programming C++
hideNav: false

live: https://fvtc.software/appel/computer-programming-cpp/space-fighter-details
---

# Space Fighter Details

In this unit, I am going to cover some parts of the game in greater detail. You do not need to go through all of these items! If a topic relates to the modifications you are making, then you should go through that topic.

# Vectors, Position, and Movement

In mathematics, a vector is a quantity that has both magnitude and direction. In our game, we use vectors to represent the position and movement of objects. A vector is represented by two numbers, x and y, which are the coordinates of the vector in 2D space.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/v1_wKN-8rJY" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Vectors are assumed to be relative to the origin (0,0) of the game world. The origin is the top-left corner of the game window. The x-axis increases to the right, and the y-axis increases downward. This is similar to the coordinate system used in mathematics, but the y-axis is flipped.

## Position

The position of an object is represented by a vector. The position vector is the location of the object in the game world. The position vector is used to draw the object on the screen and to check for collisions with other objects.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/wXeEsBLtPaE" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>


In the code that we looked at in the video, the enemy ship positions were calculated when the level content was loaded.

```cpp
	const int COUNT = 21; // number of enemies

	// enemy ships will be placed above the screen at
	// these x positions (relative to the screen width)
	// so 0.5 is the center of the screen
	double xPositions[COUNT] =
	{
		0.25, 0.2, 0.3,
		0.75, 0.8, 0.7,
		0.3, 0.25, 0.35, 0.2, 0.4,
		0.7, 0.75, 0.65, 0.8, 0.6,
		0.5, 0.4, 0.6, 0.45, 0.55
	};
	
	// this is the delay between each enemy ship
	// for example, the second enemy ship will appear
	// 0.25 seconds after the first enemy ship
	double delays[COUNT] =
	{
		0.0, 0.25, 0.25,
		3.0, 0.25, 0.25,
		3.25, 0.25, 0.25, 0.25, 0.25,
		3.25, 0.25, 0.25, 0.25, 0.25,
		3.5, 0.3, 0.3, 0.3, 0.3
	};

	float delay = 3.0; // start delay
	Vector2 position; // position of the enemy ship

	for (int i = 0; i < COUNT; i++)
	{
		delay += delays[i]; // accumulate the delay

		// calculate the position of the enemy ship
		double x = xPositions[i] * Game::GetScreenWidth();
		double y = -pTexture->GetCenter().Y; // above the screen
		position.Set(x, y); // set the position to the calculated x and y

		BioEnemyShip *pEnemy = new BioEnemyShip(); // create a new enemy ship
		pEnemy->SetTexture(pTexture); // set the texture of the enemy ship
		pEnemy->SetCurrentLevel(this); // set the current level of the enemy ship
		pEnemy->Initialize(position, (float)delay); // initialize the enemy ship
		AddGameObject(pEnemy); // add the enemy ship to the game object list
	}
```

## Movement

The movement of an object is represented by a vector. The movement vector is the direction and speed at which the object is moving. The movement vector is used to update the position of the object in each frame of the game.

As you saw in the video, we can add vectors together by adding their x and y components. This is how we calculate the new position of an object based on its movement vector.

Here is the update method for the enemy ship:

```cpp

void BioEnemyShip::Update(const GameTime& gameTime)
{
	if (IsActive()) // don't move unless the ship is active
	{
		// calculate the x position (sin wave), based on the ship's speed
		// and how much time has passed since the last frame
		// 1.4 is a constant to make the ship move further left and right
		float x = sin(gameTime.GetTotalTime() * Math::PI + GetIndex());
		x *= GetSpeed() * gameTime.GetElapsedTime() * 1.4f;

		// calculate the y position (downward movement), based on the ship's speed
		float y = GetSpeed() * gameTime.GetElapsedTime();

		// translate the position by the calculated x and y
		TranslatePosition(x, y);

		// if the ship is off the screen, deactivate it
		if (!IsOnScreen()) Deactivate();
	}

	// call the base class update method
	EnemyShip::Update(gameTime);
}
```

`TranslatePosition` is a method that moves the ship by the specified x and y amounts. It's defined in the `GameObject` class:

```cpp
void GameObject::TranslatePosition(const float x, const float y)
{	
	// add the x and y to the current position
	SetPosition(m_position.X + x, m_position.Y + y);
}
```

# Collision Detection

There are two phases to collision detection: broad phase and narrow phase. The broad phase is used to quickly determine which objects might be colliding. The narrow phase is used to determine if the objects are actually colliding.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/NxdDF3AAW-4" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Broad Phase

As you saw, the broad phase of collision detection is handled in the `Level` class. The levels are broken up into multiple sectors. Each frame, the game objects are placed into the sectors based on their position. This allows us to quickly determine which objects are close to each other and might be colliding.

I'm not going to post the code here because it is spread out over multiple methods. If you are interested in how this works, run a search for `m_pSectors`.

## Narrow Phase

The narrow phase of collision detection is, for the most part, handled by the `CollisionManager` class. This class keeps track of which types of objects can collide with each other (or shouldn't collide). When two objects are close to each other, the `CollisionManager` checks if they are colliding, and then calls the corresponding callback functions associated with the objects types.

# Game Object Activation

As you're probably aware, our game runs at 60 fps (frames per second). That means that we need to handle the user input, calculate the game logic, and render the game to the screen 60 times per second. Meaning that each frame has 0.0167 seconds to calculate. If the calculations take longer than that, the game will start to slow down, or 'drop frames'.

One way to help ensure that we dont drop frames is to avoid instantiating and destroying objects during the game loop. "Newing up" objects actually takes a lot of time, and can cause the game to slow down. Instead, we create all of the objects we need when the level loads, and then activate and deactivate them as needed. If you saw the videos that cover Vectors, Position, and Movement, you saw how the enemy ships are created. Lets take a look at how they are activated and deactivated.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/_iVXlcgg0cU" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

## Object Pooling and Recycling

Since we don't want to instantiate and destroy objects during the game loop, we use a technique called object pooling. Object pooling is a way to reuse objects instead of creating new ones. When an object is deactivated, it is added to a pool of objects. When a new object is needed, it is taken from the pool and activated.

In our game, the projectiles are pooled. When the player fires a projectile, it is taken from the pool and activated. When the projectile goes off the screen or hits an enemy, it is deactivated and returned to the pool.

Let's take a look:

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/LIpBa4RKCN8" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

As you saw in the video, we create the projectiles when the level loads, and give the blaster a reference to the pool.

Private field in `Level.h`:

```cpp
std::vector<Projectile*> m_projectiles;
```

In the `LoadContent` method of the `Level` class:

```cpp
	m_pPlayerShip = new PlayerShip(); // create the player ship
	Blaster *pBlaster = new Blaster("Main Blaster"); // create the blaster
	pBlaster->SetProjectilePool(&m_projectiles); // set the projectile pool
	m_pPlayerShip->AttachItem(pBlaster, Vector2::UNIT_Y * -20); // attach the blaster to the player ship

	// create the projectiles
	for (int i = 0; i < 100; i++)
	{
		Projectile *pProjectile = new Projectile();
		m_projectiles.push_back(pProjectile);
		AddGameObject(pProjectile);
	}
```

# Boolean Methods (Flags)

`Flags` are a programming term that refers to a boolean value that is used to control the flow of a program. In our game, we use flags to determine if an object is active, if it is collidable, if it is visible, etc.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/1rfkiNfBgTc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

Some examples in the game include:

- (GameObject) `IsActive` - determines if the object is active

- (Level) `IsScreenTransitioning` - determines if the screen is transitioning from one screen to another

- (Weapon) `IsAttachedToPlayer` - determines if the weapon is attached to the player

- (Projectile) `WasShotByPlayer` - determines if the projectile was shot by the player

- (Main Menu Screen) `IsQuittingGame` - determines if the player is trying to quit the game

# Game Timing and Frame Rate

When the game is updated, the `GameTime` class is passed to the `Update` method of each game object. The `GameTime` class contains information about the current time, the time since the last frame, and the total time the game has been running.

If you look at the update methods for various classes, you may find that moving objects often use the `GetElapsedTime` method of the `GameTime` class to determine how far to move in each frame.

This takes into account the movement for dropped frames. If the game is running at 60 fps, and the frame rate drops to 30 fps, the movement will be halved to compensate.

<details open>
	<summary class="video">Show/Hide Video</summary>
	<div class="video-container">
		<iframe src="https://www.youtube.com/embed/80J9UrdniSc" width="100%" height="100%" frameborder="0"
			allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture">
		</iframe>
	</div>
</details>

One of the examples shown in the video (In `Projectile::Update`):

```cpp
	Vector2 translation = m_direction * m_speed * gameTime.GetElapsedTime();
	TranslatePosition(translation);
```

# Additional Topics

If you would like me to cover any additional topics, please let me know. I can create videos and add examples as requested! All of the previous videos were requests from students that took the course before you.