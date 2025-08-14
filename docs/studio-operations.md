# Studio Operations Guide

## Studio Operators Protocol

### Pre-Session Setup (30 minutes)

#### Equipment Power-On Sequence
1. **Power on central recording workstation**
2. **Launch recording software** (OBS Studio/similar)
3. **Verify all 6 camera feeds active** (3 per booth)
4. **Test teleprompter systems** (both booths)

#### Camera System Verification
- ✅ Check camera sync indicators (green lights on all 6 cameras)
- ✅ Verify recording paths: `/recordings/[DATE]/booth1/` and `/recordings/[DATE]/booth2/`
- ✅ Test sample recording (5-second test on all cameras)
- ✅ Confirm timestamp synchronization across cameras

#### Lighting Validation
- ✅ Measure light levels with meter: 800+ lux at signer position
- ✅ Check for shadows on hands/face areas
- ✅ Verify color temperature consistency (5600K)

### Daily Calibration Checklist

#### Camera Calibration (Per Booth) - 10 minutes each
- ✅ Place calibration board at signer position
- ✅ Capture 10 frames from each camera angle
- ✅ Run auto-calibration software
- ✅ Verify reprojection error <1 pixel
- ✅ Save calibration files: `[DATE]_booth[X]_calibration.json`

#### Audio/Visual Sync Test
- ✅ Signer claps hands 3 times in each booth
- ✅ Verify audio-visual sync within ±1 frame
- ✅ Test teleprompter response time (<200ms)

### Recording Session Operations

#### Sign Recording Workflow (Per Sign)

**Pre-Recording (5 seconds):**
- Queue next sign word on teleprompter
- Verify signer ready position in all 3 camera views
- Check recording storage space (>1GB available)

**Recording Sequence:**

**START:** Press RECORD ALL button
- All 6 cameras begin recording simultaneously
- Teleprompter displays countdown: 3...2...1...
- Word appears with green border

**DURING:** Monitor quality indicators
- Watch for camera focus drift
- Check for occlusion warnings
- Monitor audio levels (if applicable)

**END:** Press STOP ALL when signer returns to neutral pose
- 2-second hold in neutral position required
- All cameras stop recording
- Files auto-saved with naming convention

#### Quality Control Checkpoints
- ✅ All 3 cameras captured full sign sequence
- ✅ No occlusion warnings triggered
- ✅ Hand visibility >90% in at least 2 cameras
- ✅ Facial expression clearly visible in front camera

### Equipment Troubleshooting Guide

#### Camera Issues

**Problem: Camera feed lost**
- Check USB/ethernet connection
- Restart camera software
- If persistent: Switch to backup camera

**Problem: Cameras out of sync**
- Stop all recording
- Restart sync software
- Re-run calibration if sync error >1 frame

#### Recording Issues

**Problem: File corruption**
- Check storage drive health
- Verify sufficient disk space
- Switch to backup recording drive

## Signers/Talent Protocol

### Pre-Recording Preparation (15 minutes)

#### Personal Setup

**Wardrobe Requirements:**
- Solid color clothing (avoid patterns, logos)
- Contrasting colors to skin tone
- No jewelry that interferes with hand tracking
- Hair secured away from face if long

**Position Setup:**
- Sit/stand at marked position in booth center
- Adjust stool height so arms move freely
- Test signing space - ensure no contact with walls/equipment
- Practice neutral "ready" position

### Sign Execution Guidelines

#### Optimal Signing Technique

**Spatial Requirements:**
- Keep all signing within 80cm x 80cm space in front of body
- Maintain consistent distance from cameras (2.5m)
- Face front camera for facial expressions
- Keep hands visible to side cameras

**Timing Protocol:**
1. **Ready Position:** Hands relaxed at sides or on lap
2. **Cue Recognition:** Wait for green border and countdown
3. **Sign Execution:** Clear, deliberate movements
4. **Hold Position:** Maintain final sign pose for 1 second
5. **Return to Neutral:** Smooth transition back to ready position
6. **Wait:** Remain still until next cue

**Performance Standards:**
- **Clarity:** Each sign must be distinct and well-formed
- **Consistency:** Repeat signs identically across takes
- **Speed:** Natural signing pace (not rushed or overly slow)
- **Expression:** Include appropriate facial expressions for context

### Communication Protocols

#### With Studio Operators

