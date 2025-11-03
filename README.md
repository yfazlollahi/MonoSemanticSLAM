# MonoSemanticSLAM: Semantic-Aware Monocular SLAM for Indoor Navigation

MonoSemanticSLAM is a research-oriented implementation of a monocular SLAM pipeline enhanced with semantic perception.  
The goal of the project is to combine real-time camera pose estimation with pixel-level scene understanding to produce 3D indoor maps that contain both geometric structure and semantic labels.

---

## Project Description
Traditional monocular SLAM systems recover camera trajectory and sparse 3D structure, but they do not provide information about *what* objects exist in the scene.  
This project extends the SLAM pipeline by integrating a lightweight semantic segmentation module, enabling the system to attach object-level labels (e.g., wall, floor, door, furniture) to reconstructed map points.

The project is being implemented from scratch in a modular structure, allowing individual components (tracking, mapping, semantics, fusion, visualization) to be developed, replaced, or benchmarked independently.

---

## System Components

| Module | Description |
|--------|-------------|
| **Feature Tracking** | ORB/AKAZE keypoint extraction and matching for frame-to-frame motion estimation |
| **Pose Estimation** | Keyframe-based visual odometry with planned optimization via bundle adjustment and loop closure |
| **Semantic Segmentation** | Lightweight model based on MobileNetV3 + DeepLab for real-time pixel labeling |
| **Semantic–Geometric Fusion** | Assigns semantic class attributes to 3D map points and maintains consistency across keyframes |
| **Visualization & Evaluation** | Tools for rendering labeled point clouds, pose trajectories, and segmentation overlays |

---

## Technical Scope

- **Language & Frameworks:** Python, OpenCV, PyTorch, NumPy  
- **SLAM Back-End:** keyframe graph, reprojection error minimization, future BA and loop closure  
- **Semantic Model:** MobileNetV3 encoder + DeepLab decoder (pretrained and fine-tuned on NYUv2)  
- **Datasets:** TUM RGB-D (trajectory + depth), NYUv2 (RGB + semantic labels), custom smartphone video sequences  
- **Planned Evaluation Metrics:** ATE (Absolute Trajectory Error), mIoU for segmentation, consistency metrics for fused map

