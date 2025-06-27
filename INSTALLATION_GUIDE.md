# Complete Installation Guide - Whisper AI Real Time Transcription

Welcome to the comprehensive installation guide for the Whisper AI Real Time Transcription project! This guide will walk you through every step needed to get your real-time speech transcription system up and running.

## 📋 Prerequisites

Before we begin, make sure you have:

1. **Python 3.7+** (Python 3.8+ recommended for best performance)
2. **FFmpeg** (required by Whisper for audio processing)
3. **Microphone** (any USB or built-in microphone)
4. **4GB+ RAM** (8GB+ recommended for larger models)
5. **Internet connection** (for initial model download only)

### Hardware Recommendations

| Component | Minimum | Recommended | Optimal |
|-----------|---------|-------------|---------|
| **CPU** | Any modern processor | Intel i5/AMD Ryzen 5+ | Intel i7/AMD Ryzen 7+ |
| **RAM** | 4GB | 8GB | 16GB+ |
| **Storage** | 2GB free space | 5GB free space | 10GB+ free space |
| **GPU** | Not required | CUDA-compatible | RTX 20-series or newer |
| **Audio** | Any microphone | USB microphone | Professional microphone |

---

## 🚀 Quick Start (5 Minutes)

If you're experienced with Python and want to get started quickly:

1. **Install FFmpeg:**
   ```cmd
   choco install ffmpeg
   ```

2. **Install Python dependencies:**
   ```cmd
   pip install -r requirements.txt
   ```

3. **Run the application:**
   ```cmd
   python transcribe_demo.py
   ```

4. **Start speaking!** Your speech will appear as text in real-time.

*For detailed instructions, continue reading below.*

---

## 📖 Detailed Step-by-Step Installation

### Step 1: Verify Python Installation

First, let's make sure Python is properly installed on your system.

1. **Open Command Prompt (cmd)**
   - Press `Windows + R`
   - Type `cmd` and press Enter

