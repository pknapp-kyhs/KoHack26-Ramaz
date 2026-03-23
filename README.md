## Project Overview

This is a dyslexia-friendly Mishnah learning application with the following key features:

- **Backend**: Flask REST API with Flask-CORS, ElevenLabs TTS, text simplification using BART, speech-to-command functionality, email notifications
- **Frontend**: React with TypeScript, Vite bundler, Tailwind CSS, Zustand state management, accessibility-first design
- **Accessibility**: Dyslexia-friendly fonts (OpenDyslexic, dyslexia-hebrew-extended), customizable text size, contrast, line height, and motion reduction
- **Audio**: Text-to-speech with character/word alignment, audio playback control, voice command input
- **Internationalization**: Multi-language support through ElevenLabs and Google Translate APIs
# KoHack26-Ramaz

---

# Project File Structure

This document provides a complete list of all source files in the KoHack26-Ramaz project with brief descriptions of their contents and purposes.

## Root Directory

| File | Description |
|------|-------------|
| `README.md` | Main project documentation and overview. |
| `.gitignore` | Git configuration file specifying which files to ignore from version control. |
| `Code Complexity Rubric` | Rubric or guide for evaluating code complexity standards used in this project. |

## Backend Directory (`/backend`)

### Core Backend Files
| File | Description |
|------|-------------|
| `main.py` | Entry point for text-to-speech (TTS) functionality, handling audio generation with alignment for English translations of Mishnah text. |
| `app.py` | Main Flask application server that provides REST API endpoints for frontend communication, including translation, text simplification, and email updates. |
| `eleven.py` | Integration with ElevenLabs API to generate multilingual text-to-speech audio with timestamps and support for multiple languages. |
| `email_service.py` | Email service module that sends study update emails with calendar invites (iCalendar format) for accessibility. |
| `Sentence_Simplify.py` | Text simplification module using BART model to simplify complex Hebrew sentences for accessibility. |
| `requirements.txt` | Python package dependencies for the backend application. |

### Speech-to-Command Module (`/backend/STC`)
| File | Description |
|------|-------------|
| `stc.py` | Speech-to-Command service that captures voice input, transcribes it, parses commands, and dispatches them to the application. |
| `__init__.py` | Python package initialization file for the STC module. |
| `requirements.txt` | Python dependencies specific to the Speech-to-Command module. |

#### STC Application Sub-module (`/backend/STC/app`)
| File | Description |
|------|-------------|
| `asr.py` | Automatic Speech Recognition module that handles voice transcription using speech-to-text technology. |
| `parser.py` | Command parser that interprets transcribed voice input and converts it into actionable commands. |
| `dispatcher.py` | Command dispatcher that routes and executes parsed voice commands to appropriate handlers. |
| `__init__.py` | Python package initialization file for the STC app sub-module. |

### Text-to-Speech Module (`/backend/TTS`)
| File | Description |
|------|-------------|
| `allignment.py` | Audio alignment module that maps character and word positions in text to their corresponding positions in generated audio files. |

#### TTS Audio Files (`/backend/TTS/audio`)
| File | Description |
|------|-------------|
| `mishnah.mp3` | Sample audio file containing audio output for Mishnah text. |

#### TTS Alignment Data (`/backend/TTS/alignment`)
| File | Description |
|------|-------------|
| `alignment.json` | ElevenLabs alignment data mapping characters to audio timestamps for synchronization. |
| `mishnah_data.json` | Mishnah text data used as the source for audio generation and alignment. |
| `remapped_chars.json` | Remapped character alignment data after processing and adjustments for audio alignment. |
| `word_alignment.json` | Word-level alignment data mapping words in the text to their positions in the audio file. |

## Frontend Directory (`/frontend`)

### Configuration Files
| File | Description |
|------|-------------|
| `package.json` | Node.js project metadata and dependencies for the React frontend application. |
| `package-lock.json` | Locked dependency versions for reproducible npm package installations. |
| `tsconfig.json` | TypeScript compiler configuration for the frontend application. |
| `tsconfig.node.json` | TypeScript configuration for Node.js build tools (Vite). |
| `vite.config.ts` | Vite build tool configuration for development and production builds. |
| `tailwind.config.js` | Tailwind CSS configuration for utility-first styling framework. |
| `postcss.config.js` | PostCSS configuration for processing CSS with plugins (used by Tailwind). |
| `jest.config.cjs` | Jest testing framework configuration for unit and component tests. |
| `.eslintrc.cjs` | ESLint linting rules configuration for code quality standards. |
| `.gitignore` | Git configuration specifying which files to ignore in the frontend directory. |
| `components.json` | Component generation or configuration file for the UI component library. |
| `index.html` | Main HTML entry point for the React application. |
| `README.md` | Frontend-specific documentation. |

