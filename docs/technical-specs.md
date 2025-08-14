# Technical Specifications

## Video Requirements

| Parameter | Minimum | Preferred | Maximum |
|-----------|---------|-----------|---------|
| Resolution | 1080p (1920×1080) | 4K (3840×2160) | 8K |
| Frame Rate | 30 fps | 60 fps | 120 fps |
| Duration | 2 seconds | 3-5 seconds | 15 seconds |
| File Format | MP4 (H.264) | MP4 (H.265) | ProRes |
| Bitrate | 5 Mbps | 15 Mbps | 50 Mbps |
| Color Space | Rec. 709 | Rec. 2020 | P3 |

## Video Recording Setup

Motion-S implements multi-view capture to ensure signs are visible from multiple points of view, reducing occlusion and ambiguity, especially in hand movements.

### Camera Setup Configurations

| Setup | Number of Cameras | Use Case | Coverage Angle | Optimal Distance |
|-------|------------------|----------|----------------|------------------|
| Minimum Setup | 2-4 cameras | Basic 3D pose estimation in controlled environments | 90° separation (stereo) or 120° (3 cameras) | 2-3 meters |
| Standard Setup | 6-8 cameras | Robust sign capture with occlusion handling | 45-60° separation in semicircle | 2.5-4 meters |
| Professional Setup | 8-12 cameras | High-accuracy capture for complex signs and research | 30-45° separation, full circle | 3-5 meters |

### Camera Placement Specifications (Optimal 3 Cameras)

| Position | Height | Angle | Purpose |
|----------|--------|-------|---------|
| Front Center | Eye level (1.6m) | 0° | Primary frontal view, facial expressions |
| Side Left/Right | Shoulder level (1.4m) | ±90° | Profile movements, depth perception |

### Synchronization Requirements

- Frame-level synchronization across all cameras (±0.5 frames tolerance)
- Genlock or software synchronization required
- Unified timecode across all recording devices
- Minimum 100 Mbps network for real-time preview

### Lighting Configuration

- Uniform lighting across capture volume (±10% variance)
- Minimum 800 lux at signer position
- Color temperature: 5600K (daylight balanced)
- No harsh shadows on hands or face

## Audio Specifications

| Parameter | Specification |
|-----------|---------------|
| Sample Rate | 48 kHz |
| Bit Depth | 24-bit |
| Channels | Stereo (2.0) |
| Format | AAC, 320 kbps |
| Sync Tolerance | ±1 frame |

## Facial Capture Requirements

| Component | Specification |
|-----------|---------------|
| Supported Devices | iPhone X/XS/XR/11 series, iPad Pro 3rd gen |
| Blend Shapes | 50+ based on FACS system |
| Captured Data | Face expressions + eye motion + head position/rotation |
| Export Formats | ASCII-FBX, Text-based format |
| Capture Environment | Well-lit room, stable phone mount |
| Distance Requirements | Within 3D camera range (not too close/far) |
| Head Movement Limits | Avoid extreme up/down/sideways angles |
| Recording Duration | Unlimited (with purchase unlock) |
| Live Mode | Real-time streaming via IP connection |
| Post-Processing | Built-in smoothing (5% noise reduction) |

## 3D Pose Estimation Pipeline

| Stage | Process | Output | Quality Metric |
|-------|---------|--------|----------------|
| Calibration | Camera parameter estimation | Intrinsic/Extrinsic matrices | Reprojection error <1 pixel |
| Synchronization | Temporal alignment | Synchronized frames | Drift <0.5 frames |
| 2D Pose Detection | Pose estimation per view | 2D keypoints (body + hands) | Confidence >0.8 |
| Triangulation | 3D pose estimation from multiple views | 3D joint positions | Cross-view consistency >95% |
| Temporal Smoothing | Filtering and interpolation | Smooth 3D trajectories | Jitter <5mm between frames |
| Validation | Multi-view consistency check | Pose quality score | Reprojection error <10 pixels |

## Equipment Specifications

### Multiview Equipment Requirements

#### Camera System
- Minimum 6 synchronized 4K cameras (preferred 8 cameras)
- Matching camera models for color consistency
- Global shutter sensors to prevent rolling shutter artifacts
- Minimum 30fps, synchronized to ±0.5 frames
- SDI or ethernet connectivity for reliable synchronization

#### Capture Volume Setup
- Minimum 4m × 4m × 3m capture space
- Camera mounting: Professional tripods or ceiling rigs
- Calibration board (checkerboard pattern, minimum 1m × 1m)
- Reference markers for spatial calibration

#### Synchronization System
- Hardware genlock generator or software synchronization with sub-frame accuracy
- Centralized recording system with RAID storage
- Real-time preview monitoring for all camera angles

#### Lighting Array
- 6-8 LED panel lights (minimum 300W equivalent each)
- Softboxes or diffusion to prevent harsh shadows
- Consistent illumination across capture volume
- No flickering (use lights with >1000Hz PWM or constant current)

### Booth Configuration Specifications

#### Physical Booth Setup
- **Booth Dimensions:** 3m × 3m × 2.5m (L×W×H) minimum per booth
- **Walls:** One-way glass on operator side, green screen material on remaining walls
- **Flooring:** Non-reflective, neutral-colored surface (matte gray recommended)
- **Ventilation:** Quiet HVAC system to maintain comfort without audio interference

#### Equipment Layout Per Booth

##### Camera Array (3-Camera Orthogonal Setup)

**Front Camera (C1):**
- Position: 2.5m from signer, eye level (1.6m height)
- Angle: 0° (direct frontal view)
- Mount: Adjustable vertical/lateral on tripod or wall mount
- Primary purpose: Facial expressions, frontal sign execution

**Left Side Camera (C2):**
- Position: 2.5m from signer, shoulder level (1.4m height)
- Angle: 90° left (pure profile view)
- Mount: Adjustable vertical/lateral positioning
- Primary purpose: Hand depth, profile movements

**Right Side Camera (C3):**
- Position: 2.5m from signer, shoulder level (1.4m height)
- Angle: 90° right (pure profile view)
- Mount: Adjustable vertical/lateral positioning
- Primary purpose: Hand depth, profile movements, redundancy

##### Lighting Configuration

**3-Point Lighting System:**

**Key Light:** Front-facing softbox (300W LED equivalent)
- Position: 45° above front camera, 2m distance
- Softbox size: 60cm × 60cm minimum

**Fill Lights:** Two side softboxes (200W LED equivalent each)
- Position: Behind and slightly above side cameras
- Purpose: Eliminate shadows from side angles

**Lighting Requirements:**
- Color temperature: 5600K across all lights
- Consistent illumination: ±5% variance across signing space
- No flicker: >2000Hz PWM or constant current drivers

##### Furniture & Accessories
- **Adjustable Bar Stool:** Height range 60-80cm, swivel capability, neutral color
- **Teleprompter/Monitor:** 19" system positioned just below front camera lens
- **Anti-glare screen coating:** brightness adjustable to match ambient lighting

---

[← Back to Main Documentation](README.md) | [Next: Data Structure →](data-structure.md)