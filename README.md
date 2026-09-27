# Day 3 --- Make It Decide

Day 3 moves from **computer vision** to **AI model inference and
decision-making**.

Day 2 taught the machine to see:
`Image → OpenCV / YOLO / MediaPipe → Information`

Day 3 teaches the next step:
`Information → AI Model → Prediction → Confidence → Decision`

------------------------------------------------------------------------

## 1. What you need

Use **VS Code** and its built-in terminal.

Your folder should look like:

``` text
Day-3/
│
├── .venv/
├── 01_test_ai.py
├── 02_first_model.py
├── 03_text_classification.py
├── 04_image_classification.py
├── 05_image_decision.py
│
└── images/
```

`.venv` is the Python virtual environment for this project. It keeps Day
3's Python packages separate from other projects.

------------------------------------------------------------------------

## 2. Open the Day-3 terminal

In VS Code:

`File → Open Folder → Day-3`

Then:

`Terminal → New Terminal`

Check your current location:

``` powershell
pwd
```

You should be inside the `Day-3` folder.

------------------------------------------------------------------------

## 3. Create the virtual environment

Run this **only the first time**:

``` powershell
python -m venv .venv
```

This creates the `.venv` folder.

### Activate it

``` powershell
.venv\Scripts\activate
```

When it is active, the terminal starts with:

``` text
(.venv) PS C:\...\Day-3>
```

This means commands such as `python` and `pip` are using the Day-3
environment.

### Leave the virtual environment

``` powershell
deactivate
```

This does not delete `.venv`.

### Leave the Day-3 folder

``` powershell
cd ..
```

`cd ..` moves one folder upward.

------------------------------------------------------------------------

## 4. Install the required packages

With `.venv` activated:

``` powershell
python -m pip install --upgrade pip
pip install transformers torch
```

### What are these?

-   **Transformers** --- Hugging Face's library for using pretrained AI
    models.
-   **PyTorch (`torch`)** --- the machine-learning framework used by
    many AI models.
-   **pip** --- Python's package installer.

You do not need to manually download a model for the first exercises.
The Transformers library can download the required pretrained model when
it is first used.

------------------------------------------------------------------------

# The Five Programs

## 01 --- `01_test_ai.py`

### Purpose

Check that your AI environment works and run your **first pretrained
model**.

### What it does

The program creates a Hugging Face `pipeline` for sentiment analysis.

The basic flow is:

``` text
Text
 ↓
Pretrained Model
 ↓
Prediction
 ↓
Label + Score
```

For example:

``` text
"I love robotics."
        ↓
    POSITIVE
        ↓
     0.99...
```

### Main concept

**Pretrained model:** a model that has already been trained on data by
someone else.

You are using the model, not training it yourself.

Run it with:

``` powershell
python 01_test_ai.py
```

------------------------------------------------------------------------

## 02 --- `02_first_model.py`

### Purpose

Understand the **model output**.

Instead of only printing the result, this program separates:

-   the input
-   the predicted label
-   the confidence/score

The result generally looks like:

``` text
Label: POSITIVE
Confidence: 0.99
```

### Main concept

A model's output contains information that your Python program can use.

The important Python idea is accessing values from the returned result,
such as:

``` text
result → label
result → score
```

Run:

``` powershell
python 02_first_model.py
```

------------------------------------------------------------------------

## 03 --- `03_text_classification.py`

### Purpose

Turn an AI prediction into a **decision**.

The program asks you for text, sends it to the model, and checks the
prediction and confidence.

Conceptually:

``` text
User Input
    ↓
AI Model
    ↓
Prediction
    ↓
Confidence
    ↓
if / else
    ↓
Decision
```

For example:

``` text
Input
 ↓
POSITIVE
 ↓
Confidence = 0.95
 ↓
Confidence > 0.80
 ↓
Decision: Positive
```

If the confidence is too low, the program can choose:

``` text
Decision: Uncertain
```

### Important distinction

The **AI model makes the prediction**.

Your **Python program applies the rule and makes the decision**.