### Main Application Files
| File | Description |
|------|-------------|
| `src/main.tsx` | React application entry point that initializes and renders the main App component. |
| `src/App.tsx` | Root React component that sets up routing, theme settings, and global accessibility features. |
| `src/App.css` | Global CSS styles for the main App component and layout. |
| `src/index.css` | Global CSS styles and Tailwind directives for the entire application. |
| `src/App.test.tsx` | Unit tests for the App component and main application logic. |
| `src/setupTests.ts` | Jest setup configuration for testing environment initialization. |
| `src/vite-env.d.ts` | Vite environment type definitions for TypeScript. |

### API Module (`/frontend/src/api`)
| File | Description |
|------|-------------|
| `client.ts` | HTTP client configuration for making requests to the backend API. |
| `auth.ts` | Authentication API endpoints for login, logout, and session management. |
| `apps.ts` | Application-related API endpoints for data fetching and management. |
| `collections.ts` | Collections API endpoints for managing user collections and study materials. |

### Store Module (`/frontend/src/store`)
| File | Description |
|------|-------------|
| `useAuthStore.ts` | Zustand store for managing authentication state and user session data. |
| `useSettingsStore.ts` | Zustand store for managing user preferences including accessibility settings (font size, contrast, dyslexia font). |
| `useAudioStore.ts` | Zustand store for managing audio playback state and control. |
| `useCounterStore.ts` | Zustand store for managing counter/counter-related application state. |

### Components (`/frontend/src/components`)
| File | Description |
|------|-------------|
| `AudioPlayerBar.tsx` | Audio player control component with play/pause, volume, and progress controls. |
| `VoiceCommandControl.tsx` | Voice command input component that captures and processes voice commands from users. |
| `layout.tsx` | Layout wrapper component providing consistent page structure and styling. |
| `slider.tsx` | Custom slider component wrapper for user input with drag controls. |
| `toggle.tsx` | Toggle switch component for boolean settings and preferences. |

#### UI Components (`/frontend/src/components/ui`)
| File | Description |
|------|-------------|
| `button.tsx` | Reusable button component with accessibility features and styling variants. |
| `input.tsx` | Text input field component with accessibility support. |
| `label.tsx` | Form label component for associating labels with form inputs. |
| `slider.tsx` | Range slider component for selecting values within a range. |

### Routing (`/frontend/src/routing`)
| File | Description |
|------|-------------|
| `AppRoutes.tsx` | Route definitions and navigation configuration for the React Router application. |

### Pages (`/frontend/src/pages`)
| File | Description |
|------|-------------|
| `HomePage.tsx` | Home page component displaying the main landing and navigation interface. |
| `LoginPage.tsx` | User login page with authentication form. |
| `MishnahYomiViewer.tsx` | Dedicated page for viewing the daily Mishnah with audio, text simplification, and voice controls. |
| `UserSettingsPage.tsx` | Settings page where users can configure accessibility options, preferences, and profile information. |
| `About.tsx` | About page containing project information and documentation. |
| `Default.tsx` | Default/fallback page template for new routes. |
| `NotFound.tsx` | 404 error page displayed when routes are not found. |

### Utilities (`/frontend/src/lib`)
| File | Description |
|------|-------------|
| `utils.ts` | Utility functions and helper methods used throughout the frontend application. |

### Assets (`/frontend/src/assets`)
| File | Description |
|------|-------------|
| `react.svg` | React logo SVG asset. |
| `fonts/` | Custom fonts directory (OpenDyslexic variants for accessibility). |

### Public Assets (`/frontend/public`)
| File | Description |
|------|-------------|
| `vite.svg` | Vite logo SVG asset. |
| `fonts/` | Public fonts directory (OpenDyslexic variants and dyslexia-hebrew-extended font for dyslexia-friendly interface). |

#### Font Files
| File | Description |
|------|-------------|
| `OpenDyslexic-Regular.otf` | Regular weight of OpenDyslexic font designed for dyslexic readers. |
| `OpenDyslexic-Bold.otf` | Bold weight of OpenDyslexic font for emphasis. |
| `OpenDyslexic-Italic.otf` | Italic weight of OpenDyslexic font for styling. |
| `OpenDyslexic-BoldItalic.otf` | Bold italic weight of OpenDyslexic font. |
| `dyslexia-hebrew-extended.otf` | Hebrew-extended font optimized for dyslexic readers, supporting Hebrew text. |

## Miscellaneous Files (`/misc-root-files`)

| File | Description |
|------|-------------|
| `LICENSE` | Project license file. |
| `README.md` | Miscellaneous documentation. |