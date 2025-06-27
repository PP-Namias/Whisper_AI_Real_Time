# 🎤 Whisper AI Real Time Transcription

![Demo](demo.gif)

[![Python 3.7+](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Powered by OpenAI Whisper](https://img.shields.io/badge/Powered%20by-OpenAI%20Whisper-green.svg)](https://github.com/openai/whisper)

**Real-time speech-to-text transcription powered by OpenAI's Whisper model** - Turn your spoken words into text instantly with state-of-the-art AI accuracy.

## ✨ Features

- 🎯 **Real-time transcription** - See your words as you speak them
- 🧠 **AI-powered accuracy** - Leverages OpenAI's Whisper for superior recognition
- ⚡ **Multiple model sizes** - Choose from tiny to large models based on your needs
- 🖥️ **Cross-platform** - Works on Windows, macOS, and Linux
- 🎛️ **Customizable settings** - Adjust sensitivity, timing, and model parameters
- 🔊 **Smart audio detection** - Automatically detects speech and handles pauses
- 💾 **Local processing** - Your audio never leaves your device
- 🚀 **GPU acceleration** - Automatic CUDA support for faster processing

## 🚀 Quick Start

### Prerequisites
- Python 3.7+ (3.8+ recommended)
- FFmpeg (for audio processing)
- Microphone

### Installation
```bash
# 1. Install FFmpeg (Windows with Chocolatey)
choco install ffmpeg

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the application
python transcribe_demo.py
```

**That's it!** Start speaking and watch your words appear in real-time.

## 📖 Detailed Setup

For comprehensive installation instructions, troubleshooting, and optimization tips, see our detailed **[Installation Guide](INSTALLATION_GUIDE.md)**.

## 🎛️ Usage Options

### Basic Usage
```bash
python transcribe_demo.py  # Uses medium model (balanced speed/accuracy)
```

### Model Selection
```bash
python transcribe_demo.py --model tiny    # Fastest, good for testing
python transcribe_demo.py --model base    # Fast, decent accuracy
python transcribe_demo.py --model small   # Balanced option
python transcribe_demo.py --model medium  # Default, very good accuracy
python transcribe_demo.py --model large   # Best accuracy, slower
```

### Sensitivity & Timing
```bash
# Adjust microphone sensitivity (default: 1000)
python transcribe_demo.py --energy_threshold 500   # More sensitive
python transcribe_demo.py --energy_threshold 1500  # Less sensitive

# Adjust real-time responsiveness (default: 2 seconds)
python transcribe_demo.py --record_timeout 1       # More real-time
python transcribe_demo.py --record_timeout 3       # Less frequent updates

# Adjust phrase detection (default: 3 seconds)
python transcribe_demo.py --phrase_timeout 5       # Longer phrases
```

### Non-English Languages
```bash
python transcribe_demo.py --non_english  # For languages other than English
```

## 🏗️ How It Works

```
🎤 Microphone → 🔊 Audio Detection → 🧠 Whisper AI → 📝 Real-time Text
```

1. **Continuous Audio Capture** - Records audio from your microphone in real-time
2. **Speech Detection** - Intelligently detects when you're speaking vs. silence
3. **AI Processing** - Uses OpenAI's Whisper model to convert speech to text
4. **Live Updates** - Displays transcription with minimal latency

## 📊 Model Comparison

| Model | Size | Speed | Accuracy | Memory | Best For |
|-------|------|-------|----------|--------|----------|
| `tiny` | ~40MB | ⚡⚡⚡⚡⚡ | ⭐⭐⭐ | 1GB RAM | Testing, low-resource systems |
| `base` | ~75MB | ⚡⚡⚡⚡ | ⭐⭐⭐⭐ | 1GB RAM | Quick transcription tasks |
| `small` | ~250MB | ⚡⚡⚡ | ⭐⭐⭐⭐ | 2GB RAM | General use |
| `medium` | ~770MB | ⚡⚡ | ⭐⭐⭐⭐⭐ | 5GB RAM | **Recommended default** |
| `large` | ~1.5GB | ⚡ | ⭐⭐⭐⭐⭐ | 10GB RAM | Highest accuracy needs |

## 🔧 System Requirements

### Minimum
- **OS:** Windows 10, macOS 10.15, or Ubuntu 18.04+
- **CPU:** Any modern processor
- **RAM:** 4GB
- **Storage:** 2GB free space
- **Audio:** Any microphone

### Recommended
- **OS:** Windows 11, macOS 12+, or Ubuntu 20.04+
- **CPU:** Intel i5/AMD Ryzen 5 or better
- **RAM:** 8GB+
- **GPU:** CUDA-compatible GPU (optional, 2-5x speed boost)
- **Storage:** 5GB+ free space
- **Audio:** USB microphone or headset

## 🛠️ Development

This project is actively developed and maintained. See our documentation for more details:

- **[Development Logs](DEVELOPMENT_LOGS.md)** - Technical architecture and development details
- **[Change Log](CHANGELOG.md)** - Version history and updates  
- **[Development Plans](DEVELOPMENT_PLANS.md)** - Future features and roadmap
- **[Installation Guide](INSTALLATION_GUIDE.md)** - Comprehensive setup instructions

## 🤝 Contributing

We welcome contributions! Whether it's:
- 🐛 Bug reports
- 💡 Feature suggestions
- 📖 Documentation improvements
- 🔧 Code contributions

Please feel free to open an issue or submit a pull request.

## 📚 Learn More

### About Whisper
This project is powered by [OpenAI's Whisper](https://github.com/openai/whisper), a robust speech recognition model trained on diverse multilingual data.

### Technical Details
- Built with Python, PyTorch, and OpenAI Whisper
- Uses SpeechRecognition library for audio input
- Multi-threaded architecture for real-time performance
- Cross-platform audio processing with FFmpeg

## 🐛 Troubleshooting

**Common issues and solutions:**

- **FFmpeg not found** → Install FFmpeg and add to PATH
- **PyAudio installation fails** → Use `pipwin install pyaudio`
- **Microphone not detected** → Check Windows audio permissions
- **Slow performance** → Try smaller model or enable GPU acceleration

For detailed troubleshooting, see the [Installation Guide](INSTALLATION_GUIDE.md).

## 📄 License

This project is released under the [MIT License](LICENSE) - feel free to use it for any purpose.

## 🙏 Acknowledgments

- **OpenAI** for the incredible Whisper model
- **PyTorch team** for the machine learning framework
- **SpeechRecognition contributors** for audio input handling
- **The open source community** for continuous inspiration and support

---

**Made with ❤️ by PP Namias**

*Star ⭐ this repository if you find it useful!*