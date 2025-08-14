# Data Structure & Format

## File Naming Convention

### Standard Format
```
[LANGUAGE]_[CATEGORY]_[SIGN_ID]_[SIGNER_ID]_[VARIANT].[EXTENSION]
```

### Multi-Camera Format
```
[LANGUAGE]_[SIGN_ID]_[SIGNER_ID]_[BOOTH]_[CAMERA]_[TAKE].[EXTENSION]
```

### Examples
- **Standard:** `KSL_WORD_HELLO_S001_V1.mp4`
- **Multi-camera:** `KSL_HELLO_S001_B1_C1_T01.mp4` (Booth 1, Camera 1, Take 1)
- **Motion data:** `KSL_PHRASE_HOWAREYOU_S025_V2.bvhx`
- **Metadata:** `KSL_EMOTION_HAPPY_S150_V1.json`

## Directory Structure

```
SignvrseDataset_v1.0/
├── videos/
│   ├── professional/
│   │   ├── booth1/
│   │   │   ├── camera1/
│   │   │   ├── camera2/
│   │   │   └── camera3/
│   │   └── booth2/
│   │       ├── camera1/
│   │       ├── camera2/
│   │       └── camera3/
│   ├── academic/
│   ├── media/
│   └── online/
├── motion_data/
│   ├── bvhx_files/
│   ├── facial_data/
│   └── validation/
├── metadata/
│   ├── annotations/
│   ├── demographics/
│   ├── quality_metrics/
│   └── calibration/
└── documentation/
    ├── specifications/
    ├── guidelines/
    └── changelog/
```

## BVHX Enhanced Format

### Standard BVHX Components
- Joint hierarchy and bone structure
- Frame-by-frame rotation data
- Root motion and translation

### Signvrse Enhancements
- Embedded facial landmark data (50 blendshapes)
- Expression classification metadata
- Quality confidence scores
- Temporal alignment markers

## Metadata Schema

### Core Metadata (Required)

```json
{
  "sign_id": "KSL_HELLO_001",
  "language": "KSL",
  "meaning": "Hello/Greeting",
  "category": "common_word",
  "duration_ms": 2500,
  "signer_id": "S001",
  "recording_date": "2025-07-11",
  "quality_score": 0.95,
  "validation_status": "approved"
}
```

### Technical Metadata

```json
{
  "video_specs": {
    "resolution": "1920x1080",
    "fps": 30,
    "codec": "H.264",
    "bitrate_mbps": 8.5
  },
  "motion_data": {
    "joint_count": 59,
    "facial_landmarks": 468,
    "capture_system": "Face Cap V1.9"
  },
  "processing": {
    "pipeline_version": "1.2",
    "processing_date": "2025-07-11",
    "quality_checks": ["resolution", "fps", "landmark_accuracy"]
  }
}
```

### Linguistic Metadata

```json
{
  "linguistic_features": {
    "grammatical_type": "noun",
    "handshape": "5-hand",
    "movement": "circular",
    "location": "neutral_space",
    "orientation": "palm_down",
    "facial_expression": "neutral",
    "regional_variant": "standard_KSL"
  },
  "complexity": {
    "difficulty_level": 2,
    "one_handed": false,
    "uses_facial": true,
    "body_movement": false
  }
}
```

## File Format Specifications

### Video Files
- **Primary Format:** MP4 with H.264 encoding
- **Naming:** Following multi-camera convention for synchronized captures
- **Quality:** Minimum 1080p, 30fps
- **Audio:** AAC encoding, 48kHz sample rate

### Motion Data Files
- **Format:** Enhanced BVHX with facial data integration
- **Content:** 59 joint skeletal data + 468 facial landmarks
- **Synchronization:** Frame-aligned with corresponding video files

### Metadata Files
- **Format:** JSON for structured data
- **Schema:** Three-tier system (Core, Technical, Linguistic)
- **Validation:** JSON Schema validation for consistency

### Calibration Files
- **Format:** JSON containing camera intrinsic/extrinsic parameters
- **Naming:** `[DATE]_booth[X]_calibration.json`
- **Content:** Camera matrices, reprojection errors, validation metrics

## Data Processing Pipeline

### Input Processing
1. **Multi-camera video ingestion**
2. **Synchronization validation**
3. **Quality assessment**
4. **Metadata extraction**

### Motion Data Generation
1. **2D pose estimation per camera**
2. **3D triangulation**
3. **Temporal smoothing**
4. **BVHX export with facial data**

### Validation and Export
1. **Cross-view consistency checks**
2. **Quality scoring**
3. **Final format conversion**
4. **Archive preparation**

## Storage Requirements

### Per Sign Estimate
- **Video files (3 cameras):** ~150MB (1080p, 30fps, 3 seconds)
- **Motion data:** ~5MB (BVHX with facial landmarks)
- **Metadata:** ~50KB (JSON files)
- **Total per sign:** ~155MB

### Full Dataset Estimate
- **20,000 signs:** ~3.1TB
- **With redundancy/backups:** ~6.2TB
- **Working storage:** ~10TB recommended

## Access Patterns

### Research Access
- **Batch download:** Full dataset packages
- **Selective access:** Query-based subset selection
- **Streaming:** Real-time processing pipelines

### Development Access
- **API endpoints:** RESTful access to metadata
- **File serving:** Direct video/motion file access
- **Preview system:** Low-resolution samples for browsing

---

[← Back to Technical Specs](technical-specs.md) | [Next: Content Specifications →](content-specifications.md)