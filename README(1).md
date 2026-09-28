# 🩰 NatyaAI

> **AI-powered classical dance interpretation for preserving,
> understanding, and experiencing India's performing-arts heritage.**

NatyaAI is an AI-powered classical dance interpretation system that
combines **computer vision, pose estimation, hand tracking, movement
analysis, contextual knowledge, and Google Gemini** to interpret Indian
dance performances in real time.

The platform is designed to recognize full-body dance poses, hand
mudras, movements, and dance-form context, then turn those observations
into understandable captions, cultural meanings, story context, and
learning insights.

## ✨ Why NatyaAI?

Indian classical dance is a sophisticated visual language. A single
mudra or movement can carry different meanings depending on the **dance
form, pose, sequence, and narrative context**.

NatyaAI aims to bridge that gap:

**Dance Performance → Computer Vision → Movement & Mudra Recognition →
Contextual AI → Human-Readable Interpretation**

This makes traditional performances more accessible to students,
audiences, educators, researchers, and people discovering Indian
classical dance for the first time.

------------------------------------------------------------------------

## 🚀 Key Features

### 🎥 Real-Time Vision

-   Live camera-based dance analysis.
-   Full-body pose tracking using MediaPipe Pose Landmarker.
-   Hand tracking with 21 hand landmarks.
-   Visual skeleton and hand-landmark overlays.
-   Framing checks and vision telemetry for live analysis.

### 🤲 Mudra Intelligence

-   Hand landmark feature extraction.
-   Mudra classification.
-   Temporal filtering to reduce unstable frame-to-frame predictions.
-   Support for **Asamyuta** and **Samyuta** mudra data.
-   Context-aware interpretation rather than relying only on a gesture's
    name.

### 💃 Dance & Pose Recognition

-   Dance-form classification.
-   Classical dance pose recognition.
-   Movement feature extraction and classification.
-   Context from the selected dance tradition.
-   Structured data for dance forms, poses, movements, and stories.

### 🧠 Gemini-Powered Interpretation

NatyaAI uses Google Gemini on the server side for: - Live
interpretation. - Performance analysis. - Cultural grounding. - Story
and narrative interpretation. - Contextual meaning generation. -
Upload-based video analysis.

The application also contains an **offline/fallback interpretation
path** so the experience can continue using structured local knowledge
when Gemini is unavailable.

### 📹 Performance Analysis

-   Camera-based analysis.
-   Uploaded performance/video analysis.
-   Performance result views.
-   Extracted keyframes and MediaPipe landmarks.
-   AI-generated interpretation of detected performance events.

### 📚 Cultural Knowledge

The project includes structured cultural data for: - Indian dance
forms. - Dance poses. - Dance movements. - Asamyuta mudras. - Samyuta
mudras. - Traditional references. - Mythological stories and narrative
scenes.

### 🗂️ Dataset Management

The application includes a dedicated dataset-management workflow for: -
Dataset upload. - Video processing. - Frame extraction. - Landmark
extraction. - Dataset validation. - Dataset review. - Dataset
statistics. - Performance-result inspection.

------------------------------------------------------------------------

## 🧩 Technology Stack

  Layer             Technology
  ----------------- -------------------------------
  Frontend          React 19 + TypeScript
  Build Tool        Vite
  Styling           Tailwind CSS + custom CSS
  UI Icons          Lucide React
  Animation         Motion
  Computer Vision   MediaPipe Tasks Vision
  AI                Google Gemini API
  Backend           Node.js + Express
  Environment       dotenv
  Bundling          esbuild
  Package Manager   npm / Bun-compatible lockfile

------------------------------------------------------------------------

## 🏗️ System Architecture

``` text
                     ┌─────────────────────────┐
                     │       User / Dancer      │
                     └────────────┬────────────┘
                                  │
                         Camera / Video Upload
                                  │
                                  ▼
                     ┌─────────────────────────┐
                     │      React Frontend     │
                     │   Camera & UI Layer     │
                     └────────────┬────────────┘
                                  │
                                  ▼
                     ┌─────────────────────────┐
                     │     VisionCore Pipeline │
                     └────────────┬────────────┘
                                  │
              ┌───────────────────┼───────────────────┐
              ▼                   ▼                   ▼
        Pose Detector       Hand Detector      Framing Checker
              │                   │
              └───────────┬───────┘
                          ▼
               ┌──────────────────────┐
               │ Landmark Smoothing   │
               │ & Temporal Filtering │
               └──────────┬───────────┘
                          ▼
          ┌───────────────┼────────────────┐
          ▼               ▼                ▼
     Pose Classifier  Mudra Classifier  Movement Classifier
          │               │                │
          └───────────────┼────────────────┘
                          ▼
                 Dance Form Context
                          │
                          ▼
              ┌────────────────────────┐
              │ Structured Knowledge   │
              │ Mudras / Poses /       │
              │ Movements / Stories    │
              └────────────┬───────────┘
                           │
                           ▼
                 ┌──────────────────┐
                 │   Gemini Backend │
                 │ Contextual AI    │
                 └────────┬─────────┘
                          ▼
                 Live Caption / Meaning
                 Story / Cultural Context
```

