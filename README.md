# JSON Specification for Interactive Questionnaires with Scoring and Branching Pathways
## by Hikmat bin Iskandar

This JSON schema defines a convention for representing A/B/C/D questionnaires with scoring, pathways based on answers, and tooltips with attached images. It aims to standardize the format for such questionnaires, making it easier to implement them across various applications and platforms.

# Features

- Define A/B/C/D questions with scoring criteria for each answer option.
- Specify pathways based on answers to skip or visit certain questions.
- Associate tooltip images with specific questions for visual representation.
- (optional) File to browse json files and load into exam UI.
- (optional) Send POST to defined location with exam results.
- (optional) Apply different themes and gamification methodologies to the same JSON.
- (optional) Can also serve as a step-by-step documentation website manual/documentation

# Directory Structure

The files will be organized in this manner:

```
../
resources/                       -- store all exam json's here.
resources/<exam name>
resources/<exam name>/<revision> -- versions/variations
index.html
browser.html
viewer.html
assets/js/
assets/img/
```

# Usage
Developers can use this JSON schema to represent complex questionnaires in a structured format, enabling easy management of scoring, pathways, and tooltip images associated with each question.

# License
This project is licensed under the MIT License.
