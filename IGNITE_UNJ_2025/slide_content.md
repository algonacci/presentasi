# Slide Content

## Slide 1 - Title

**Exploring the Potential of Intelligent Technologies**  
Machine Learning for Intelligent Vehicles

Visual idea: Electric vehicle silhouette with sensor waves, camera view, and battery icon.

Presenter notes:  
Open with the big idea: modern vehicles are no longer just mechanical systems. They sense, estimate, detect, and decide. Tell participants that today is not about becoming ML experts in one session, but about getting a direct first experience with ML workflows.

---

## Slide 2 - Why Are Vehicles Becoming Intelligent?

- Roads are dynamic
- Energy is limited
- Safety decisions must be fast
- Sensors generate huge data

Visual idea: Four icons: road, battery, shield, sensor.

Presenter notes:  
Frame intelligence as a practical need. A vehicle must understand both its internal condition and its environment. Avoid abstract AI claims; keep it grounded in real vehicle problems.

---

## Slide 3 - Workshop Journey

Inside the vehicle:

**Battery sensors -> SoC estimation**

Outside the vehicle:

**Camera image -> Object detection**

Visual idea: Split screen, left battery dashboard, right road camera with boxes.

Presenter notes:  
Explain the two-part structure. The first part uses tabular sensor data. The second part uses images. Both follow the same ML idea: input data goes in, useful prediction comes out.

---

## Slide 4 - What Will You Build Today?

- Predict battery State of Charge from sensor data
- Detect road objects using YOLOv8
- Connect predictions to vehicle decisions

Visual idea: Simple pipeline: data -> model -> prediction -> action.

Presenter notes:  
Use the word “build” lightly. Participants will run and modify notebooks, not train a production autonomous driving model. The goal is confidence and intuition.

---

## Slide 5 - What Is Machine Learning?

Traditional programming:

**Rules + Data -> Answer**

Machine Learning:

**Data + Answer examples -> Learned pattern**

Visual idea: Two simple flow diagrams.

Presenter notes:  
Give a simple analogy: instead of writing every rule for battery behavior or road objects, we let a model learn patterns from examples. Keep this slide short.

---

## Slide 6 - ML in an Intelligent Vehicle

Examples:

- Estimate battery charge
- Detect cars and pedestrians
- Predict maintenance risk
- Decide when to slow down

Visual idea: Car surrounded by ML tasks.

Presenter notes:  
Connect ML to engineering systems. ML is not magic; it is one component inside a larger system with sensors, software, and control logic.

---

## Slide 7 - The Four Words We Need

| Word | Simple Meaning | Vehicle Example |
|---|---|---|
| Feature | Input data | Current, voltage, temperature |
| Target | What we want | State of Charge |
| Training | Learning from examples | Fresh battery data |
| Prediction | Model output | Estimated SoC |

Visual idea: Table with icons.

Presenter notes:  
Tell participants these four words are enough to follow most of today’s workflow. Use the battery case immediately so the terms are not abstract.

---

## Slide 8 - Supervised Learning Intuition

We show the model many examples:

**Sensor readings -> Known SoC**

Then ask it:

**New sensor readings -> Estimated SoC**

Visual idea: Notebook-like rows flowing into a model box.

Presenter notes:  
Avoid formulas. Emphasize examples and labels. If participants understand “practice questions with answer keys,” supervised learning will feel natural.

---

## Slide 9 - Part 1: Battery State of Charge

Question:

**Can a vehicle estimate battery SoC from sensor data?**

Visual idea: EV dashboard battery gauge.

Presenter notes:  
Introduce SoC as similar to a fuel gauge, but harder because batteries behave differently depending on current, voltage, temperature, and aging.

---

## Slide 10 - Why SoC Matters

- Driver range estimation
- Energy management
- Battery safety
- Charging strategy

Visual idea: Battery icon connected to range, charger, warning, route.

Presenter notes:  
Make it concrete: if SoC is wrong, the vehicle may overestimate range, charge inefficiently, or make poor energy decisions.

---

## Slide 11 - Our Sensor Table

Dataset columns:

- Time
- Current
- Voltage
- Temperature

Visual idea: Small dataframe screenshot mockup.

Presenter notes:  
Point out that this is tabular data, like Excel. Many engineering ML problems begin exactly like this: rows are measurements, columns are variables.

---

## Slide 12 - From Sensor Data to ML Data

Features:

`Current`, `Voltage`, `Temperature`, `cum_charge`

Target:

`SOC_true`

Visual idea: Data table with feature columns highlighted blue and target highlighted green.

Presenter notes:  
Explain that the model does not know what is important by itself. We choose useful inputs, then let the algorithm learn the relationship to the target.

---

## Slide 13 - Notebook Walkthrough: Load Data

Practice checkpoint:

```python
df_aged = pd.read_csv(...)
df_fresh = pd.read_csv(...)
df_ocv = pd.read_csv(...)
```

Visual idea: Three dataset boxes.

Presenter notes:  
Tell participants to first inspect shape, columns, and a few rows. Before modelling, always know what data you have.

---

## Slide 14 - Notebook Walkthrough: Create SoC Label

Idea:

**Current over time -> charge used -> SoC estimate**

Visual idea: Current-time curve turning into battery percentage.

Presenter notes:  
Keep this intuitive. Current flowing over time changes the battery charge. The notebook uses this idea to create `SOC_true`, then ML tries to learn it from sensor features.

---

## Slide 15 - Train and Test Split Story

