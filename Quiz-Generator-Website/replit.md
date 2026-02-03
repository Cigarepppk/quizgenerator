# AI Quiz Generator

## Overview

AI Quiz Generator is a web application that transforms text content into interactive quizzes. Users paste a paragraph of text, specify the number of questions they want (up to 50), and the system generates a quiz based on the provided content. The application features a clean, educational-themed interface with a pale blue color scheme.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

- **Technology**: Vanilla HTML/JavaScript with Tailwind CSS for styling
- **Design Pattern**: Single-page application with view switching (setup view, quiz view)
- **Styling Approach**: Tailwind CSS loaded via CDN with custom utility classes for the pale blue educational theme
- **Typography**: Inter font family from Google Fonts

### UI/UX Decisions

- **Color Scheme**: Pale blue educational theme with white cards and blue accents
- **Loading States**: Custom CSS spinner animation for quiz generation feedback (required due to potentially slow AI generation)
- **Responsive Design**: Max-width container (3xl/768px) with mobile-friendly padding

### Audio Integration (Replit Voice Features)

The codebase includes reusable audio utilities for voice chat functionality:
- **Audio Worklet**: Ring buffer-based PCM16 audio playback processor for streaming audio
- **React Hooks**: Custom hooks for voice recording (`useVoiceRecorder`), audio playback (`useAudioPlayback`), and SSE voice streaming (`useVoiceStream`)
- **Audio Format**: WebM/Opus for recording, PCM16 for playback at 24kHz sample rate

### API Design

- REST API patterns defined in `@shared/routes`
- Quiz generation endpoint expected to handle text input and question count
- Voice conversations endpoint for audio streaming (`/api/voice-conversations/:id/messages`)

## External Dependencies

### Frontend Dependencies (Listed in requirements.md)

| Package | Purpose |
|---------|---------|
| framer-motion | Smooth layout animations and page transitions |
| clsx | Utility for constructing className strings conditionally |
| tailwind-merge | Utility for merging Tailwind CSS classes efficiently |

### CDN Dependencies

- Tailwind CSS (via CDN script)
- Google Fonts (Inter font family)

### Browser APIs Used

- MediaRecorder API for voice recording
- AudioContext and AudioWorklet for audio playback
- Fetch API with SSE streaming for voice responses

### Backend Requirements

- Express.js server expected (based on `express.json()` references)
- AI/LLM integration for quiz generation (implementation not shown but implied by app purpose)
- Shared route definitions in `@shared/routes` module