<!--
Copyright (c) 2026, Lalit Manam
-->

# Parallel Rigidity Matters for Bundle Adjustment

<b>IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2026</b>


**Authors**<br>
[Lalit Manam](https://lalitmanam.github.io/) and [Venu Madhav Govindu](https://ee.iisc.ac.in/~venu/)<br>

[Project Page](https://www.merl.com/research/highlights/parallel-rigid-ba) | [Paper](https://www.merl.com/publications/docs/TR2026-053.pdf)

<br>

Implementation of methods HOF (Hanging Observation Filter) and GPRBA (Extracting Generic Parallel Rigid Component in Bundle Adjsutment Graph).


## Installation

Tested on **Ubuntu 24.04.4** with **Glomap 1.2.0** and database from **Colmap 3.13.0**.

### Prerequisites

Download this repository
```
git clone <path_to_repository>
cd parallel_rigid_ba
```

Requirements:
Install prerequisutes of Glomap 1.2.0
```
git clone --branch 1.2.0  https://github.com/colmap/glomap.git
```
Installation instructions: https://github.com/colmap/glomap/blob/main/README.md#getting-started

### Apply Patch on Glomap and Install

After installing the prerequisites of Glomap 1.2.0, apply the patch and install Glomap.

```
cd glomap
git apply ../parallel_rigid_ba_glomap.patch
mkdir build && cd build
cmake .. -GNinja
ninja
ninja install
```

## Usage

Obtain a Colmap 3.13.0 database after feature extraction and matching. Run below commands to test different settings.

Run Glomap
```
glomap mapper \
    --database_path "<database_path>" \
    --image_path "<image_path>" \
    --output_path "<reconstruction_path>" \
    --output_path_wo_retri "<reconstruction_without_retriangulation_path>"
```

Run Glomap with HOF (Hanging Observation Filter)
```
glomap mapper \
    --database_path "<database_path>" \
    --image_path "<image_path>" \
    --output_path "<reconstruction_path>" \
    --output_path_wo_retri "<reconstruction_without_retriangulation_path>" \
    --use_hof_tracks 1
```

Run Glomap with HOF (Hanging Observation Filter) and GPRBA (Parallel Rigid BA Graph)
```
glomap mapper \
    --database_path "<database_path>" \
    --image_path "<image_path>" \
    --output_path "<reconstruction_path>" \
    --output_path_wo_retri "<reconstruction_without_retriangulation_path>" \
    --use_gpr_ba 1
```

## Citation

If you use this code, please cite the following:

```BibTeX
@inproceedings{manam2026gprba,
    author = {Lalit Manam and Venu Madhav Govindu},
    title = {{Parallel Rigidity Matters for Bundle Adjustment}},
    booktitle = {IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
    year = 2026,
}
```

## Contact

Lalit Manam<br>
E-Mail: manam@merl.com, lalitmanam@gmail.com

## License

Released under `BSD 3-Clause License`, as found in the [LICENSE.md](LICENSE.md) file.

All files, except as noted below:

```
Copyright (c) 2026, Lalit Manam.
All rights reserved.
```

Before patching, Glomap 1.2.0 is taken without modifications from [https://github.com/colmap/glomap](https://github.com/colmap/glomap). [License](LICENSE/glomap_license.md):
```
Copyright (c) 2024, ETH Zurich.
All rights reserved.
```
