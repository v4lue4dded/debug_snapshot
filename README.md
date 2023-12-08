# debugsnap

## Overview

**debugsnap** is a Python package designed to facilitate debugging by enabling the saving and loading of a **snapshot of the state of the local and global variables** that can then be used for debugging.

This tool is especially useful when you would like to use the functionally of **interactive python for debugging**.

For example in order to itterate on code in a function that is in a state that takes a long time to achieve.

Just **save a snapshot** using the debug console when you are in that state then load the snapshot whenever and as often as you want and itterate.

## Installation

To install debugsnap, run the following command:

```bash
pip install debugsnap
```

## Usage

To use debugsnap, follow these steps:

> ** Warning:** By default a new folder named `tmp_save_snapshot` will be created in your `~` directory and the shapshot files (containing the **global variables**, **local variables** and **information** about any **variable that could not be saved** for any reason) will be saved there. To change the storage location you have to provide a `storage_path`.

1. **Saving the Debugging Snapshot**:
   In your debug session, use the appropriate function to save the current snapshot. For example:
   ```python
    from debugsnap import save_snapshot
    save_snapshot(local_vars=locals(), global_vars=globals())
   ```

2. **Loading the Debugging Snapshot**:
   In a new Python session or an interactive environment, load the saved snapshot:
   ```python
    from debugsnap import load_snapshot
    global_vars, local_vars = load_snapshot()
    globals().update(global_vars)
    locals().update(local_vars)
   ```

# Snippets

In order to make the use of this package easier we suggest adding the following snippets to your VScode, by adding them to `/snippets/python.json` 
```json
    "Save Debug Snapshot": {
        "prefix": "save_snapshot",
        "body": [
            "from debugsnap import save_snapshot",
            "save_snapshot(local_vars=locals(), global_vars=globals())"
        ],
        "description": "Save the current state of local and global variables, excluding specific ones."
    },
    "Load Debug Snapshot": {
        "prefix": "load_snapshot",
        "body": [
            "from debugsnap import load_snapshot",
            "global_vars, local_vars = load_snapshot()",
            "globals().update(global_vars)",
            "locals().update(local_vars)"
        ],
        "description": "Load a saved state into the current global and local variables."
    }
```

- **Snapshot Saving**: Captures the current snapshot of your Python environment, including variables and their values.
- **Snapshot Loading**: Restores the saved snapshot in a new Python session, allowing for continued exploration and debugging.
- **Non-Picklable Object Handling**: Gracefully manages non-picklable objects, ensuring a robust saving process.

## Requirements

debugsnap requires Python 3.6 or later. Dependencies include:
- dill >= 0.3.0

## Contributing

Contributions to debugsnap are welcome!

## License

debugsnap is released under the MIT License. See the `LICENSE` file for more details.

## Contact

For questions or feedback, please contact v4lue4dded@gmail.com.

## Author

Developed by v4lue4dded. Visit the [GitHub repository](https://github.com/v4lue4dded/debugsnap) for more information and updates.