Run:

``` powershell
python 03_text_classification.py
```

Try different sentences.

------------------------------------------------------------------------

# 04 --- `04_image_classification.py`

### Purpose

Move from **text AI** to **vision AI**.

Create an `images` folder and put an image inside it:

``` text
images/
└── test.jpg
```

The program uses an image-classification model.

The flow becomes:

``` text
Image
 ↓
Pretrained Vision Model
 ↓
Possible Labels
 ↓
Scores
```

For example:

``` text
cat       → 0.73
tiger cat → 0.12
other     → ...
```

### Important difference from YOLO

You used YOLO on Day 2.

**YOLO:**

``` text
Image
 ↓
Find objects
 ↓
Object + Bounding Box + Confidence
```

**Image classification:**

``` text
Image
 ↓
What does this image represent?
 ↓
Label + Score
```

Image classification normally does not tell you where the object is.

Run:

``` powershell
python 04_image_classification.py
```

------------------------------------------------------------------------

# 05 --- `05_image_decision.py`

### Purpose

Combine **vision + prediction + decision**.

The program takes the best image prediction and checks its confidence.

Conceptually:

``` text
Image
 ↓
Vision Model
 ↓
Prediction
 ↓
Confidence
 ↓
Decision Rule
 ↓
"Confident" / "Not confident"
```

For example:

``` text
Prediction: dog
Confidence: 0.91

        ↓

Confidence > 0.70

        ↓

Decision: I am confident
```

This is the basic idea behind a machine that does something based on
what it sees.

Run:

``` powershell
python 05_image_decision.py
```

------------------------------------------------------------------------

# Key Concepts

## Model

A trained mathematical system that produces predictions from input data.

## Pretrained Model

A model that has already been trained. You can use it directly for
inference.

## Inference

Using a trained model to produce a prediction from new input.

``` text
New Input
   ↓
Trained Model
   ↓
Prediction
```

## Prediction

The model's output about what it thinks the input represents.

## Confidence / Score

A numerical score associated with a prediction.

It should not automatically be treated as a guaranteed probability of
being correct.

## Decision

A rule in your program that uses the model's output.

Example:

``` text
IF confidence > threshold
        ↓
      ACT
ELSE
        ↓
      WAIT
```

------------------------------------------------------------------------

# How Day 3 Connects to Day 2

### Day 2

``` text
Camera
 ↓
OpenCV
 ↓
YOLO / MediaPipe
 ↓
"What do I see?"
```

### Day 3

``` text
What I see
 ↓
AI Model
 ↓
"What does it mean?"
 ↓
Prediction
 ↓
Confidence
 ↓
Decision
```

### Eventually, robotics

``` text
Camera
 ↓
Computer Vision
 ↓
AI Model
 ↓
Prediction
 ↓
Decision Logic
 ↓
Robot Controller
 ↓
Motor / Servo / Action
```

This is the basic **Vision → AI → Decision** pipeline.

------------------------------------------------------------------------

# Normal Day-3 Workflow

### First time

``` powershell
cd Day-3
python -m venv .venv
.venv\Scripts\activate
python -m pip install --upgrade pip
pip install transformers torch
```

### Every later session

``` powershell
cd Day-3
.venv\Scripts\activate
```

Then run whichever program you are working on:

``` powershell
python 01_test_ai.py
```

or:

``` powershell
python 02_first_model.py
```

etc.

### When finished

``` powershell
deactivate
```

------------------------------------------------------------------------

# Recommended Learning Order

Do not skip directly to the final program.

``` text
01_test_ai.py
      ↓
Understand pretrained models
      ↓
02_first_model.py
      ↓
Understand model output
      ↓
03_text_classification.py
      ↓
Understand prediction → decision
      ↓
04_image_classification.py
      ↓
Move from text → vision
      ↓
05_image_decision.py
      ↓
Vision → prediction → decision
```

By the end of these five programs, the important idea to understand is:

> **A pretrained AI model produces information; your program can use
> that information to make a decision.**
# Day-3
