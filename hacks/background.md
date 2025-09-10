---
#YML definition of metdadata for file, used by GH pages
layout: base
title: Background with Object
description: Use JavaScript to have an in motion background.
# these are the locations of images in this game
sprite: images/platformer/sprites/car-removebg-preview.png
background: images/platformer/backgrounds/background.jpg
permalink: /background
---
<!-- HTML for where the Game is stored -->
<canvas id="world"></canvas>
<!-- JS logic for the game -->
<script>

  // Get the canvas element and its drawing context
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');

  // Create image objects for the background and the player sprite
  const backgroundImg = new Image();
  const spriteImg = new Image();
  // Set image sources using Jekyll variables
  backgroundImg.src = '{{page.background}}';
  spriteImg.src = '{{page.sprite}}';

  // Track when both images are loaded before starting the game
  let imagesLoaded = 0;
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };

  function startGameWorld() {

  // Only start the game when both images are loaded
  if (imagesLoaded < 2) return;


    // Base class for all objects in the game world
    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image; // Image to draw
        this.width = width; // Width of the object
        this.height = height; // Height of the object
        this.x = x; // X position
        this.y = y; // Y position
        this.speedRatio = speedRatio; // Speed relative to game speed
        this.speed = GameWorld.gameSpeed * this.speedRatio; // Actual speed
      }
      update() {} // Default update does nothing
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }


    // Background class for scrolling background effect
    class Background extends GameObject {
      constructor(image, gameWorld) {
        // Fill entire canvas and set a slow speed for parallax effect
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        // Move background to the left, loop when off screen
        this.x = (this.x - this.speed) % this.width;
      }
      draw(ctx) {
        // Draw two images side by side for seamless scrolling
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }


    // Player class for the moving sprite
    class Player extends GameObject {
      constructor(image, gameWorld) {
        // Set player size to half the image size and center it
        const width = image.naturalWidth / 2;
        const height = image.naturalHeight / 2;
        const x = (gameWorld.width - width) / 2;
        const y = (gameWorld.height - height) / 2;
        super(image, width, height, x, y);
        this.baseY = y; // Base Y position for floating effect
        this.frame = 0; // Animation frame counter
      }
      update() {
        // Make the player float up and down using a sine wave
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }


    // GameWorld class manages the canvas, objects, and game loop
    class GameWorld {
      static gameSpeed = 50; // Base speed for the game
      constructor(backgroundImg, spriteImg) {
        // Set up canvas and context
        this.canvas = document.getElementById("world");
        this.ctx = this.canvas.getContext('2d');
        // Set canvas size to window size
        this.width = window.innerWidth;
        this.height = window.innerHeight;
        this.canvas.width = this.width;
        this.canvas.height = this.height;
        this.canvas.style.width = `${this.width}px`;
        this.canvas.style.height = `${this.height}px`;
        this.canvas.style.position = 'absolute';
        this.canvas.style.left = `0px`;
        this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

        // Create game objects: background and player
        this.objects = [
         new Background(backgroundImg, this),
         new Player(spriteImg, this)
        ];
      }
      // Main game loop: update and draw all objects, then repeat
      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.objects) {
          obj.update();
          obj.draw(this.ctx);
        }
        requestAnimationFrame(this.gameLoop.bind(this));
      }
      // Start the game loop
      start() {
        this.gameLoop();
      }
    }

  // Create the game world and start the animation
  const world = new GameWorld(backgroundImg, spriteImg);
  world.start();
  }
  
</script>
