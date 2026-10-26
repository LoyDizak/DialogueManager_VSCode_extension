# Godot Dialogue Manager - VS Code Extension

<p align="center">
  <img src="icon.png" alt="Logo" width="200"/>
</p>

<p align="center">
  <strong>A VS Code extension providing complete development support for Godot 4.x Dialogue Manager</strong>
</p>

<p align="center">
  Made by <a href=https://github.com/hakubox>hakubox</a>, translated by <a href=https://github.com/LoyDizak>Loy_Dizak</a> using AI
</p>

<p align="center">
  <a href="https://github.com/LoyDizak/DialogueManager_VSCode_extension">GitHub</a> •
  <a href="https://github.com/LoyDizak/DialogueManager_VSCode_extension/issues">Report an issue</a> •
  <a href="https://github.com/LoyDizak/DialogueManager_VSCode_extension/releases">Download</a>
</p>


## Features
### You can find full list of features on the [official DialogueManager github page](https://github.com/nathanhoad/godot_dialogue_manager)

## Quick Start

### 1. Install the extension

#### Method A: Install from the VS Code Marketplace
1. Open VS Code
2. Press `Ctrl+Shift+X` to open the Extensions view
3. Search for `Godot Dialogue Manager`
4. Click **Install**

#### Method B: Install manually from a `.vsix`
1. Download the latest `.vsix` file from [GitHub Releases](https://github.com/LoyDizak/DialogueManager_VSCode_extension/releases)
2. Press `Ctrl+Shift+P` in VS Code
3. Enter `Extensions: Install from VSIX...`
4. Select the downloaded `.vsix` file

### 2. Open a Godot project
Make sure your project includes the Dialogue Manager plugin and contains `.dialogue` files.

### 3. Start writing dialogue
Create or open a `.dialogue` file and write some dialogue! Here is an example:

```dialogue
~ start
# This is a test title

NPC: Hello! [#happy]
Player: Hello, may I ask...

- I want to buy something => shop
- I want to leave => END

~ shop
do! ShopManager.open_shop()
=> END
```

## Configuration

### Complete configuration example

```json
{
  // ========== Global class configuration ==========
  "dialogue.diagnostics.globalClasses": [
    "PlayerState",
    "AudioManager",
    "SaveManager"
  ],

  // ========== Global variable configuration ==========
  "dialogue.diagnostics.globalVariables": {
    "playerName": {
      "type": "String",
      "comment": "Player name"
    },
    "playerStats": {
      "type": "Dictionary",
      "schema": {
        "hp": { "type": "int" },
        "mp": { "type": "int" }
      }
    }
  },

  // ========== Custom tag configuration ==========
  "dialogue.diagnostics.customTags": {
    "happy": {
      "description": "Happy expression",
      "category": "face",
      "alias": ["joyful"]
    }
  },

  // ========== Tag category configuration ==========
  "dialogue.diagnostics.metadataCategories": {
    "face": {
      "icon": "😊",
      "description": "Expression"
    }
  },

  // ========== Other options ==========
  "dialogue.diagnostics.enableCustomTags": true,
  "dialogue.diagnostics.strictMode": false
}
```

## FAQ

### Q1: Why is my class missing from the completion list?
**A**: Make sure your class uses a `class_name` declaration:

```gdscript
# ✅ Correct
class_name PlayerState
extends Node

# ❌ Incorrect
extends Node
```

Alternatively, register the class globally, then restart VS Code or wait for the class cache to refresh.


### Q2: Why is cross-file title completion not working?
**A**: Make sure that:
1. The `import` statement is correct and uses a `res://` path
2. The imported `.dialogue` file has been opened to trigger scanning
3. The imported file contains a `~ xxx` title definition


### Q3: How can I disable specific checks?
**A**: Set the option in `settings.json`:

```json
{
  "dialogue.diagnostics.strictMode": false  // Disable strict mode
}
```


### Q4: Why are private members (starting with `_`) not displayed?
**A**: This is expected and follows GDScript visibility rules. To access a private member, enter its full name manually; it will not be completed automatically.


### Q5: Why is completion slow when opening a project for the first time?
**A**: The extension scans all GDScript files to build the class cache, which usually takes 2-5 seconds. Wait for `✅ Class cache initialization complete` in the console before using completion.


## License

MIT License - See the [LICENSE](LICENSE) file for details


## Acknowledgements
- Author of the original extension: [hakubox](https://github.com/hakubox)
- [Godot Engine](https://godotengine.org/)
- [Dialogue Manager Plugin](https://github.com/nathanhoad/godot_dialogue_manager) by [Nathan Hoad](https://nathanhoad.net/)
- [VSCode Extension API](https://code.visualstudio.com/api)


## Contact

- **GitHub Issues**: [Submit an issue](https://github.com/LoyDizak/DialogueManager_VSCode_extension/issues)
- **Author**: [hakubox](https://github.com/hakubox)
- **Email**: hakubox@outlook.com