**Hand Signals (when audio communication unavailable):**
- 👍 **Thumbs up:** Ready to continue
- ✋ **Open palm raised:** Need a break
- 👉 **Pointing to camera:** Technical issue with specific camera
- 🔄 **Circular motion:** Request retake of last sign

#### Issue Reporting

**Technical Problems:**
- **If teleprompter malfunctions:** Raise both hands
- **If lighting changes:** Point to affected area
- **If equipment noise/distraction:** Cup ear and point to source

**Physical Comfort:**
- Request breaks every 30 minutes
- Report fatigue or strain immediately
- Communicate any discomfort with booth environment

### Performance Feedback System

#### Real-Time Feedback
- 🟢 **Green light on teleprompter:** Sign accepted
- 🟡 **Yellow light:** Acceptable but could improve
- 🔴 **Red light:** Retake required

#### Session Review
- Review selected recordings with operators
- Discuss areas for improvement
- Celebrate successful captures
- Plan adjustments for next session

## Technical Directors Protocol

### Equipment Procurement Specifications

#### Primary Cameras (6 units required)
**Model:** [Specific camera model TBD]
**Specifications:**
- 4K recording capability
- Minimum 60fps preferred
- Global shutter or high-speed rolling shutter
- Clean HDMI output
- Genlock capability for synchronization

#### Recording Infrastructure

**Workstation Specifications:**
- **CPU:** [High-performance multi-core processor]
- **RAM:** 64GB DDR4 minimum
- **Storage:**
  - 2TB NVMe SSD for active recording
  - 10TB RAID array for archival
  - Backup drives (2x 10TB external)
- **Graphics:** [Professional GPU for real-time processing]

### Software Configuration Requirements

#### Recording Software Stack
```
Primary Recording: OBS Studio (Multi-cam setup)
├── Camera Control: [Camera control software]
├── Sync Software: Tentacle Sync Studio
├── Storage Management: Custom Python scripts
└── Quality Control: OpenCV-based validation tools
```

### Quality Validation Workflows

#### Real-Time Validation Pipeline

**Recording Start**
├── Camera Sync Check (<0.5 frame drift)
├── Focus Validation (edge detection)
├── Lighting Consistency (±10% variance)
├── Storage Space Verification (>1GB available)
└── Backup System Status

**During Recording**
├── Frame Drop Detection
├── Audio-Visual Sync Monitor
├── Occlusion Warnings
├── Focus Drift Alerts
└── Recording Quality Metrics

**Recording End**
├── File Integrity Check
├── Metadata Generation
├── Backup Copy Creation
├── Quality Score Calculation
└── Next Recording Preparation

## Coordination Protocols

### Daily Briefing (15 minutes before each session)
- **Technical Director:** System status and any issues
- **Studio Operators:** Equipment readiness and calibration status
- **Interpreters:** Sign list review and special requirements
- **Signers:** Comfort, questions, and goal setting

### Quality Gates and Escalation

#### Quality Control Checkpoints
1. **Technical Gate:** All equipment operational and calibrated
2. **Recording Gate:** Each sign meets technical quality standards
3. **Linguistic Gate:** Sign accuracy validated by deaf community reviewers
4. **Final Gate:** Complete session review and approval

#### Escalation Procedures
- **Level 1:** Operator resolves (equipment adjustment, retake)
- **Level 2:** Technical Director involvement (system reconfiguration)
- **Level 3:** Session halt (major technical failure, safety concern)
- **Level 4:** Project management escalation (schedule impact, resource needs)

## Data Collection Protocols

### Professional Studio Recording

See [Technical Specifications](technical-specs.md) for detailed equipment requirements.

### Existing Dataset Integration

#### Processing Pipeline
1. **Source dataset evaluation and selection**
2. **Format conversion to Signvrse standards**
3. **Quality enhancement where possible**
4. **Metadata extraction and standardization**
5. **Validation against acceptance criteria**

## Safety and Compliance

### Health and Safety
- **Ergonomic considerations** for extended recording sessions
- **Lighting safety** - appropriate levels to prevent eye strain
- **Equipment safety** - proper mounting and electrical safety
- **Emergency procedures** - clear evacuation routes and contacts

### Data Protection
- **Secure storage** of all recorded material
- **Access controls** limiting who can view raw footage
- **Backup procedures** ensuring data integrity
- **Privacy compliance** with local data protection laws

---

[← Back to Quality Assurance](quality-assurance.md) | [Next: Privacy & Ethics →](privacy-ethics.md)