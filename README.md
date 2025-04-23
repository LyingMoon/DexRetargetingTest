# DexRetargetingTest
This project demonstrates how to set up and run examples from the [dexsuite/dex-retargeting](https://github.com/dexsuite/dex-retargeting) repository, a library for retargeting human hand motion to various robot hands using optimization.

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/dexsuite/dex-retargeting
   cd dex-retargeting
   ```

2. **Install the package with example dependencies:**
   ```bash
   pip install -e ".[example]"
   ```

This installs the core package and additional requirements like sapien, mediapipe, and opencv-python.


## Example: Position Retargeting Using DexYCB

**Step 1: Download the DexYCB dataset**

Download a subset of the DexYCB dataset (e.g., `20200709-subject-01.tar.gz`), and also the `models` and `calibration` folders. Place them in the following structure:

```
your_dexycb_dir/
├── 20200709-subject-01
├── calibration
└── models
```

**Step 2: Verify the dataset**

Navigate to the position retargeting example folder and run:

```bash
cd example/position_retargeting
python dataset.py --dexycb-dir=PATH_TO_YOUR_DEXYCB_DIR_ROOT
```

Replace `PATH_TO_YOUR_DEXYCB_DIR_ROOT` with the actual path to your DexYCB directory.

**Step 3: Set up manopth**

Clone and install `manopth`, which is used for hand mesh reconstruction:

```bash
git clone https://github.com/hassony2/manopth
cd manopth
pip install chumpy opencv-python
pip install -e .
```

Download the MANO models from mano.is.tue.mpg.de and place them inside the manopth directory. Then run:

```bash
unzip mano_v1_2.zip
cd mano
ln -s ../mano_v1_2/models models
```

**Step 4: Install additional dependencies**

```bash
pip install tyro pyyaml sapien==3.0.0b0
```

**Step 5: Visualize human hand-object interaction**

```bash
python visualize_hand_object.py --dexycb-dir=PATH_TO_YOUR_DEXYCB_DIR_ROOT
```

**Step 6: Visualize robot hand retargeting results**

```bash
python visualize_hand_object.py --dexycb-dir=PATH_TO_YOUR_DEXYCB_DIR_ROOT --robots allegro shadow svh
```

This command visualizes the retargeting results of the human hand motion to the specified robot hands.