------------------------------------------------------------------------

## 📁 Project Structure

``` text
.
├── src/
│   ├── components/
│   │   ├── CameraFeed.tsx
│   │   ├── OverlayCanvas.tsx
│   │   ├── LiveCaptionBar.tsx
│   │   ├── MudraPanel.tsx
│   │   ├── MudraDetailModal.tsx
│   │   ├── PerformanceRecorder.tsx
│   │   ├── PracticeMetricsCard.tsx
│   │   ├── ScholarChatModal.tsx
│   │   ├── StorySceneCard.tsx
│   │   └── dataset/
│   │
│   ├── config/
│   │   └── vision.ts
│   │
│   ├── data/
│   │   ├── dances/
│   │   ├── movements/
│   │   ├── mudras/
│   │   ├── poses/
│   │   └── stories/
│   │
│   ├── pages/
│   │   └── DatasetManager/
│   │
│   ├── services/
│   │   └── dataset/
│   │
│   ├── types/
│   │
│   ├── vision/
│   │   ├── dance/
│   │   ├── hands/
│   │   ├── movement/
│   │   ├── mudra/
│   │   ├── pipeline/
│   │   ├── pose/
│   │   ├── smoothing/
│   │   └── story/
│   │
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
│
├── server/
│   └── services/
│       └── gemini/
│           ├── analyzePerformance.ts
│           ├── culturalGrounding.ts
│           ├── liveInterpret.ts
│           ├── uploadGeminiVideo.ts
│           └── prompts/
│
├── server.ts
├── package.json
├── vite.config.ts
├── tsconfig.json
├── .env.example
└── README.md
```

------------------------------------------------------------------------

## ⚙️ Getting Started

### Prerequisites

Make sure you have:

-   **Node.js 18+**
-   npm
-   A modern browser with camera support
-   A **Google Gemini API key** for AI-powered interpretation

> Camera functionality requires browser permission. For production
> deployment, use HTTPS so browser camera APIs work reliably.

### 1. Clone the repository

``` bash
git clone https://github.com/<your-username>/natyaai.git
cd natyaai
```

### 2. Install dependencies

``` bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root:

``` env
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
APP_URL="http://localhost:3000"
```

You can also start from the provided example:

``` bash
cp .env.example .env
```

Then replace the placeholder Gemini key with your own API key.

> **Security:** Never commit `.env`, API keys, or other secrets to
> GitHub.

### 4. Start the development server

``` bash
npm run dev
```

The Express server starts the application and serves the Vite
development environment.

Open the local URL shown in the terminal, typically:

``` text
http://localhost:3000
```

------------------------------------------------------------------------

## 🧠 Gemini Integration

NatyaAI keeps the Gemini API interaction on the **server side** rather
than exposing the API key directly to the browser.

The backend provides endpoints for AI-assisted workflows such as:

``` text
POST /api/gemini/live-interpret
POST /api/gemini/upload-video
POST /api/gemini/analyze-performance
```

The backend also includes model fallback handling and an offline
interpretation path.

### Gemini responsibilities

Gemini is used for higher-level interpretation after computer-vision
evidence is collected. The system can provide measured evidence such as:

-   Detected dance form
-   Pose information
-   Mudra information
-   Movement events
-   Story context
-   Cultural context

This separation helps distinguish **computer-vision observations** from
**AI-generated cultural interpretation**.

------------------------------------------------------------------------

## 👁️ Computer Vision Pipeline

NatyaAI uses MediaPipe Tasks Vision for real-time body and hand
tracking.

### Body Tracking

The Pose Landmarker provides a **33-point body landmark
representation**, which is used by the vision pipeline for:

-   Pose recognition
-   Movement features
-   Body alignment
-   Dance-form features
-   Framing checks

### Hand Tracking

The Hand Landmarker provides **21 landmarks per hand**, supporting:

-   Finger geometry
-   Palm orientation
-   Mudra features
-   Temporal mudra classification

### Stabilization

Raw landmarks can be noisy during live camera movement. NatyaAI
therefore includes smoothing and temporal-processing modules such as:

-   `AdaptiveSmoother`
-   `LandmarkSmoother`
-   `OneEuroFilter`
-   `TemporalLandmarkBuffer`
-   `MudraTemporalFilter`

These components help produce a more stable visual and classification
experience.

------------------------------------------------------------------------

## 🩰 Dance Knowledge Layer

NatyaAI stores structured information about dance traditions and
performance vocabulary.

The knowledge layer includes:

``` text
Dance Forms
   ├── Region
   ├── Tradition
   ├── Movement Characteristics
   ├── Music Characteristics
   ├── Key Stances
   ├── Signature Mudras
   └── Cultural Sources

Mudras
   ├── Name
   ├── Sanskrit / Traditional Name
   ├── Hand Configuration
   ├── Meanings
   └── Usage

Poses
   ├── Pose Name
   ├── Body Configuration
   └── Dance Context

Movements
   ├── Movement Name
   ├── Features
   └── Dance Context

Stories
   ├── Scene
   ├── Narrative
   ├── Deity / Theme
   └── Rasa / Bhava
