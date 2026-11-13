# dolly-models

Speech-to-text model files that Dolly Recorder downloads on demand when it generates captions. Each file is an unmodified copy of a published model, kept here with its licence. Two large files are split into parts so they fit GitHub's release asset limit; the app joins the parts back together after downloading.

Nothing else lives in this repository.

## Releases

### `whisper-v1`: Whisper (ggml format)

Source: [ggerganov/whisper.cpp on Hugging Face](https://huggingface.co/ggerganov/whisper.cpp), which converts OpenAI's [Whisper](https://github.com/openai/whisper) weights to the ggml format.
Licence: MIT. Model weights © 2022 OpenAI ([`LICENSE-whisper-openai.txt`](LICENSE-whisper-openai.txt)); ggml conversion © The ggml authors ([`LICENSE-whisper-cpp.txt`](LICENSE-whisper-cpp.txt)). Both files are also attached to the release.

| Asset | Bytes | SHA-256 |
|---|---:|---|
| `ggml-small.bin` | 487,601,967 | `1be3a9b2063867b937e64e2ec7483364a79917e157fa98c5d94b5c1fffea987b` |
| `ggml-medium.bin.part0` | 800,000,000 | `23182e96dea53b763310b202c4f33a7cea3c587d3795c439035bc5bd3c103ed9` |
| `ggml-medium.bin.part1` | 733,763,059 | `98cd5a140c0d4b457724b5c10c32309d8ec9a17ffc7f08be8867c346e71c3075` |

`ggml-medium.bin` = `part0` followed by `part1` (1,533,763,059 bytes, SHA-256 `6c14d5adee5f86394037b4e4e8b59f1673b6cee10e3cf0b11bbdbee79c156208`, identical to the source file).

### `parakeet-tdt-v1`: NVIDIA Parakeet TDT 0.6B v3 (ONNX)

Source: [istupakov/parakeet-tdt-0.6b-v3-onnx on Hugging Face](https://huggingface.co/istupakov/parakeet-tdt-0.6b-v3-onnx), an ONNX conversion of NVIDIA's [parakeet-tdt-0.6b-v3](https://huggingface.co/nvidia/parakeet-tdt-0.6b-v3).
Licence: Creative Commons Attribution 4.0 International ([`LICENSE-parakeet-CC-BY-4.0.txt`](LICENSE-parakeet-CC-BY-4.0.txt), also attached to the release).

Attribution: "Parakeet TDT 0.6B v3" by NVIDIA, licensed under CC BY 4.0, converted to ONNX by istupakov. Changes made here: none to the model data; `encoder-model.onnx.data` is split into two byte ranges for hosting.

| Asset | Bytes | SHA-256 |
|---|---:|---|
| `encoder-model.int8.onnx` | 652,183,999 | `6139d2fa7e1b086097b277c7149725edbab89cc7c7ae64b23c741be4055aff09` |
| `decoder_joint-model.int8.onnx` | 18,202,004 | `eea7483ee3d1a30375daedc8ed83e3960c91b098812127a0d99d1c8977667a70` |
| `encoder-model.onnx` | 41,770,866 | `98a74b21b4cc0017c1e7030319a4a96f4a9506e50f0708f3a516d02a77c96bb1` |
| `encoder-model.onnx.data.part0` | 1,300,000,000 | `93dad257fc93c5ed8782518f40d1900a00f5552b46fa597c86ac1a0c0e6ebd49` |
| `encoder-model.onnx.data.part1` | 1,135,420,160 | `86e971be68e93c72e33124f0600843dfb6f2cf4941fa149b5fc866533e6df222` |
| `decoder_joint-model.onnx` | 72,520,893 | `e978ddf6688527182c10fde2eb4b83068421648985ef23f7a86be732be8706c1` |
| `vocab.txt` | 93,939 | `d58544679ea4bc6ac563d1f545eb7d474bd6cfa467f0a6e2c1dc1c7d37e3c35d` |

`encoder-model.onnx.data` = `part0` followed by `part1` (2,435,420,160 bytes, SHA-256 `9a22d372c51455c34f13405da2520baefb7125bd16981397561423ed32d24f36`, identical to the source file).

The `.int8` files are the quantised model Dolly uses by default; the others are the full-precision model.
