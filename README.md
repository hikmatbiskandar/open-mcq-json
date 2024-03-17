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

# Proposed Structure

example filename: `resources/My Exam/Revision 2009 Sample 1.json`

## Main Structure

```
{
  "version": "0.0.1",
  "author": "Hikmat bin Iskandar,
  "organization": "Hikmat's Company",
  "steps":
  [
    <refer to Steps object>
  ]
}

```

## Steps

Steps are also known as Questions, or Pages, depending on your use case. Basically represents each page that the question is presented to the screen.

```
{
  "question-key": "question-1",                   # anchor key for the question (optional) which another prior question can link back to
  "title": "Question #1",                         # the question's title
  "description": "The full descriptions",         # the full description
  
  "options": [                                    # options for this question
    <refer to Options object>
  ],

  "required_keys": [                              # in order to view this question, the user must own this keys
    "tag1","tag2"                                 # keys can be awarded by answering a prior question
  ],

  "image": "https://placehold.co/600x400",        # direct link to the image URL
  "tooltips": [                                   # list of tooltips to appear on top of the image
    <refer to Tooltips object>                     
  ]
}
```

## Options

```
"options": [
  "question": "What is A?",                   # a more simplified, direct question or instructions to appear before the options
  "answers": [
    "text":   "A is my answer",
    "key":    "user-picked-A",                # the key that can be used to access future questions (unique)
    "goto":   "question-1",                   # redirect user to go here
    "point"   1                               # the score ( >0 means the answer is answered correctly.)
  ]
]
```

## Tooltips

Tooltips are placed based on percentage coordinate in reference to the size of the image provided. As the sample below provides, 73.3, 3.5 means 73.3% from top of the image and 3.5% from the left of the image size.

```
"tooltips": [
    {
      "text": "Tooltip 1",
      "location": [
        90.8, /* x of image by percentage */
        34.4  /* y of image by percentage */
      ],
      "position": "bottom-center"
    },
    {
      "text": "Tooltip 2",
      "location": [
        53.0,
        70.2
      ],
      "position": "bottom-center"
    }
  ]

```


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
