# Piper TTS Project - Emmanuella

This repository contains a Piper text-to-speech (TTS) model trained on a custom audio dataset. The model was fine-tuned, exported to ONNX format, and tested to generate WAV files. A Docker setup is included for deployment.

## Files
- `model_2195.onnx`: Trained ONNX model (63.5 MB).
- `model_2195.onnx.json`: Model configuration (7 KB).
- `config.json`: Training configuration.
- `dataset.jsonl`: Preprocessed training dataset.
- `test_onnx.wav`: Sample output WAV (78 KB).
- `piper_setup_commands.txt`: Commands used for setup, training, and export.
- `docker_piper.tar.gz`: Docker archive (2 GB, available on Google Drive: https://drive.google.com/file/d/1J8MghFESQgD3dFPfKh9O9NFVoO3wGWb6/view?usp=sharing).

## Setup Instructions
See `piper_setup_commands.txt` for detailed setup and deployment instructions.

## License
MIT License
