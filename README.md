# 🎧 Podcast-Transcription-Whisper

Speech-to-text transcription workflow using Whisper, Jupyter, and FFmpeg.

---

## What You'll Need

- Git  
- Python (e.g., via [Anaconda](https://www.anaconda.com/))  
- Jupyter Notebook  
- FFmpeg  
- An audio file (`.mp3`, `.wav`, etc.)

---

## Step 1: Install PyTorch and Whisper from GitHub

Whisper requires PyTorch to be installed first.  
Visit the [PyTorch site](https://pytorch.org/get-started/locally/) to find the correct install command for your system.

For example, on Windows with CPU only, run:

```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

Then install Whisper with:

```bash
pip install git+https://github.com/openai/whisper.git
```

> ✅ **Note:** Make sure Git is installed on your machine! Restart the terminal before running the above commands.

---

## Step 2: Select the Correct Jupyter Kernel

Make sure the environment where you installed Whisper is selected in Jupyter:  
Go to `Kernel > Change Kernel`.

If you don’t, you might see this error:

```python
ModuleNotFoundError: No module named 'whisper'
```

---

## Step 3: Set Up FFmpeg

Whisper requires FFmpeg to process audio.

1. Download FFmpeg from [gyan.dev](https://www.gyan.dev/ffmpeg/builds/).  
2. Unzip the downloaded file.  
3. Add the `bin` folder inside FFmpeg to your system `PATH` **within your Python script**:

```python
import os
os.environ["PATH"] = r"D:\path\to\ffmpeg\bin;" + os.environ["PATH"]
```

---

## Step 4: Transcribe Your Audio in Jupyter

Use this sample Python script to transcribe your audio file:

```python
import os
os.environ["PATH"] = r"D:\path\to\ffmpeg\bin;" + os.environ["PATH"]

import whisper
print("Whisper is ready!")

model = whisper.load_model("base")
result = model.transcribe(r"D:\path\to\podcast.mp3")

with open("transcript.txt", "w", encoding="utf-8") as f:
    f.write(result["text"])

print("Transcript saved!")
```

---

## 🛠 Troubleshooting

- **Invisible characters in file paths:** Re-copy the path directly from Windows Explorer.  
- **"FP16 not supported on CPU":** This is just a warning — safe to ignore.  
- **Transcription is slow:** This is normal due to heavy processing.

---

## ✅ Done!

You now have a clean `.txt` transcript file.  
I upload mine to [Readlang](https://readlang.com/) to read along while listening as a language learning tool!


