
<div align="center">
<h1 align="center">
<img src="https://i.imgur.com/1IRtxAw.png" width="200" />
</h1>
<h3>Unleash your word power with Boggle!</h3>
<img src="https://img.shields.io/github/languages/top/adir-barak/Boggle?style&color=5D6D7E" alt="GitHub top language" />
<img src="https://img.shields.io/github/languages/code-size/adir-barak/Boggle?style&color=5D6D7E" alt="GitHub code size in bytes" />
<img src="https://img.shields.io/github/commit-activity/m/adir-barak/Boggle?style&color=5D6D7E" alt="GitHub commit activity" />
<img src="https://img.shields.io/github/license/adir-barak/Boggle?style&color=5D6D7E" alt="GitHub license" />
<h3>Screenshots and Snippets:</h3>
</div>

![enter image description here](https://i.gyazo.com/e21562f84e7f4b1b89f9fae09b9f49be.png)
![enter image description here](https://i.gyazo.com/95f27b2b2349b9813ebdc6b7ecfeb989.png)

We added a special party mode to the game, so you can enjoy it double-time!
Some of the features are a custom button, changing colors, and sound effects.

```python
def party_mode_activated(self):


self.party_mode = 1
# self.play_sound("media/cute_song.mp3")
for cube in self.cubes:
    if cube.marked:
        continue
    cube["bg"] = self.random_color()

for button in self.buttons.values():
    button["bg"] = self.random_color()
self._timer["bg"] = self.random_color()
self._score["bg"] = self.random_color()
self._found_words["bg"] = self.random_color()
self.buttons["PARTY"]["image"] = self.meme
self._display_label["bg"] = self.random_color()


def random_color(self):
    hex_color = ["#" + ''.join([random.choice('ABCDEF0123456789') for _ in range(6)])]
    return hex_color


def party_action(self):
    self.play_sound("media/wow.mp3")
    self._gui.party_mode_activated()

```

Added sound to all buttons, using pygame library:
```python
    def play_sound(self, soundtrack: str):
        pygame.mixer.music.load(soundtrack)
        pygame.mixer.music.play()
```

![alt text](https://i.gyazo.com/6982b45ca1c84e2a86b83c5981999440.png)

Custom coloring of default board and smart coloring of picked cube path:

```python
def hue_red_color(self, multipler):
    rgb = 255, max(208 - 13 * multipler, 0), max(208 - 13 * multipler, 0)
    rgb_to_hex = "#" + '%02x%02x%02x' % rgb
    return rgb_to_hex


def _make_cube(self, cube_chars: str, row: int, col: int, rowspan: int = 1, columnspan: int = 1) -> tki.Button:
    cube = tki.Button(self._lower_frame, text=cube_chars, **BUTTON_STYLE)
    cube.marked = False
    if row % 2 == col % 2:
        cube["bg"] = REGULAR_COLOR_2
    cube.grid(row=row, column=col, rowspan=rowspan, columnspan=columnspan, sticky=tki.NSEW)
    self.cubes.append(cube)
```


---

## 📖 Table of Contents
- [📖 Table of Contents](#-table-of-contents)
- [📍 Overview](#-overview)
- [📦 Features](#-features)
- [⚙️ Modules](#modules)
- [🚀 Getting Started](#-getting-started)
    - [🔧 Installation](#-installation)
    - [🤖 Running Boggle](#-running-Boggle)
    - [🧪 Tests](#-tests)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [👏 Acknowledgments](#-acknowledgments)

---


## 📍 Overview

This project is a Boggle game implementation with a graphical user interface (GUI). It includes functionalities to generate a random Boggle board and validate user-provided words. The game allows users to play and score points based on the words they find on the board. Overall, this project provides an interactive and enjoyable experience for players while testing their word-building skills.

---

## 📦 Features

|    | Feature            | Description                                                                                                        |
|----|--------------------|--------------------------------------------------------------------------------------------------------------------|
| ⚙️ | **Architecture**   | The codebase follows a MVC (Model-View-Controller) architectural pattern, with separate files for the model, view (GUI), and controller. This promotes separation of concerns and facilitates code maintainability. |
| 🔗 | **Dependencies**   | The codebase does not have any external dependencies on external libraries or systems beyond the standard Python libraries used for string manipulation and file operations, so it's super light! |
| 🧩 | **Modularity**     | The system is organized into separate files for different components, such as the BoggleBoard class, GUI, random board generator, and game controller. This modular organization allows for easier extension and modification of individual components. |
| 🧪 | **Testing**        | The codebase includes several test files (test_set_1.py, test_set_2.py, test_set_3.py) for testing various aspects of the system. The system uses a combination of manual testing and test cases with assertions to verify correctness. |
| ⚡️ | **Performance**    | Evaluating performance can be a demanding task, especially in the absence of dedicated performance monitoring or profiling within the codebase. Nonetheless, our program demonstrates commendable efficiency, swiftly generating random boards and seamlessly handling user moves in real-time for a game of Boggle. We envision even greater performance gains through strategic algorithmic optimizations and effective caching techniques. |

---

## ⚙️ Modules

<details closed><summary>Root</summary>

| File                                                                                                      | Summary                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ---                                                                                                       | ---                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [boggle_board_randomizer.py](https://github.com/adir-barak/Boggle/blob/main/boggle_board_randomizer.py) | The code generates a random Boggle board using a provided list of letters. It shuffles the dice indices, selects a random letter from each dice, and constructs the board. The generated board is then printed using the pprint function.                                                                                                                                                                                    |
| [test_set_1.py](https://github.com/adir-barak/Boggle/blob/main/test_set_1.py) [test_set_2.py](https://github.com/adir-barak/Boggle/blob/main/test_set_2.py)   [test_set_3.py](https://github.com/adir-barak/Boggle/blob/main/test_set_3.py)                           | This code imports a module for randomizing a boggle board, reads words from a file into a set, creates a dictionary of word prefixes, and implements a binary search function. It also includes a timing decorator to measure execution time.                                                                                                                                                                                |                                                                                                                                                                                                                                                                                                                                                                                   |
| [boggle_model.py](https://github.com/adir-barak/Boggle/blob/main/boggle_model.py)                       | The code defines a BoggleBoard class that represents a Boggle game board. It contains methods for generating valid words, possible moves, and coordinates. It also handles user input, updates the score and found words list, validates words, and allows undoing and resetting the board. The code also includes utility functions for reading words from a file, generating a random board, and manipulating coordinates. |
| [boggle_gui.py](https://github.com/adir-barak/Boggle/blob/main/boggle_gui.py)                           |  The code in this file encompasses the graphical user interface (GUI) for the Boggle game. It's responsible for rendering the game board, handling user interactions, displaying the score and found words, and allowing players to interact with the Boggle game seamlessly. The GUI is thoughtfully designed to provide an engaging and intuitive user experience while complementing the underlying game logic defined in `boggle_model.py`.                                                                                                                                                                                                                                                                                                                                                                                                  |
| [boggle.py](https://github.com/adir-barak/Boggle/blob/main/boggle.py)                                   | The code creates a controller for a game of Boggle. It integrates a GUI, game model, and various actions such as picking letters, undoing moves, starting/resetting the game, and activating party mode. The controller handles logic for updating the game state, interacting with the GUI, and playing sound effects. The main game loop is initiated through the'run' method.                                             |
| [words.txt](https://github.com/adir-barak/Boggle/blob/main/words.txt)                                   | This file contains a comprehensive list of valid words that the Boggle game refers to for word validation. It serves as a crucial resource for ensuring that player-submitted words are legitimate and part of the game's accepted vocabulary. The contents of this file directly influence the gameplay experience and the accuracy of word validation within the Boggle game.                                                                                                                                                                                                                                                                                                                                                                                      |
| [algos.py](https://github.com/adir-barak/Boggle/blob/main/algos.py)                                     |  This file, `algos.py`, is a pivotal component of the Boggle game implementation. It houses various algorithms and key computational functions that optimize and enhance the game's performance. These algorithms are essential for efficiently generating valid words, finding possible moves, and implementing other computational aspects critical to the Boggle game's mechanics. They significantly contribute to the overall speed and responsiveness of the game.                                                                                                                                                                                                                                                                                                                                                                                                 

</details>

---

## 🚀 Getting Started



### 🔧 Installation

1. Clone the Boggle repository:
```sh
git clone https://github.com/adir-barak/Boggle.git
```

2. Change to the project directory:
```sh
cd Boggle
```

3. Install the dependencies:
```sh
pip install -r requirements.txt
```

### 🤖 Running Boggle

```sh
python main.py
```

### 🧪 Tests
```sh
pytest
```

---

## 🤝 Contributing

Contributions are always welcome! Please follow these steps:
1. Fork the project repository. This creates a copy of the project on your account that you can modify without affecting the original project.
2. Clone the forked repository to your local machine using a Git client like Git or GitHub Desktop.
3. Create a new branch with a descriptive name (e.g., `new-feature-branch` or `bugfix-issue-123`).
```sh
git checkout -b new-feature-branch
```
4. Make changes to the project's codebase.
5. Commit your changes to your local branch with a clear commit message that explains the changes you've made.
```sh
git commit -m 'Implemented new feature.'
```
6. Push your changes to your forked repository on GitHub using the following command
```sh
git push origin new-feature-branch
```
7. Create a new pull request to the original project repository. In the pull request, describe the changes you've made and why they're necessary.
The project maintainers will review your changes and provide feedback or merge them into the main branch.

---

## 📄 License

This project is licensed under the `ℹ️  MIT` License. See the [LICENSE-Type](LICENSE) file for additional info.

---

## 👏 Acknowledgments

`- ℹ️ Special thanks are owed to Arie Levental for the collaborative effort on this project, and acknowledgment goes to the Hebrew University for being a source of inspiration.`

---
