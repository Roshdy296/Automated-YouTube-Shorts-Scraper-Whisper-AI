Markdown
# 🎬 Automated YouTube Shorts Scraper & Whisper AI Engine

An end-to-end Python automation pipeline designed to scrape viral YouTube Shorts by hashtag, transcribe audio using OpenAI's Whisper, identify key video highlights, and automatically sync outputs to Google Sheets and Google Drive.

---

## 📌 Project Overview

This project automates the content pipeline for short-form video creation and metadata analysis. By combining web scraping, audio-to-text machine learning models, and cloud API integrations, the system eliminates manual content searching and video transcribing.

### Key Features
* **Automated Scraping:** Uses `yt-dlp` to extract metadata and download YouTube Shorts by target hashtags or search terms.
* **Local AI Transcription:** Leverages OpenAI's `Whisper` model locally for accurate speech-to-text conversion.
* **Aspect Ratio Conversion:** Automates video cropping to standard 9:16 vertical short formats using `MoviePy` / `OpenCV`.
* **Cloud Synchronization:** Automatically uploads processed clips to Google Drive (`PyDrive2`) and records video metrics into Google Sheets (`gspread`).

---

## 🛠️ Architecture & Tech Stack

* **Language:** Python 3.10+
* **Scraping & Media Retrieval:** `yt-dlp`
* **AI & Transcription:** `openai-whisper`, `torch`
* **Video Editing & Manipulation:** `moviepy`, `opencv-python`
* **Cloud & Automation API:** `gspread`, `PyDrive2`, `openpyxl`
* **Environment Support:** Local Environment & Google Colab

---

## 🚀 Getting Started

### 1. Prerequisites
Ensure you have `ffmpeg` installed on your system for media manipulation:

* **Ubuntu/Debian:** `sudo apt install ffmpeg`
* **MacOS:** `brew install ffmpeg`
* **Windows:** Install via `choco install ffmpeg` or download directly from official releases.

### 2. Installation

Clone the repository and install dependencies:

```bash
git clone [https://github.com/Roshdy296/Automated-YouTube-Shorts-Scraper-Whisper-AI.git](https://github.com/Roshdy296/Automated-YouTube-Shorts-Scraper-Whisper-AI.git)
cd Automated-YouTube-Shorts-Scraper-Whisper-AI
pip install -r requirements.txt
💻 Code Quickstart
Python
import pandas as pd
import yt_dlp
import whisper

def scrape_shorts(hashtag="tech", max_results=5):
    ydl_opts = {'quiet': True, 'extract_flat': True}
    search_query = f"ytsearch{max_results}:#{hashtag} shorts"
    
    with yt_dlp.YoutubeDL(ydl_opts) as ydl:
        info = ydl.extract_info(search_query, download=False)
        
    videos = []
    if 'entries' in info:
        for entry in info['entries']:
            videos.append({
                'ID': entry.get('id'),
                'Title': entry.get('title'),
                'URL': f"[https://www.youtube.com/watch?v=](https://www.youtube.com/watch?v=){entry.get('id')}"
            })
    return pd.DataFrame(videos)

def transcribe(audio_path):
    model = whisper.load_model("base")
    result = model.transcribe(audio_path)
    return result['text']

if __name__ == "__main__":
    df = scrape_shorts("dataanalysis", max_results=3)
    df.to_excel("metadata_output.xlsx", index=False)
    print("Scraping completed. Saved to metadata_output.xlsx")
📂 Repository Structure
Plaintext
├── src/
│   ├── scraper.py          # Scrapes YouTube metadata via yt-dlp
│   ├── transcriber.py      # Audio extraction & OpenAI Whisper integration
│   └── drive_sync.py       # Syncs processed videos to Google Drive
├── data/                   # Directory for storing output Excel files & downloaded audio
├── requirements.txt        # Required Python packages
├── .gitignore              # Excludes temp media files, models, and API keys
└── README.md               # Project documentation
👤 Author
Mohamed Rashidi

GitHub: @Roshdy296

Portfolio: roshdy296.github.io
