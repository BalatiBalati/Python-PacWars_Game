

# Python-PacWars_Game Guide: From Creation to Web Hosting
## A star wars themed pacman game created with pygames

## 1. **Creating the Game**

### Game Overview

**Python-PacWars_Game** is a Pac-Man inspired game created using **Pygame**. The game includes a player who must navigate through a maze, collect points, and avoid ghosts. There are power-ups that allow the player to turn the tables and eat the ghosts for extra points.

### Game Features

- **Player Movement**: The player can move up, down, left, and right using arrow keys.
- **Ghost AI**: The game features four ghosts (Blinky, Inky, Pinky, and Clyde) with unique behaviors.
- **Power-ups**: Collecting power-ups allows the player to eat the ghosts for bonus points.
- **Lives and Scoring**: The player starts with a set number of lives and scores points by eating pellets and ghosts.

### Core Libraries Used

- **Pygame**: Used to build the 2D game environment, including rendering graphics, handling input, and managing game logic.
- **pygbag**: A tool to convert the Python game to JavaScript, making it playable in web browsers.

---

## 2. **Setting Up the Game Locally**

### Install Pygame

Before starting, you need to install **Pygame** to run the game locally.

1. **Set up a virtual environment** (recommended for managing dependencies):
   ```bash
   python -m venv venv
   ```

2. **Activate the virtual environment**:
   - On **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - On **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```

3. **Install the required dependencies** using `pip`:
   ```bash
   pip install pygame
   ```

4. **Additional Dependencies**:
   The game may also use other dependencies that are required for rendering and handling game elements. Ensure the following are installed:

   - **pygame** (used for all graphics and game logic).
   - **pygbag** (used for converting the game to a browser-compatible format).

   To ensure all dependencies are installed, you can include a `requirements.txt` file in your project with the following content:
   ```txt
   pygame>=2.0.1
   pygbag>=1.0.0
   ```

   Then install them with:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Game Locally

1. **Clone the repository** or **download** the Python-PacWars_Game files.

2. **Run the game**:
   ```bash
   python main.py
   ```

### Game Controls

- **Arrow Keys**: Move the player in the four directions.
- **Spacebar**: If the game is over or won, pressing Space will restart the game.

### Asset Files

Make sure that all your game assets (images, sounds, etc.) are in the correct directories. For example:
- `assets/player.png`
- `assets/pellet.png`

Ensure these files are accessible to the game’s main script.

---

## 3. **Building the Game for the Web**

To make your game playable in a web browser, use **pygbag**, a tool that converts Pygame code into JavaScript.

### Install pygbag

1. **Install pygbag**:
   ```bash
   pip install pygbag
   ```

2. **Convert the Python code into JavaScript**:
   ```bash
   pygbag main.py
   ```
   This command will create a `dist/` folder containing the web-ready files: `index.html`, `main.js`, and assets.

### Test Locally

After converting the game to JavaScript, you can test it by opening `index.html` in your web browser. This file serves as the entry point for your game in the browser.

#### Troubleshooting:
- Ensure assets are properly loaded by checking their paths.
- Use the browser’s developer tools to inspect JavaScript errors.
- Test across multiple browsers for compatibility.

---

## 4. **Hosting the Game Online**

Once your game is converted to JavaScript using pygbag, you can host it on several platforms. Here are three popular options:

### Hosting on **GitHub Pages**

1. **Create a GitHub Repository**: 
   - Push your `dist/` folder (which contains `index.html`, `main.js`, etc.) to your repository.

2. **Set Up GitHub Pages**:
   - Go to your repository's **Settings** > **Pages**.
   - Select the `main` branch and the `/dist` folder as the source.
   
3. **Access Your Game**:
   - GitHub Pages will provide a URL like `https://yourusername.github.io/your-repository-name`.

### Hosting on **Netlify**

1. **Sign Up for Netlify** and connect your GitHub repository.
2. **Deploy the Game**:
   - Select the `dist/` folder as the root directory for the site.
   
3. **Access Your Game**: 
   - Netlify will provide a URL where your game will be hosted.

### Hosting on **Firebase Hosting**

1. **Install Firebase CLI**:
   ```bash
   npm install -g firebase-tools
   ```

2. **Initialize Firebase Hosting**:
   ```bash
   firebase init hosting
   ```

3. **Deploy the Game**:
   - Point Firebase to the `dist/` folder during the setup process.
   - Run `firebase deploy` to upload your game to Firebase Hosting.

---

## 5. **Game Features Recap**

### Core Mechanics

- **Player Movement**: Arrow keys to move the player.
- **Ghost Movement**: Four unique ghosts with different AI behaviors.
- **Power-ups**: Eat the power-up to turn ghosts into edible targets.
- **Score**: Earn points by collecting pellets and eating ghosts.
- **Lives**: The player loses a life when colliding with an active ghost.

---

## 6. **Code Overview**

### Main Game Loop

```python
# Main game loop (example snippet)
while run:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            run = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_RIGHT:
                direction_command = 0  # Right direction
            ...
    
    # Move player
    player_x, player_y = move_player(player_x, player_y)

    # Check collisions
    if player_circle.colliderect(ghost.rect):
        if not powerup:
            lives -= 1
            restart_game()  # Reset positions and lives

    # Render game screen
    pygame.display.flip()
```

### Ghost AI Movement

Each ghost has its own behavior. Some are random, and others target the player based on simple AI algorithms.

---

## 7. **Important Considerations**

### Game Optimization

To ensure smooth gameplay, especially on the web:
- **Compress images** (use PNG or JPEG format).
- **Convert sounds** to lighter formats like MP3 or OGG.
- **Optimize collision detection** and game logic to improve performance.

### Debugging

If you encounter any issues, use browser developer tools (Console tab) to check for JavaScript errors. Enable `--debug` mode in pygbag for more detailed output.

### Performance

Web games can sometimes be slower than desktop versions. If your game experiences lag:
- Optimize assets and game logic.
- Check for unnecessary animations or complex operations.

---

## 8. **Full Setup Process**

1. **Create and Develop the Game**:
   - Build the game using Pygame with assets and game logic.
   
2. **Convert with pygbag**:
   - Run `pygbag main.py` to convert the game into a web-compatible format.
   
3. **Test Locally**:
   - Open `index.html` in your browser to test the game.
   
4. **Host Online**:
   - Choose a hosting platform (GitHub Pages, Netlify, Firebase) and upload your `dist/` folder.

---

## 9. **Resources**

- **pygbag Documentation**: [https://pygbag.dev/](https://pygbag.dev/)
- **Pygame Documentation**: [https://www.pygame.org/docs/](https://www.pygame.org/docs/)
- **Netlify**: [https://www.netlify.com/](https://www.netlify.com/)
- **GitHub Pages**: [https://pages.github.com/](https://pages.github.com/)
- **Firebase Hosting**: [https://firebase.google.com/docs/hosting](https://firebase.google.com/docs/hosting)

---

## 10. **Conclusion**

By following the above steps, you can create, test, and host your **Python-PacWars_Game** online. From local development with Pygame to converting and deploying it for web play using **pygbag**, this guide covers everything you need to turn your Python game into a playable web experience. Enjoy sharing your game with friends or users worldwide!
