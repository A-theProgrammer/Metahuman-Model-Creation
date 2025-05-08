# Metahuman Motion Editing in Unreal Engine 5.5

## 📌 Project Overview

This project demonstrates advanced motion editing techniques in **Unreal Engine 5.5**, focusing on animation retargeting and facial performance capture. The project showcases how to transform motion capture data into polished character animations with realistic facial expressions.

The primary goals of this project are:

- Demonstrate effective retargeting of motion capture data to Metahuman skeletons
- Implement realistic facial animation using Metahuman performance capture
- Create a seamless workflow from raw mocap to final animation

Through this implementation, the project provides a comprehensive framework for character animation in UE5.5 that maintains the original motion intent while enhancing realism and expressiveness.

## 🧰 Features Implemented

### ✅ Motion Capture Retargeting

The project implements a robust retargeting system that transfers mocap animations to different character skeletons:

- **IK Rig-based retargeting** to map source animations to custom skeletons
- **Skeleton mismatch correction** to handle differences in bone structure
- **Motion artifact removal** to eliminate foot sliding and other common issues
- **Chain-based mapping** for precise control over specific body regions

### ✅ Motion Editing & Refinement

Raw mocap data is refined through several techniques:

- **Motion Warping** to ensure accurate ground contact and interaction with environment
- **Animation concatenation** to seamlessly blend multiple animation segments
- **Curve-based editing** to smooth out noisy joints, particularly in fingers and hands
- **Custom Blend Spaces** for fluid transitions between different motion states

### ✅ Metahuman Facial Animation

The project features advanced facial animation using Metahuman:

- **LiveLink Face integration** for real-time facial performance capture
- **Audio-driven animation** that synchronizes facial movements with dialogue
- **Blendshape refinement** for enhanced micro-expressions and emotional fidelity
- **Control Rig manipulation** for precise control over facial features

## 🚀 Installation & Setup

### Prerequisites

