# Quiz Application Setup Guide

## 📁 Directory Structure

Set up your quiz files in this structure:

```
/your-project-directory/
├── index.html                 # Main quiz application
└── quizzes/                   # Quiz files directory
    ├── mlb_expert.json        # Expert baseball quiz
    ├── cybersecurity.json     # Cybersecurity quiz
    ├── networking_basics.json # Networking fundamentals
    └── ...                    # Add more quiz files
```

## 🔗 URL Patterns for Loading Quizzes

### 1. **Direct Quiz Name (Recommended for GitHub Pages)**

```
https://yourdomain.com/simplequizzer/?mlb_expert
https://yourdomain.com/simplequizzer/?cybersecurity
https://yourdomain.com/simplequizzer/?networking_basics
```

- **Format**: `?quiz_name`
- **Loads**: `./quizzes/quiz_name.json`
- **Best for**: GitHub Pages and clean URLs

### 2. **Explicit File Parameter**

```
https://yourdomain.com/simplequizzer/?file=mlb_expert
https://yourdomain.com/simplequizzer/?file=cybersecurity
```

- **Format**: `?file=filename`
- **Loads**: `./quizzes/filename.json`

### 3. **Remote Quiz URL**

```
https://yourdomain.com/simplequizzer/?quiz=https://api.example.com/quiz.json
```

- **Format**: `?quiz=full_url`
- **Loads**: External JSON file

### 4. **Base64 Encoded Data**

```
https://yourdomain.com/simplequizzer/?data=eyJ0aXRsZSI6Ik15IFF1aXoiLCAicXVlc3Rpb25zIjpbXX0=
```

- **Format**: `?data=base64_encoded_json`
- **Loads**: Embedded quiz data

## 📋 Quiz JSON Format

Each quiz file should follow this structure:

```json
{
  "title": "Expert Major League Baseball History",
  "questions": [
    {
      "question": "According to MLB Rule 6.03(a)(3), what happens if a batter enters the box with an illegal bat?",
      "options": [
        "A. The batter is out, runners return",
        "B. The play stands, but the batter is ejected",
        "C. The illegal bat penalty cannot be enforced after the play",
        "D. The umpire must declare the batter out"
      ],
      "answer": "C. The illegal bat penalty cannot be enforced after the play",
      "explanation": "Under Rule 6.03(a)(3), if a batter completes his at-bat and reaches first base safely, and the opposing team does not appeal the illegal bat before the next pitch or play, the illegal bat penalty cannot be enforced."
    }
  ]
}
```

### Required Fields:

- `questions` (array): List of question objects
- `question` (string): The question text
- `options` (array): Array of answer choices
- `answer` (string): Correct answer (must match one of the options exactly)

### Optional Fields:

- `title` (string): Quiz title (overrides default)
- `explanation` (string): Detailed explanation for each question

## 🎲 Randomization Features

The quiz application automatically:

- **Shuffles question order** each time a quiz starts
- **Randomizes answer options** while preserving correctness
- **Provides fresh experience** on every retake

## 🚀 Quick Start Examples

### For GitHub Pages:

1. Create `/quizzes/mlb_expert.json` with your quiz data
2. Share URL: `https://yourusername.github.io/yourrepo/?mlb_expert`
3. Users get randomized questions and answers automatically

### For Local Development:

1. Place quiz files in `/quizzes/` directory
2. Test with: `http://localhost:8080/?cybersecurity`
3. All features work the same as production

## 📤 Sharing Quizzes

The application provides multiple sharing options:

- **Base64 URLs**: Embed entire quiz in URL (good for small quizzes)
- **File URLs**: Reference quiz files (better for larger quizzes)
- **Copy to Clipboard**: Built-in sharing functionality

## 🔧 Troubleshooting

### Common Issues:

**404 Error on GitHub Pages:**

- ✅ Use `?quiz_name` format instead of `/quiz_name` paths
- ✅ Ensure quiz files are in `/quizzes/` directory
- ✅ Check file names match exactly (case-sensitive)

**Quiz Won't Load:**

- ✅ Validate JSON format using a JSON validator
- ✅ Ensure all required fields are present
- ✅ Check browser console for error messages

**Answers Not Randomizing:**

- ✅ Refresh the page to see new randomization
- ✅ Use "Retake Quiz" for fresh randomization
- ✅ Check that options array has multiple items

## 📈 Best Practices

1. **File Naming**: Use descriptive, URL-friendly names (e.g., `advanced_networking`, `security_fundamentals`)
2. **Quiz Size**: 10-50 questions work best for user engagement
3. **Answer Options**: 4 options per question is optimal
4. **Explanations**: Include detailed explanations for learning value
5. **Testing**: Always test quiz files before sharing URLs