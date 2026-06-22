# Workshop Outline

## Event

**IGNITE Batavia Team - Universitas Negeri Jakarta**  
Theme: **Exploring the Potential of Intelligent Technologies**

## Audience

- Undergraduate engineering students
- Mostly new to Machine Learning
- Need a practical, visual, and low-math introduction
- Main outcome: participants experience how ML can read sensor data and visual scenes

## Duration

Total event: about 4 hours  
Machine Learning session: about 2-3 hours

Recommended ML session flow:

| Segment | Duration | Activity |
|---|---:|---|
| Opening and motivation | 10 min | Why intelligent vehicles need ML |
| Part 1: Tabular ML | 55-70 min | Battery SoC estimation walkthrough |
| Break / transition | 5-10 min | From sensor table to camera image |
| Part 2: Computer Vision | 60-75 min | YOLOv8 object detection inference |
| Wrap-up challenge | 10-15 min | Reflection and mini exercise |

## Learning Goals

By the end of the session, participants should be able to:

- Explain what Machine Learning does in simple terms.
- Identify **features**, **target**, **training data**, and **prediction** in an automotive use case.
- Run a tabular ML workflow for Battery State of Charge estimation.
- Explain the difference between image classification, object detection, and segmentation.
- Run pretrained YOLOv8 object detection on road images.
- Count detected objects and connect detection output to vehicle decision making.

## Workshop Storyline

The story is built around one question:

> How can a modern vehicle understand its own condition and its surrounding environment?

Part 1 answers the **inside-the-vehicle** question:

- Sensors record current, voltage, and temperature.
- ML estimates battery State of Charge.
- The vehicle can make energy-aware decisions.

Part 2 answers the **outside-the-vehicle** question:

- Cameras capture the road.
- YOLO detects people, vehicles, and traffic lights.
- The system can support safer driving decisions.

## Slide Plan

Total: **31 slides**

| Section | Slides | Focus |
|---|---:|---|
| Opening | 1-5 | Motivation and workshop map |
| ML Basics | 6-9 | Intuition, features, target, train/predict |
| Tabular ML: Battery SoC | 10-18 | Dataset, pipeline, model, evaluation, interpretation |
| Transition to Vision | 19-21 | Why cameras need CV |
| Computer Vision + YOLO | 22-29 | Classification vs detection vs segmentation, YOLO inference |
| Wrap-up | 30-31 | Vehicle intelligence pipeline and closing challenge |

## Practical Files

Existing:

- `EECCIS_UB_MALANG_SoC.ipynb`  
  Used for Battery State of Charge estimation practice.

New:

- `code/yolo_object_detection_workshop.ipynb`  
  Used for YOLOv8 object detection inference practice.

## Recommended Delivery Notes

- Keep theory short and concrete.
- Prefer “what the vehicle sees/knows/does” language.
- Use automotive examples before introducing ML terms.
- Pause after every code block and ask participants what changed.
- Do not emphasize model training details for YOLO; the workshop goal is inference and interpretation.
- For SoC, focus on the ML workflow rather than battery electrochemistry.

## Hands-on Milestones

Part 1: Battery SoC

- Load the battery datasets.
- Identify sensor columns as features.
- Identify `SOC_true` as the target.
- Train baseline models.
- Compare prediction against ground truth.
- Discuss what errors mean for an electric vehicle.

Part 2: YOLOv8

- Install and import Ultralytics.
- Load pretrained `yolov8n.pt`.
- Run inference on a road image.
- Visualize bounding boxes.
- Filter relevant road objects.
- Count detected objects.
- Try another road image independently.

## Suggested Closing Question

Ask participants:

> If you were building a small intelligent vehicle prototype, what sensors would you use, what would you predict, and what decision would the vehicle make?