- **Unreal Engine 5.5** (Download from [Epic Games Launcher](https://www.unrealengine.com/))
- Windows 10 or later (MacOS support limited)
- Minimum 16 GB RAM
- GPU: NVIDIA GTX 1070/AMD Radeon RX 5700 or better (RTX 3060/AMD Radeon 6700 XT recommended)
- 50GB free disk space
- Required Plugins (all available through Epic Games Marketplace):
  - **Metahuman SDK**
  - **LiveLink** and **LiveLink Face** (for facial capture)

### Getting Started

#### Step 1: Clone the Repository

```bash
git clone https://github.com/A-theProgrammer/Metahuman-Model-Creation.git
cd Metahuman-Model-Creation
```

#### Step 2: Install Unreal Engine 5.5

1. Download and install the [Epic Games Launcher](https://www.epicgames.com/store/en-US/download)
2. In the launcher, go to the **Unreal Engine** tab
3. Click **Install Engine** and select version **5.5**
4. Follow the installation instructions

#### Step 3: Install Required Plugins

1. Open the Epic Games Launcher
2. Navigate to the **Marketplace** tab
3. Search for and install:
   - Metahuman SDK
   - LiveLink

#### Step 4: Open the Project

1. Launch Unreal Engine 5.5
2. Click **Browse** and navigate to the cloned project directory
3. Open the `MotionEditing.uproject` file
4. When prompted about missing modules, click **Yes** to rebuild them

#### Step 5: Download Large Assets (LFS)

Some large assets are managed with Git LFS. If not downloaded automatically:

```bash
# Install Git LFS if you don't have it
git lfs install

# Pull LFS content
git lfs pull
```

## 🎮 Using the Project

### Opening the Demo Scene

1. In the Content Browser, navigate to `Content/Levels`
2. Open the `MainDemo` level
3. Press **Play** to see the demo in action

### Exploring Key Components

#### Animation Blueprint
1. Navigate to `Content/Characters/Animations/BP_MainCharacter_AnimBlueprint`
2. Open to explore the animation state machine and blend spaces

#### Retargeting Setup
1. Check `Content/Characters/IK_Rigs` for the IK Rig assets
2. Study `Content/Characters/RetargetingAssets` for retargeting configurations

#### Metahuman Facial Setup
1. Open `Content/Characters/Metahumans/FacialRig`
2. Study the LiveLink configuration in `BP_FacialControl`

## 📖 Detailed Implementation Guides

### Motion Retargeting System

The project uses UE5.5's IK Rig system for retargeting, providing a more robust approach than earlier techniques:

#### Key Components

1. **IK Rig Asset**: Defines the skeleton hierarchy and joints
2. **IK Retargeter Asset**: Maps the source skeleton to the target skeleton
3. **Animation Retarget Chains**: Define the relationship between bones

#### Retargeting Workflow

1. **Prepare Source Animation**:
   - Ensure mocap data is clean without artifacts
   - Properly scale to match target character
   - Have a T-pose or A-pose reference frame

2. **Create IK Rig for Source Character**:
   - Define retarget chains for root, spine, arms, legs
   - Add Full Body FBIK solver
   - Configure root, pelvis, and foot bone settings

3. **Create IK Rig for Target Character**:
   - Follow the same process for Metahuman or custom character
   - Ensure consistent naming conventions

4. **Create IK Retargeter Asset**:
   - Map each chain from source to target
   - Set up bone offsets as needed
   - Configure retarget pose

5. **Batch Retarget Animations**:
   - Select animations in Content Browser
   - Choose your IK Retargeter asset
   - Process all selected animations

#### Advanced Retargeting Techniques

For fixing common issues like foot sliding:

1. **Enable Root Motion**:
   - Check "Transfer Root Motion" in IK Retargeter
   - Configure Root Motion parameters

2. **Use Motion Warping**:
   - Create a Motion Warping component
   - Add foot lock warping targets
   - Configure timing based on your animation

For hand and finger retargeting:

1. **Create Detailed Finger Chains**:
   - Add separate chains for each finger
   - Map metacarpals, proximal, middle, and distal phalanges

The project includes specific chain mapping for the Metahuman target with custom offsets to ensure proper alignment.

### Facial Animation System

The project implements a comprehensive facial animation system using Metahuman:

#### Metahuman Setup

1. **Configure the Facial Control Rig**:
   - Access the Control Rig at `Content/Characters/Metahumans/[YourCharacter]/Face/CR_Face`
   - Understand the main controls: jaw, lips, eyebrows, eyelids
   - Test control manipulation to see how they affect expressions

#### LiveLink Face Configuration

1. **Install and Configure LiveLink**:
   - Enable LiveLink plugin in UE5.5
   - Add LiveLink Face as a source
   - Download LiveLink Face app on iOS device

2. **Connect to LiveLink Face App**:
   - Ensure device is on same network as development machine
   - Enter computer's IP address in app settings
   - Verify data is reaching Unreal Engine

3. **Configure LiveLink Remapping**:
   - Create remapping asset for ARKit to Metahuman
   - Map each blendshape with appropriate scale values
   - Test with a sample recording

#### Audio-driven Animation

1. **Set Up Audio Analysis**:
   - Import dialogue audio to `Content/Audio/Dialogue/`
   - Enable audio analysis in Sound Wave properties

2. **Create Audio-to-Facial Animation Blueprint**:
   - Map audio amplitude to jaw opening
   - Configure phoneme detection for lip-sync
   - Set up timing controls for synchronization

3. **Blend Animation Sources**:
   - Create layers for LiveLink and audio animation
   - Configure masks to prioritize different facial regions
   - Add manual animation for micro-expressions



## 🛠️ Customizing the Project

### Adding Your Own Mocap Data

1. Import your FBX files to `Content/Mocap/Raw`
2. Use the IK Rig retargeting workflow:
   - Open the IK Rig asset for your target skeleton
   - Select your imported mocap animation
   - Use the retargeting panel to create a new animation



### Tweaking Facial Animation

1. Open the Metahuman control rig
2. Adjust blendshape weights in the curve editor
3. For LiveLink capture, configure your device in the LiveLink panel
4. Modify the audio-driven animation parameters for better lip-sync

## 📦 Project Structure

```
MotionEditing/
├── Config/                  # Project configuration files
├── Content/
│   ├── Characters/          # Character assets and animations
│   │   ├── Animations/      # Animation sequences and montages
│   │   ├── IK_Rigs/         # IK Rig setups for retargeting
│   │   ├── Metahumans/      # Metahuman assets and facial rigs
│   │   └── RetargetingAssets/ # Retargeting configurations
│   ├── Levels/              # Main demo levels
│   ├── Mocap/               # Motion capture data
│   │   ├── Raw/             # Original mocap FBX files
│   │   └── Processed/       # Processed and retargeted animations
├── Plugins/                 # Project-specific plugin configurations
└── MotionEditing.uproject   # Project file
```

## 🔍 Performance Optimization

### Animation System Optimization

1. **LOD System**:
   - Configure animation LODs for distance-based simplification
   - Reduce bone count for distant characters
   - Simplify blend spaces at lower detail levels

2. **Animation Compression**:
   - Use appropriate compression settings for animations
   - Balance quality and memory usage
   - Consider ACL compression for best results

### VFX System Optimization

1. **Particle Count Management**:
   - Implement distance-based LOD system
   - Reduce spawn rates for distant effects
   - Use larger, fewer particles where appropriate

2. **GPU Simulation**:
   - Fire and smoke effects use GPU computation
   - Significantly improves performance for complex effects
   - Enable GPU simulation in system properties

3. **Dynamic LOD System**:
   - Automatically adjusts effect quality based on:
     - Distance from camera
     - Current frame rate
     - Number of visible effects

## 🔧 Troubleshooting

### Common Issues and Solutions

#### Animation Issues

1. **Retargeting Problems**:
   - Verify source and target skeletons are properly scaled
   - Check for mapping errors in the retargeter
   - Adjust chain rotation offsets if joints bend incorrectly

2. **Facial Animation Issues**:
   - Ensure LiveLink connection is stable
   - Check blendshape mapping for facial features
   - Verify audio analysis settings for lip-sync

#### VFX Issues

1. **Missing Effects**:
   - Check that VFX Controller is properly referenced
   - Verify animation notifies are correctly set up
   - Ensure socket names match exactly between blueprints

2. **Performance Problems**:
   - Reduce particle spawn rates
   - Lower simulation quality settings
   - Check for unnecessary computation in modules

## 📽️ Demo & Documentation

### Video Showcase

Watch the full animation and feature breakdown: [YouTube Demo](https://youtu.be/1lke6OSJItk)

The showcase demonstrates:
- Original mocap data compared to retargeted animation
- Facial animation performance with audio synchronization
- VFX integration with character movement
- Before and after motion refinement

## 🙏 Acknowledgments

This project was completed as part of a coursework assignment for CS7GV5. Special thanks to:
- Course Instructor and TAs for guidance
- Epic Games for Unreal Engine 5.5 and Metahuman technology
- Fellow students for feedback and testing

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Note:** If you encounter any issues with the project, please open an issue on this repository or refer to the Unreal Engine documentation for additional guidance.
