# MedGemma-Powered Multilingual STT/TTS Voice Assistant for Radiology Reports

## 🌟 Overview
This project is an **AI-driven multilingual voice assistant** designed to streamline the **radiology reporting process**.  
It enables radiologists to **dictate findings in local languages** like Urdu, Punjabi, Saraiki, and Pashto and automatically:
- **Transcribe speech to text** using **Whisper** with **Pyannote diarization** to separate doctor and patient voices.
- **Generate structured radiology reports** using **Google's MedGemma LLM** hosted on **Ollama**.
- **Create FHIR-compliant intake forms** for seamless integration with modern EMR systems.
- Provide **voice-based playback (TTS)** of reports for accessibility.

The solution improves reporting speed, accuracy, and accessibility in **multilingual healthcare environments**.

---

## ✨ Features
- 🎙 **Speech-to-Text (STT)**  
  - Multilingual transcription (Urdu, Punjabi, English) using **Whisper**.  
  - **Pyannote diarization** for separating doctor and patient voices.

- 🩺 **AI-Powered Report Generation**  
  - Structured and coherent radiology reports via **MedGemma LLM**.
  - FHIR-compliant data structures for interoperability with EMRs.

- 🔊 **Text-to-Speech (TTS)**  
  - Native language report playback using **Bark** or **Coqui**.

- 🤖 **Agent Layer**  
  - Fetch patient history dynamically.
  - Suggest report templates based on modality (e.g., X-ray, CT).

- ⚡ **Remote GPU Wrappers**  
  - Run heavy AI models on external GPU platforms like **Kaggle**.
  - Access them locally via APIs to handle limited local hardware resources.

- ⚙ **Backend APIs**  
  - Built with **FastAPI**, providing modular endpoints:
    - `/transcribe` – Speech-to-text conversion.
    - `/generate-report` – Generate radiology reports with MedGemma.
    - `/fhir/intake-form` – Create FHIR-compliant forms.

---

## 🧰 Tech Stack

| **Category**         | **Tools & Frameworks**            |
|-----------------------|-----------------------------------|
| **LLM**              | MedGemma (via Ollama)            |
| **Speech-to-Text**   | Whisper, Pyannote                |
| **Text-to-Speech**   | Bark, Coqui                       |
| **Backend**          | FastAPI, Python                   |
| **Database**         | MongoDB, SQLite                   |
| **FHIR Support**     | Pydantic-FHIR                     |
| **Frontend (Demo)**  | React Native, Tailwind CSS        |

---

## 🗂 System Architecture

Radiologist Speech
↓
Whisper + Pyannote (STT + Diarization)
↓
Structured Text
↓
MedGemma (LLM) → FHIR-Compliant Report
↓
Optional TTS Playback
↓
Final Output


---

## 🚀 Setup Instructions

### **Prerequisites**
- Python 3.10+
- FastAPI
- GPU-enabled environment **or** remote GPU setup (e.g., Kaggle)
- MongoDB or SQLite
- Ollama installed to host MedGemma locally

---

### **Installation**
1. **Clone the repository:**
   git clone https://github.com/your-username/medgemma-radiology-assistant.git
   cd medgemma-radiology-assistant
 
2. **Create and activate a virtual environment:**

python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

3. **Install dependencies:**
pip install -r requirements.txt
4. **Start the FastAPI server:**
uvicorn main:app --reload
🌐 API Endpoints
| **Endpoint**        | **Method** | **Description**                       |
| ------------------- | ---------- | ------------------------------------- |
| `/transcribe`       | POST       | Convert speech to text (STT).         |
| `/generate-report`  | POST       | Generate structured radiology report. |
| `/fhir/intake-form` | POST       | Generate FHIR-compliant intake form.  |

📌 Usage Example

Upload an audio file containing a radiologist’s dictation to the /transcribe endpoint.

1. Receive the transcription, with doctor and patient voices separated.

2. Send the transcribed text to the /generate-report endpoint to generate a complete radiology report.

3. (Optional) Generate a FHIR-ready form via /fhir/intake-form.

4. Use TTS to play back the report in a selected local language.
   
🔮 Future Enhancements

Build a full mobile/web frontend for deployment.

- Expand language support to additional dialects.
- Improve TTS models for natural and localized voices.
- Integrate directly with hospital EMRs for real-world usage

