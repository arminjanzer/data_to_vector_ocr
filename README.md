# data_to_vector OCR component

This repository hosts the downloads of the **optional OCR component** of
*data_to_vector*. It's a desktop app that converts documents (PDF, images,
DOCX, HTML) into clean Markdown for RAG systems, fully on the local machine.

You don't need to download anything from here by hand. The app downloads
the matching archive itself when you turn on **"Cross-check scans with OCR"**,
verifies its SHA-256 checksum and unpacks it into its own data folder.
**"Remove OCR component"** in the app deletes it again.

## What the component does

For scanned documents, the app's vision language model sometimes drops lines
or replaces words with plausible but wrong ones (for example a missing digit
in an ID). The OCR component reads the same pages a second time with classic
text recognition. It doesn't change the converted text. Wherever the two
readings disagree, the app asks you to check that spot against the original.

## Contents of each archive

| Part | Version | License |
| --- | --- | --- |
| CPython ([python-build-standalone](https://github.com/astral-sh/python-build-standalone)) | 3.14.8 | PSF License |
| [RapidOCR](https://github.com/RapidAI/RapidOCR) | 3.10.0 | Apache-2.0 |
| [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) models: PP-OCRv6 detection (small), Latin PP-OCRv5 recognition (mobile) | – | Apache-2.0 |
| [ONNX Runtime](https://github.com/microsoft/onnxruntime) | 1.31.0 | MIT |
| [OpenCV](https://github.com/opencv/opencv-python) (headless) | 5.0.0.93 | Apache-2.0 |
| [NumPy](https://numpy.org) | 2.5.3 | BSD-3-Clause |
| further Python dependencies | see `component.json` | see their `*.dist-info` folders |
| `ocr_worker.py` (connects the app to the OCR engine) | – | MIT (see [LICENSE](LICENSE)) |

The full license texts are in each archive: `NOTICE.txt`, `LICENSE`
(`ocr_worker.py`), `python/LICENSE.txt` and the `*.dist-info` folders under
`python/Lib/site-packages` (Windows) or `python/lib/python3.14/site-packages`
(macOS, Linux).

## Downloads

Each release `ocr-component-v<version>` contains one archive per platform:

| Platform | File |
| --- | --- |
| Windows (x64) | `data_to_vector-ocr-<version>-windows-x64.tar.gz` |
| macOS (Apple silicon) | `data_to_vector-ocr-<version>-macos-arm64.tar.gz` |
| Linux (x64) | `data_to_vector-ocr-<version>-linux-x64.tar.gz` |
| Linux (arm64) | `data_to_vector-ocr-<version>-linux-arm64.tar.gz` |

`SHA256SUMS` lists the checksums. Every archive is built and self-tested
automatically on its platform before it's published.

The component runs only on your machine and never connects to the internet.
It needs about 330 MB of disk space (download about 130 MB).
