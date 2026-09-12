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
