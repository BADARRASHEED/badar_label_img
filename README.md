## Setup and Run LabelImg on Windows

### 1. Open the Project Folder

Open the LabelImg project folder in VS Code. Then open a terminal.

Make sure this folder contains `labelImg.py` and `resources.qrc`.

### 2. Create the Python Environment

Use Python 3.9 for this project.

```bat
conda create -p .venv python==3.9 -y
```

Activate the environment:

```bat
conda activate .venv/
```

Check the Python version:

```bat
python --version
```

The output should show `Python 3.9.x`.

### 3. Check the Requirements File

Open this file:

```text
requirements/requirements-linux-python3.txt
```

For this Windows setup, replace its contents with:

```text
PyQt5==5.15.9
lxml==4.9.3
```

Save the file. These versions avoid the old PyQt5 installation error.

### 4. Install Requirements

From the main project folder, run:

```bat
python -m pip install -r requirements/requirements-linux-python3.txt
```

The file name includes `linux`, but these packages also work on Windows.

### 5. Generate GUI Resources

Run this command from the main project folder:

```bat
pyrcc5 -o libs/resources.py resources.qrc
```

This prepares the icons and other interface resources. Usually, you only need to run it once during setup.

### 6. Set the Class Name

Open:

```text
data/predefined_classes.txt
```

For person annotation, remove the old class names and keep only:

```text
person
```

Save the file. Do not change the class order after starting annotation.

### 7. Run LabelImg

```bat
python labelImg.py
```

### 8. Annotate Images

1. Click **PascalVOC** to switch to **YOLO** mode.
2. Click **Open Dir** and select your images folder.
3. Click **Change Save Dir** and select an empty labels folder.
4. Press **W** and draw a tight box around a person.
5. Select `person` as the label.
6. Draw a separate box for every person.
7. Press **Ctrl + S** to save.
8. Press **D** for the next image or **A** for the previous image.

Labels are saved as separate `.txt` files. The original images stay unchanged.

Example:

```text
Images: 1.jpg
Labels: 1.txt
```

### Run the Project Again

Open a terminal in the main project folder and run:

```bat
conda activate .venv/
python labelImg.py
```

## Author

**Badar Rasheed Butt**  
AI Engineer
