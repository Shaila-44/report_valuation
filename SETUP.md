# Quick Setup Guide

## Prerequisites Installation

### 1. Install Tesseract OCR (Required for Backend)

**macOS:**
```bash
brew install tesseract tesseract-lang
```

**Ubuntu/Debian:**
```bash
sudo apt-get install tesseract-ocr tesseract-ocr-tam
```

**Windows:**
Download from: https://github.com/UB-Mannheim/tesseract/wiki

### 2. Verify Installation

```bash
tesseract --version
python3 --version
node --version
```

## Configuration

### Backend Configuration

1. Copy environment template:
```bash
cd tamil-translator-api
cp .env.example .env
```

2. Edit `.env` and add your OpenAI API key:
```bash
OPENAI_API_KEY=sk-your-actual-api-key-here
```

### Frontend Configuration

```bash
cd web_app
cp .env.example .env
```

Default configuration works for local development.

## Quick Start

### Option 1: Automated Script (Recommended)

```bash
./start.sh
```

This will:
- Check all prerequisites
- Set up environment files
- Install dependencies
- Start both backend and frontend
- Show you the URLs

### Option 2: Manual Start

**Terminal 1 - Backend:**
```bash
cd tamil-translator-api
source venv/bin/activate  # or: venv\Scripts\activate on Windows
python -m src.main
```

**Terminal 2 - Frontend:**
```bash
cd web_app
npm run dev
```

## Access the Application

- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:8000
- **API Documentation:** http://localhost:8000/docs
- **Health Check:** http://localhost:8000/health

## Testing

1. Open http://localhost:5173
2. Upload a Tamil PDF document
3. Watch real-time processing progress
4. Review extracted metadata
5. Create the report

## Troubleshooting

### Backend won't start

1. **Check OpenAI API key:**
   ```bash
   cat tamil-translator-api/.env
   ```

2. **Check dependencies:**
   ```bash
   cd tamil-translator-api
   source venv/bin/activate
   pip install -r requirements.txt
   ```

3. **Check Tesseract:**
   ```bash
   which tesseract  # Should show path to tesseract
   ```

### Frontend won't start

1. **Check dependencies:**
   ```bash
   cd web_app
   npm install
   ```

2. **Check port availability:**
   Port 5173 might be in use. Kill the process or change port in `vite.config.ts`

### CORS Errors

Make sure backend `.env` has:
```bash
ALLOWED_ORIGINS=http://localhost:5173,http://localhost:3000
```

### API Connection Failed

1. Verify backend is running: `curl http://localhost:8000/health`
2. Check frontend `.env` has correct API URL
3. Check browser console for errors

## Next Steps

1. ✅ Install Tesseract OCR
2. ✅ Configure OpenAI API key
3. ✅ Run `./start.sh`
4. ✅ Upload test document
5. ✅ Verify processing works

For detailed documentation, see README.md