2. **Check Python version:**
   ```cmd
   python --version
   ```
   
   **Expected output:** `Python 3.8.x` or higher
   
   ❌ **If you see an error:**
   - Download Python from [python.org](https://www.python.org/downloads/)
   - ✅ **Important:** Check "Add Python to PATH" during installation
   - Restart your command prompt and try again

3. **Verify pip is working:**
   ```cmd
   pip --version
   ```
   
   **Expected output:** `pip 21.x.x` or similar

### Step 2: Install FFmpeg (Required)

FFmpeg is essential for Whisper to process audio. Choose the method that works best for you:

#### Method A: Using Chocolatey (Recommended) ⭐

**Install Chocolatey first (if not already installed):**
```cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

**Install FFmpeg:**
```cmd
choco install ffmpeg
```

#### Method B: Using Scoop
```cmd
# Install Scoop first (if not already installed)
powershell -Command "Set-ExecutionPolicy RemoteSigned -scope CurrentUser; iwr -useb get.scoop.sh | iex"

# Install FFmpeg
scoop install ffmpeg
```

#### Method C: Manual Installation
1. Download FFmpeg from [ffmpeg.org/download.html](https://ffmpeg.org/download.html)
2. Extract to `C:\ffmpeg`
3. **Add to PATH:**
   - Open System Properties → Advanced → Environment Variables
   - Under "System Variables", find and select "Path", then click "Edit"
   - Click "New" and add `C:\ffmpeg\bin`
   - Click "OK" to save

**Verify FFmpeg installation:**
```cmd
ffmpeg -version
```
**Expected output:** Version information starting with `ffmpeg version`

### Step 3: Navigate to Project Directory

1. **Open Command Prompt in your project folder:**
   ```cmd
   cd "c:\Users\ADMIN\Desktop\PP Namias\Whisper_AI_Real_Time"
   ```

2. **Verify you're in the right location:**
   ```cmd
   dir
   ```
   
   **You should see these files:**
   - `transcribe_demo.py`
   - `requirements.txt`
   - `README.md`
   - And other project files

### Step 4: Set Up Python Environment (Recommended)

Using a virtual environment keeps your project dependencies isolated:

1. **Create a virtual environment:**
   ```cmd
   python -m venv .venv
   ```

2. **Activate the virtual environment:**
   ```cmd
   .venv\Scripts\activate
   ```
   
   **Success indicator:** Your command prompt should now show `(.venv)` at the beginning

3. **Upgrade pip (recommended):**
   ```cmd
   python -m pip install --upgrade pip
   ```
### Step 5: Install Python Dependencies

Now we'll install all the required Python packages:

1. **Install the dependencies:**
   ```cmd
   pip install -r requirements.txt
   ```

   **This installs:**
   - ✅ `setuptools` - Python package tools
   - ✅ `pyaudio` - Audio I/O library
   - ✅ `SpeechRecognition` - Speech recognition library
   - ✅ `torch` - PyTorch (with CUDA support if available)
   - ✅ `numpy` - Numerical computing library
   - ✅ `whisper` - OpenAI's Whisper model

2. **Installation progress:**
   - This may take 5-15 minutes depending on your internet speed
   - PyTorch is a large download (~1-2GB)
   - The first time you run Whisper, it will download the model files

**⚠️ Troubleshooting PyAudio Installation:**

If PyAudio installation fails (common on Windows), try:

```cmd
# Method 1: Use pipwin (recommended)
pip install pipwin
pipwin install pyaudio

# Method 2: Install Microsoft Visual C++ Build Tools
# Download from: https://visualstudio.microsoft.com/visual-cpp-build-tools/
# Then retry: pip install pyaudio

# Method 3: Use pre-compiled wheel
pip install https://github.com/intxcc/pyaudio_portaudio/releases/download/v19.7.0/PyAudio-0.2.11-cp39-cp39-win_amd64.whl
```

### Step 6: Verify Installation

Let's make sure everything is installed correctly:

1. **Test all dependencies:**
   ```cmd
   python -c "import whisper; import speech_recognition; import torch; import numpy; import pyaudio; print('✅ All dependencies installed successfully!')"
   ```

2. **Check CUDA availability (GPU acceleration):**
   ```cmd
   python -c "import torch; print('CUDA available:', torch.cuda.is_available()); print('CUDA device:', torch.cuda.get_device_name(0) if torch.cuda.is_available() else 'CPU only')"
   ```

3. **Test microphone access:**
   ```cmd
   python -c "import speech_recognition as sr; r = sr.Recognizer(); print('✅ Microphone access working!')"
   ```

**Expected outputs:**
- ✅ "All dependencies installed successfully!"
- ✅ CUDA status (GPU acceleration available or CPU-only mode)
- ✅ "Microphone access working!"

---

## 🎯 Running the Application

### Basic Usage

**Start the transcription with default settings:**
```cmd
python transcribe_demo.py
```

**What you'll see:**
1. "Model loaded." - The Whisper model is ready
2. **Start speaking!** - Your speech will appear as text in real-time
3. Press `Ctrl+C` to stop and see the final transcription

### Advanced Usage Options

#### Choose Different Whisper Models

**Faster, less accurate (good for testing):**
```cmd
python transcribe_demo.py --model tiny
```

**Balanced performance (default):**
```cmd
python transcribe_demo.py --model medium
```

**Highest accuracy (slower):**
```cmd
python transcribe_demo.py --model large
```

**Model comparison:**
| Model | Size | Speed | Accuracy | Best For |
|-------|------|-------|----------|----------|
| `tiny` | ~40MB | Fastest | Good | Testing, low-end hardware |
| `base` | ~75MB | Fast | Better | Quick transcription tasks |
| `small` | ~250MB | Medium | Good | General use |
| `medium` | ~770MB | Slower | Very Good | **Default recommendation** |
| `large` | ~1.5GB | Slowest | Best | Highest accuracy needs |

#### Adjust Sensitivity and Timing

**More sensitive to quiet speech:**
```cmd
python transcribe_demo.py --energy_threshold 500
```

**Less sensitive (ignore background noise):**
```cmd
python transcribe_demo.py --energy_threshold 1500
```

**More real-time (process every 1 second):**
```cmd
python transcribe_demo.py --record_timeout 1
```

**Longer phrases (wait 5 seconds of silence):**
```cmd
python transcribe_demo.py --phrase_timeout 5
```

#### Non-English Languages

**For languages other than English:**
```cmd
python transcribe_demo.py --non_english
```

#### Combine Multiple Options

**Example: Fast, sensitive transcription:**
```cmd
python transcribe_demo.py --model base --energy_threshold 500 --record_timeout 1
```

---

## 🔧 Configuration & Optimization

### Performance Optimization

#### For Faster Performance:
1. **Use smaller models:** `--model tiny` or `--model base`
2. **Increase processing intervals:** `--record_timeout 3`
3. **Close unnecessary applications** to free up CPU/RAM
4. **Use GPU acceleration** (automatic if CUDA is available)

#### For Better Accuracy:
1. **Use larger models:** `--model large`
2. **Good microphone positioning:** 6-12 inches from mouth
3. **Quiet environment:** Minimize background noise
4. **Adjust sensitivity:** `--energy_threshold 800` (experiment with values)

### Audio Setup Tips

1. **Microphone Selection:**
   - USB microphones generally work better than built-in ones
   - Headset microphones reduce background noise
   - Position microphone consistently

2. **Windows Audio Settings:**
   - Set your microphone as the default recording device
   - Adjust microphone levels in Windows Sound settings
   - Disable audio enhancements that might interfere

3. **Environment Setup:**
   - Use in a quiet room when possible
   - Avoid echoing environments
   - Consistent speaking volume and pace

---

## 🐛 Troubleshooting Guide

### Common Issues and Solutions

#### Issue 1: "FFmpeg not found"
**Symptoms:** Error message about FFmpeg not being available
**Solutions:**
1. Restart command prompt after FFmpeg installation
2. Verify FFmpeg is in PATH: `ffmpeg -version`
3. Try manual installation method if package managers failed

#### Issue 2: "No module named 'pyaudio'"
**Symptoms:** ImportError when trying to run the application
**Solutions:**
```cmd
# Try these in order:
pip install pipwin
pipwin install pyaudio

# Or install Visual C++ Build Tools and retry
pip install pyaudio
```

#### Issue 3: Microphone not detected
**Symptoms:** No transcription appears when speaking
**Solutions:**
1. Check Windows microphone permissions:
   - Settings → Privacy → Microphone → Allow apps to access microphone
2. Set correct default microphone:
   - Settings → System → Sound → Input device
3. Test microphone in other applications first

#### Issue 4: Very slow transcription
**Symptoms:** Long delays between speech and text appearance
**Solutions:**
1. Use smaller model: `--model tiny`
2. Check CPU usage in Task Manager
3. Ensure adequate RAM (4GB+ free)
4. Close other intensive applications

#### Issue 5: Poor transcription accuracy
**Symptoms:** Many incorrect words in transcription
**Solutions:**
1. Use larger model: `--model medium` or `--model large`
2. Improve microphone setup and environment
3. Adjust energy threshold: `--energy_threshold 800`
4. Speak more clearly and at consistent volume

#### Issue 6: Application crashes or freezes
**Symptoms:** Program stops responding or exits unexpectedly
**Solutions:**
1. Check available RAM (models need significant memory)
2. Update GPU drivers if using CUDA
3. Try CPU-only mode by uninstalling CUDA version of PyTorch:
   ```cmd
   pip uninstall torch
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
   ```

### Getting Help

**If you're still having issues:**

1. **Check system requirements** - Ensure you meet minimum specifications
2. **Try with different models** - Start with `tiny` model for testing
3. **Test in isolation** - Try with no other applications running
4. **Check the logs** - Look for error messages in the console output
5. **Community support** - Check project documentation and community forums

---

## 🎉 Success! You're Ready to Go

**Congratulations!** You now have a fully functional real-time speech transcription system. Here's what you can do next:

### Immediate Next Steps:
1. **Test with different models** to find your preferred accuracy/speed balance
2. **Experiment with settings** to optimize for your voice and environment
3. **Try various speaking scenarios** - normal conversation, dictation, presentations
4. **Share your experience** - Let others know how it works for you!

### Advanced Usage:
- **Meeting transcription** - Use during video calls or in-person meetings
- **Content creation** - Transcribe podcasts, videos, or voice recordings
- **Accessibility** - Assist with hearing impairments or language learning
- **Productivity** - Voice-to-text for emails, documents, or notes

### Future Enhancements:
Check out `DEVELOPMENT_PLANS.md` to see what exciting features are coming next, including:
- Graphical user interface
- Multiple language support
- Speaker identification
- Export to various formats
- Integration with other applications

---

## 📚 Additional Resources

- **README.md** - Project overview and basic information
- **DEVELOPMENT_LOGS.md** - Technical architecture and development details
- **CHANGELOG.md** - Version history and updates
- **DEVELOPMENT_PLANS.md** - Future features and roadmap

**Official Links:**
- [OpenAI Whisper Documentation](https://github.com/openai/whisper)
- [PyTorch Installation Guide](https://pytorch.org/get-started/locally/)
- [FFmpeg Documentation](https://ffmpeg.org/documentation.html)

---

*Installation Guide v2.0 - Updated June 27, 2025*  
*For technical support, please refer to the troubleshooting section or project documentation.*