Training:

**Fresh battery data**

Testing:

**Aged battery data**

Visual idea: Two batteries, one new and one older.

Presenter notes:  
This is a strong automotive story. A model trained on one condition may perform differently on another condition. That is why testing matters.

---

## Slide 16 - Model 1: Random Forest

Random Forest intuition:

Many decision trees vote together.

Visual idea: Several small trees pointing to one SoC gauge.

Presenter notes:  
No need to explain tree splitting deeply. Say it is a popular model for tabular data because it can learn nonlinear relationships and is fairly easy to use.

---

## Slide 17 - Model 2: XGBoost

XGBoost intuition:

Many small models improve each other step by step.

Visual idea: Model blocks stacked like upgrades.

Presenter notes:  
Explain XGBoost as a stronger tabular baseline often used in competitions and industry. Avoid optimization details.

---

## Slide 18 - How Do We Read Results?

Useful questions:

- Is prediction close to real SoC?
- Where does the model make errors?
- Is it reliable on aged battery data?

Visual idea: True vs predicted line chart.

Presenter notes:  
Shift focus from “highest score” to engineering meaning. In vehicles, an error is not just a number; it affects range, safety, and user trust.

---

## Slide 19 - Model Interpretation with SHAP

Question:

**Which sensor values influenced the prediction most?**

Visual idea: Bar chart of feature importance.

Presenter notes:  
Introduce interpretation as asking the model “what did you pay attention to?” This is useful in engineering because we need to debug and trust systems.

---

## Slide 20 - Transition: From Battery Sensors to Road Cameras

Inside:

**Numbers in a table**

Outside:

**Pixels in an image**

Visual idea: Table rows morphing into image pixels.

Presenter notes:  
Make the bridge explicit. Both are data. The difference is the structure: tabular ML reads columns, computer vision reads spatial patterns in images.

---

## Slide 21 - Why Computer Vision for Vehicles?

Vehicles need to notice:

- People
- Cars
- Motorcycles
- Buses and trucks
- Traffic lights

Visual idea: Road scene with labeled objects.

Presenter notes:  
Keep this grounded in perception. Before a vehicle can decide, it must know what is around it.

---

## Slide 22 - Three Computer Vision Tasks

Classification:

**What is in the image?**

Detection:

**What and where?**

Segmentation:

**Which pixel belongs to what?**

Visual idea: Same road image shown in three styles.

Presenter notes:  
Spend a little time here because it clears up common confusion. Today’s practical focus is detection because vehicles need object location.

---

## Slide 23 - Object Detection Output

For each object:

- Class name
- Bounding box
- Confidence score

Visual idea: Person box, car box, confidence labels.

Presenter notes:  
Explain confidence as the model’s score, not absolute truth. A high score means the model is more confident, but outputs still need engineering judgment.

---

## Slide 24 - Meet YOLOv8

YOLO:

**You Only Look Once**

Today:

**Pretrained YOLOv8n for inference**

Visual idea: Camera image -> YOLO -> boxes.

Presenter notes:  
Clarify that we are not training YOLO today. We use a pretrained model so participants can focus on inference, visualization, and interpretation.

---

## Slide 25 - Why Pretrained Models?

Pretrained means:

- Already learned from many images
- Ready for common objects
- Good for demos and prototypes

Visual idea: Large image dataset feeding a ready model.

Presenter notes:  
Make the tradeoff clear. Pretrained models are fast to try, but may need retraining or fine-tuning for specialized local road conditions.

---

## Slide 26 - YOLO Practical Pipeline

1. Install library
2. Load model
3. Load image
4. Run inference
5. Visualize boxes
6. Count objects

Visual idea: Six-step horizontal pipeline.

Presenter notes:  
This slide maps directly to the notebook. Participants should know what step they are currently running.

---

## Slide 27 - Objects We Care About

Workshop classes:

- Person
- Car
- Motorcycle
- Bus
- Truck
- Traffic Light

Visual idea: Six object icons.

Presenter notes:  
Explain that object filtering is important. A production system may ignore irrelevant classes and focus only on objects related to driving decisions.

---

## Slide 28 - From Detection to Decision

Example:

Detected:

**person ahead + traffic light + cars**

Possible decision:

**slow down, keep distance, alert driver**

Visual idea: Detection boxes leading into decision module.

Presenter notes:  
Be careful not to imply YOLO alone drives the vehicle. YOLO detects objects. A separate decision system uses detection plus other data.

---

## Slide 29 - Practical Notebook Challenge

Try:

- Change the input image
- Adjust confidence threshold
- Count only vehicle classes
- Compare crowded vs empty road

Visual idea: Checklist beside notebook screenshot.

Presenter notes:  
This is where participants become active. Encourage exploration. Ask them to predict what will happen before running each change.

---

## Slide 30 - Big Picture: Intelligent Vehicle System

Sensors:

**Battery + camera + radar**

ML:

**Estimate + detect + predict**

Decision:

**manage energy + improve safety**

Visual idea: Full vehicle intelligence architecture.

Presenter notes:  
Tie both parts together. SoC estimation and object detection are different tasks, but both support intelligent decision making.

---

## Slide 31 - Closing Reflection

Ask yourself:

**What data can I collect?**  
**What should the model predict?**  
**What decision will use that prediction?**

Visual idea: Three question cards around a small vehicle prototype.

Presenter notes:  
End with an engineering mindset. A useful AI project starts from a real decision, not from a model name.

