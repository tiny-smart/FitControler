# FitControler

FitControler is a fit-aware virtual try-on method that enables controllable garment-fit generation. The paper presents both the FitControler method and the Fit4Men dataset; Fit4Men is one of the paper's contributions, rather than the entire project.

### TODO

- [x] Release the Fit4Men dataset (publicly available through Google Drive)
- [ ] Release the FitControler training and evaluation code
- [ ] Release pretrained FitControler model weights

## Fit4Men Dataset

Fit4Men is a male fashion dataset used by the FitControler project for fit-aware virtual try-on research. The dataset is now publicly available for download. It contains two garment categories, upper-body garments (`upper`) and lower-body garments (`lower`), together with training and test splits and garment-fit labels. The accompanying paper describes Fit4Men as containing approximately 13,000 body-garment pairs across different fits, camera distances, and body poses.

> This README was prepared from the actual contents of the local `Fit4Men` dataset. Because the archive is large, Google Drive may not be able to preview it online, but the file can still be downloaded.

### Download

- **Google Drive:** <https://drive.google.com/file/d/11yDFh6JYcstnBrdbttsJBXl0tWNsgdMI/view?usp=sharing>

After downloading, extract the archive to obtain the `Fit4Men/` directory and preserve the directory structure shown below. The uncompressed dataset is approximately **10.94 GB** and contains **85,778 files**.

### Dataset Structure

```text
Fit4Men/
├── lower/
│   ├── train/
│   │   ├── cloth/
│   │   ├── densepose/
│   │   ├── image/
│   │   ├── mask/
│   │   ├── person_keypoints/
│   │   ├── person_mask/
│   │   └── seg/
│   ├── test/
│   │   ├── cloth/
│   │   ├── cloth_mask/
│   │   ├── densepose/
│   │   ├── image/
│   │   ├── mask/
│   │   ├── person_keypoints/
│   │   ├── person_mask/
│   │   └── seg/
│   ├── train.json
│   ├── test.json
│   └── test_unpairs.json
└── upper/
    ├── train/
    │   ├── cloth/
    │   ├── densepose/
    │   ├── image/
    │   ├── mask/
    │   ├── person_keypoints/
    │   ├── person_mask/
    │   └── seg/
    ├── test/
    │   ├── cloth/
    │   ├── cloth_mask/
    │   ├── densepose/
    │   ├── image/
    │   ├── mask/
    │   ├── person_keypoints/
    │   ├── person_mask/
    │   └── seg/
    ├── train.json
    ├── test.json
    └── test_unpairs.json
```

### Dataset Statistics

| Category | Training records | Test records | Approximate size | `type` labels |
| --- | ---: | ---: | ---: | --- |
| `lower` | 2,174 | 544 | 7.09 GB | `straight`, `tapered` |
| `upper` | 1,853 | 467 | 3.85 GB | `loose`, `regular`, `slim` |

The complete dataset contains **85,077 PNG files**, **695 JPG files**, and **6 JSON files**.

### File Description

| Directory/File | Description |
| --- | --- |
| `cloth/` | Garment images |
| `image/` | Model images |
| `cloth_mask/` | Garment masks, provided for the test split |
| `mask/` | Human-related masks |
| `person_mask/` | Human-region masks |
| `person_keypoints/` | Human keypoint annotations or visualizations |
| `densepose/` | DensePose results |
| `seg/` | Semantic segmentation results |
| `train.json` | Training manifest |
| `test.json` | Test manifest |
| `test_unpairs.json` | Unpaired test manifest |

### JSON Annotation Format

Each record contains a garment filename, a list of corresponding model-image filenames, and a garment-fit label:

```json
{
  "cloth": "337.png",
  "image": ["692.png", "693.png", "694.png"],
  "type": "tapered"
}
```

- `cloth`: The garment-image filename.
- `image`: A list of model-image filenames corresponding to the garment. The list usually contains multiple elements, allowing one garment to be associated with a group of model images.
- `type`: The garment-fit category. The `lower` subset uses `straight` and `tapered`, while the `upper` subset uses `loose`, `regular`, and `slim`.

### Usage

1. Download `Fit4Men.zip` from the Google Drive link above.
2. Extract the archive and place the resulting `Fit4Men/` directory under the data root configured by your data loader.
3. Select either `upper` or `lower`, then load `train.json`, `test.json`, or `test_unpairs.json` as required by your task.

### License

The Fit4Men dataset is released under the **Fit4Men Dataset Non-Commercial License (F4M-NC) v1.0**. It may be used only for non-commercial purposes such as academic research, teaching, evaluation, and personal study. **Commercial use is prohibited.** See [LICENSE](LICENSE) for the complete terms. Please contact the project maintainers for separate written permission before any commercial use.

Images, annotations, or other materials in the dataset may also be subject to rights held by their original owners. This license does not replace those rights or grant permissions beyond those that the dataset authors are legally able to provide.

### Citation

If FitControler or the Fit4Men dataset contributes to your research, please cite the ECCV 2026 paper:

```bibtex
@inproceedings{yang2026fitcontroler,
  title     = {FitControler: Toward Fit-Aware Virtual Try-On},
  author    = {Yang, Lu and Liu, Yicheng and Zhou, Letian and Li, Yanan and Bai, Xiang and Lu, Hao},
  booktitle = {European Conference on Computer Vision (ECCV)},
  year      = {2026}
}
```