```

This structured layer provides grounding for the interpretation system
instead of treating every AI response as an unconstrained generation
task.

------------------------------------------------------------------------

## 🎭 Interpretation Flow

A typical live analysis follows this sequence:

1.  The dancer appears in front of the camera.
2.  MediaPipe detects body and hand landmarks.
3.  The vision pipeline smooths and stabilizes the landmarks.
4.  Pose, mudra, movement, and dance-form classifiers process the
    features.
5.  The detected information is matched with structured cultural
    knowledge.
6.  Relevant evidence is sent to the Gemini backend when AI
    interpretation is required.
7.  Gemini produces contextual explanations and interpretation.
8.  NatyaAI displays the result through live captions, panels, story
    cards, and performance views.

------------------------------------------------------------------------

## 📊 Dataset Workflow

The project includes tools for building and reviewing performance
datasets.

``` text
Video
  ↓
Upload
  ↓
Frame Extraction
  ↓
MediaPipe Landmark Extraction
  ↓
Validation
  ↓
Dataset Record Creation
  ↓
Review
  ↓
Analysis / Statistics
```

Dataset-related services include:

-   `extractFrames.ts`
-   `processVideo.ts`
-   `validateDataset.ts`
-   `createDatasetRecord.ts`
-   `uploadDataset.ts`
-   `analyzePerformance.ts`

------------------------------------------------------------------------

## 🛠️ Available Scripts

### Development

``` bash
npm run dev
```

Starts the development server.

### Production Build

``` bash
npm run build
```

Builds the Vite frontend and bundles the Node/Express server.

### Production Start

``` bash
npm start
```

Starts the built server.

### Type Checking

``` bash
npm run lint
```

Runs TypeScript checking without emitting files.

### Clean Build Output

``` bash
npm run clean
```

Removes generated build artifacts.

------------------------------------------------------------------------

## 🔐 Environment Variables

  -----------------------------------------------------------------------
  Variable                Required                Description
  ----------------------- ----------------------- -----------------------
  `GEMINI_API_KEY`        Yes for Gemini features Google Gemini API key

  `APP_URL`               Recommended             Application URL used by
                                                  the server/deployment
                                                  environment
  -----------------------------------------------------------------------

Example:

``` env
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
APP_URL="http://localhost:3000"
```

------------------------------------------------------------------------

## 🌏 Cultural & Educational Impact

NatyaAI is designed not only as a technical demonstration, but as a
bridge between **AI and cultural heritage**.

Potential applications include:

-   🎓 Classical dance education
-   🧑‍🏫 Teaching and classroom demonstrations
-   🌍 Introducing Indian dance to global audiences
-   🏛️ Digital cultural-heritage projects
-   🔬 Dance research and documentation
-   🎭 Audience interpretation during performances
-   📱 Interactive cultural-learning experiences

The long-term vision is to help make India's diverse performing-arts
traditions more **discoverable, understandable, and digitally
accessible** while keeping cultural context central to the experience.

------------------------------------------------------------------------

## 🔭 Future Scope

Possible future improvements include:

-   More robust multi-dancer tracking.
-   Expanded support for regional and classical traditions.
-   Improved sequence-level movement recognition.
-   More practitioner-reviewed cultural grounding.
-   Multilingual interpretation.
-   Mobile and progressive-web-app optimization.
-   Larger annotated dance-performance datasets.
-   Personalized learning and practice feedback.
-   Improved evaluation metrics for pose, movement, and mudra
    recognition.
-   Real-time performance timelines and event visualization.

------------------------------------------------------------------------

## ⚠️ Important Limitations

NatyaAI is an AI-assisted interpretation system, not a replacement for a
trained classical-dance practitioner.

Dance gestures and mudras can have **multiple meanings depending on
tradition, choreography, sequence, and context**. AI-generated
interpretations should therefore be treated as an assistive explanation
and should be validated against authoritative cultural sources and
practitioner knowledge.

Computer-vision performance can also vary with:

-   Camera angle
-   Lighting
-   Occlusion
-   Distance from camera
-   Clothing
-   Movement speed
-   Multiple people in the frame
-   Hand visibility

------------------------------------------------------------------------

## 🤝 Contributing

Contributions are welcome.

A typical contribution workflow:

``` bash
git checkout -b feature/your-feature
```

Make your changes, test them, and then submit a pull request.

When contributing cultural knowledge or interpretation logic, please
provide appropriate references and, where possible, seek review from
qualified practitioners or reliable cultural institutions.

------------------------------------------------------------------------

## 📜 License

A license has not yet been specified for this repository.

If you plan to publish the project publicly, add an appropriate
`LICENSE` file before distributing the code.

------------------------------------------------------------------------

## ❤️ Vision

> **Preserve tradition. Understand movement. Connect generations.**

NatyaAI explores how artificial intelligence can be used not simply to
recognize movement, but to help people **understand the cultural
language behind the movement**.

By bringing computer vision and contextual AI together with India's
classical dance traditions, NatyaAI aims to turn cultural heritage into
an interactive learning experience for the next generation.

------------------------------------------------------------------------

### Built with ❤️ for Indian Classical Dance & Cultural Heritage
