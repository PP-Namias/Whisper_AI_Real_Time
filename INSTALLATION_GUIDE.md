# Installation Guide for Whisper Real-Time Transcription

This guide will help you set up and run the real-time speech transcription application using OpenAI's Whisper model.

## Prerequisites

1. **Python 3.7+** (Python 3.8+ recommended)
2. **FFmpeg** (required by Whisper)
3. **Microphone** (for audio input)

## Step-by-Step Installation

### 1. Install FFmpeg (Required)

FFmpeg is required by Whisper for audio processing. Choose one of these methods for Windows:

**Option A: Using Chocolatey (Recommended)**
```cmd
choco install ffmpeg
```

**Option B: Using Scoop**
```cmd
scoop install ffmpeg
```

**Option C: Manual Installation**
1. Download FFmpeg from https://ffmpeg.org/download.html
2. Extract to a folder (e.g., `C:\ffmpeg`)
3. Add `C:\ffmpeg\bin` to your system PATH environment variable

### 2. Set Up Python Environment

A virtual environment has already been created for you at:
`.venv` folder in your project directory

### 3. Install Python Dependencies

Run the following command to install all required packages:

```cmd
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe -m pip install -r requirements.txt
```

This will install:
- `setuptools` - Python package tools
- `pyaudio` - Audio I/O library
- `SpeechRecognition` - Speech recognition library
- `torch` - PyTorch (with CUDA support if available)
- `numpy` - Numerical computing library
- `whisper` - OpenAI's Whisper model

### 4. Verify Installation

Test if everything is installed correctly:

```cmd
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe -c "import whisper; import speech_recognition; import torch; print('All dependencies installed successfully!')"
```

## Running the Application

### Basic Usage

To run with default settings (medium model):

```cmd
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py
```

### Command Line Options

You can customize the behavior with these options:

**Select Whisper Model:**
```cmd
# Use tiny model (fastest, less accurate)
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --model tiny

# Use large model (slowest, most accurate)
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --model large
```

**Available models:** `tiny`, `base`, `small`, `medium`, `large`

**Adjust Sensitivity:**
```cmd
# Higher threshold = less sensitive to background noise
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --energy_threshold 1500

# Lower threshold = more sensitive
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --energy_threshold 500
```

**Non-English Languages:**
```cmd
# For languages other than English
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --non_english
```

**Adjust Timing:**
```cmd
# Record every 1 second (more real-time)
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --record_timeout 1

# Wait 5 seconds of silence before considering phrase complete
C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe transcribe_demo.py --phrase_timeout 5
```

## How It Works

1. **Audio Recording:** The app continuously records audio from your microphone
2. **Speech Detection:** Uses speech recognition to detect when you're speaking
3. **Real-time Processing:** Processes audio chunks in real-time using Whisper
4. **Live Transcription:** Updates the transcription on screen as you speak

## Troubleshooting

### Common Issues:

1. **"No module named 'pyaudio'"**
   - PyAudio can be tricky on Windows. If installation fails, try:
   ```cmd
   C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe -m pip install pipwin
   C:/Users/ADMIN/Downloads/whisper_real_time-master/whisper_real_time-master/.venv/Scripts/python.exe -m pipwin install pyaudio
   ```

2. **"FFmpeg not found"**
   - Make sure FFmpeg is installed and added to your PATH
   - Restart your command prompt after installation

3. **Microphone not detected**
   - Check Windows microphone permissions
   - Ensure your microphone is set as the default recording device

4. **High CPU usage**
   - Use a smaller model (`tiny` or `base`) for better performance
   - Increase `record_timeout` to process audio less frequently

### Performance Tips:

- **GPU Acceleration:** If you have a CUDA-compatible GPU, the app will automatically use it for faster processing
- **Model Selection:** Start with `tiny` or `base` model for testing, upgrade to `medium` or `large` for better accuracy
- **Microphone Quality:** Better microphones will give more accurate transcriptions

## Stopping the Application

Press `Ctrl+C` to stop the application. It will display the final complete transcription before exiting.

## Next Steps

Once everything is working, you can:
- Experiment with different models for your use case
- Adjust the sensitivity and timing parameters
- Integrate the transcription into other applications
- Save transcriptions to files by modifying the code

Enjoy your real-time speech transcription!
