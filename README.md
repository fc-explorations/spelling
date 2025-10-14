# Adaptive Spelling Game

A simple, adaptive spelling game designed to help users practice and improve their English spelling skills. The game uses an intelligent priority queue to present words the user struggles with more frequently. It's built with vanilla HTML, CSS, and JavaScript, and uses YAML for easy level creation.

[[link]](https://fc-explorations.github.io/spelling/)


## ✨ Features

- **Adaptive Learning**: Words answered incorrectly are shown more often.
- **Dynamic Levels**: Levels are loaded from simple `.yaml` files, making it easy to add or modify content.
- **Text-to-Speech**: The game speaks each word, with configurable voice and speed settings.
- **Admin Panel**: A built-in settings panel to customize the learning experience and create new levels.
- **Local Storage**: Saves your progress, level, and settings directly in your browser.
- **Automatic Progression**: Automatically advances to the next level once a certain accuracy is met.

## 🎮 How to Play

1.  Open `index.html` in a web browser.
2.  The game will say a word and display it with a missing part.
3.  Click on the button that you think correctly completes the word.
4.  Receive instant feedback! The game will show the correct spelling and adapt based on your answer.
5.  Use the "Level" dropdown to switch between different level files.

## ⚙️ Admin Panel

Click the **⚙️ Admin** button in the bottom-right corner to open the settings panel.

### Learning Thresholds
- **Advance if accuracy ≥ (%)**: Set the minimum accuracy percentage required to automatically move to the next level.
- **After at least (attempts)**: Set the minimum number of words that must be attempted before the game checks for level advancement.

### Speech Settings
- **Enable/Disable Speech**: Toggle the text-to-speech feature.
- **Voice**: Select from available English voices on your system/browser.
- **Speed (rate)**: Adjust the speaking speed.

### Level Editor
The admin panel includes a simple tool to create new level files.

1.  Fill in the `word`, `start` index, `end` index, and two `wrong` options.
2.  Click **Add Entry**.
3.  Repeat for all words in your new level.
4.  Click **Download YAML** to save your `new_level.yaml` file.

## 📝 Level File Structure

Levels are defined in `.yaml` files. Each file contains a list of word objects. The game logic in `index.html` expects each object to have the following structure:

```yaml
- word: "example"
  start: 2 # The starting index of the substring to guess
  end: 5   # The ending index (exclusive) of the substring
  wrong:
    - "axm" # An incorrect option
    - "amp" # Another incorrect option
```

In the example above, the game will display `ex___le` and ask the user to choose between `amp`, `axm`, and the correct answer, `amp`.

## 🚀 How to Add New Levels

1.  **Create the Level File**: Create a new file (e.g., `level_4.yaml`) using the structure described above. You can use the built-in Level Editor for this.
2.  **Update the Index**: Add the name of your new file to the `index.json` array.

    ```json
    [
      "level_1.yaml",
      "level_2.yaml",
      "level_3.yaml",
      "level_4.yaml"
    ]
    ```

3.  **Done!** The game will automatically discover and load the new level the next time you open it.

## 🛠️ Running Locally

No complex setup is required. Because this project uses standard web technologies, you can run it by simply opening the `index.html` file in any modern web browser.

For best results (especially for fetching level files), it's recommended to serve the project directory using a simple local server. If you have Python installed, you can run:

```bash
# For Python 3
python -m http.server
```

Then, navigate to `http://localhost:8000` in your browser.

