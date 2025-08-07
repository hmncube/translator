# Simple Translation App Plan

## Project Overview
A straightforward translation application with three core features: speech-to-text input, text translation via Gemini API, and text-to-speech output. Focus on simplicity, reliability, and ease of use.

## Core Features (MVP)
- **Speech-to-Text**: Record audio and convert to text
- **Text Translation**: Translate text between languages using Gemini API
- **Text-to-Speech**: Play translated text as audio
- **Language Selection**: Simple dropdown for source and target languages
- **Basic UI**: Clean, minimal interface

## Technical Architecture

### Frontend (Single Page Application)
- **Framework**: Vanilla JavaScript or simple React app
- **Speech Recognition**: Web Speech API (built into modern browsers)
- **Text-to-Speech**: Web Speech Synthesis API (built into browsers)
- **Storage**: LocalStorage for recent translations (optional)

### API Integration
- **Translation Service**: Direct calls to Gemini API from frontend
- **Authentication**: Simple API key (stored securely in environment)
- **Error Handling**: Basic try/catch with user-friendly messages

### File Structure
```
/src
  /components
    - SpeechInput.js
    - TranslationDisplay.js
    - LanguageSelector.js
    - SpeechOutput.js
  - App.js
  - api.js
  - styles.css
  index.html
```

## Implementation Details

### Core Components
1. **Audio Recording**: Use `navigator.mediaDevices.getUserMedia()` and `MediaRecorder`
2. **Speech Recognition**: `webkitSpeechRecognition` or `SpeechRecognition`
3. **Translation**: Simple fetch to Gemini API with basic prompt
4. **Speech Synthesis**: `speechSynthesis.speak()` with `SpeechSynthesisUtterance`

### Basic API Structure
```javascript
const translateText = async (text, sourceLang, targetLang) => {
  const prompt = `Translate "${text}" from ${sourceLang} to ${targetLang}`;
  // Simple Gemini API call
};
```

### Supported Languages (Start Simple)
- English, Spanish, French, German, Italian, Portuguese, Chinese, Japanese, Korean
- Expandable list as needed

## User Interface

### Layout
- **Top**: Language selector (From/To dropdowns with swap button)
- **Middle**: Large text area showing original and translated text
- **Bottom**: Three buttons - Record, Translate, Play Audio

### User Flow
1. Select source and target languages
2. Click record button and speak
3. Speech converts to text automatically
4. Click translate button
5. Translation appears below original text
6. Click play button to hear translation

## Development Timeline

### Week 1: Core Setup
- Set up basic HTML/CSS/JS structure
- Implement speech-to-text with Web Speech API
- Basic language selection UI

### Week 2: Translation & TTS
- Integrate Gemini API for translation
- Implement text-to-speech functionality
- Connect all components together

### Week 3: Polish & Testing
- Error handling and edge cases
- UI improvements and responsive design
- Basic testing on different browsers/devices

## Technical Requirements

### Browser Support
- Chrome/Edge (full Web Speech API support)
- Firefox/Safari (limited speech features, fallback to text input)

### Dependencies
- Minimal: No complex frameworks or libraries
- Optional: Simple CSS framework like Tailwind for styling

### Security
- API key stored in environment variables
- Input sanitization before API calls
- HTTPS required for microphone access

## Quality Assurance

### Basic Testing
- Manual testing of core user flows
- Test on mobile and desktop browsers
- Verify speech recognition accuracy in quiet environments

### Performance
- Keep bundle size minimal (< 100KB)
- Fast API response times (aim for < 3 seconds)
- Graceful handling of network failures

## Deployment

### Simple Hosting
- Static site hosting (Netlify, Vercel, GitHub Pages)
- Environment variable for API key
- Basic analytics (Google Analytics) if needed

### Maintenance
- Monitor API usage and costs
- Update supported languages as needed
- Fix bugs reported by users

## Success Criteria
- Speech recognition works reliably in quiet environments
- Translation accuracy is good for common phrases
- Text-to-speech output is clear and understandable
- App loads quickly and works on mobile devices
- Users can complete translate workflow in under 30 seconds

## Future Enhancements (Only if needed)
- History of recent translations (localStorage)
- Keyboard shortcuts for power users
- Better error messages and help text
- Support for more languages
- Offline translation for common phrases

## Notes
- Start with core functionality first
- Add features only based on actual user feedback
- Keep codebase simple and maintainable
- Focus on reliability over complexity