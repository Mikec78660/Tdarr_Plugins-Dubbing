# Tdarr_Plugins-Dubbing

This repository contains Tdarr Flow plugins for AI-powered dubbing and audio processing.

## AI-Dubbing Plugin

The AI-Dubbing plugin is a Tdarr Flow plugin that enables automated dubbing of video files using AI services. It transcribes audio from video files, translates the transcribed text into a target language, and synthesizes new speech in the target language, which is then muxed back into the original video file.

### Features

- **Audio Transcription**: Uses AI services to transcribe audio from video files
- **Text Translation**: Translates transcribed text into a specified target language
- **Text-to-Speech Synthesis**: Converts translated text back into speech
- **Audio Muxing**: Merges the synthesized audio back into the original video file as the last audio stream
- **Configurable API Endpoint**: Supports custom API endpoints (defaulting to Speaches API)
- **Flexible Audio Stream Selection**: Can process specific audio streams from multi-audio files
- **Debug Logging**: Optional detailed logging for troubleshooting

### How It Works

1. Extracts the specified audio stream from the input video file
2. Sends the audio to an AI transcription service to generate text
3. Translates the transcribed text to the target language
4. Synthesizes speech from the translated text using a text-to-speech service
5. Muxes the new synthesized audio back into the video file as the last audio stream

### Configuration

The plugin accepts the following inputs:

- **API Endpoint URL**: Base URL of the AI service API (default: https://api.speaches.ai)
- **Target Language**: Language code for translation (default: en)
- **Audio Stream Index**: Index of the audio stream to process (default: 0)
- **Enable Debug Logging**: Toggle detailed logging for debugging purposes

### Requirements

- Tdarr Server v2.11.01 or higher
- FFmpeg installed and accessible
- Access to an AI transcription/translation/synthesis API service

### Usage

1. Add the plugin to your Tdarr Flow pipeline
2. Configure the API endpoint URL and target language
3. Specify the audio stream index to process
4. Enable debug logging if needed for troubleshooting
5. Run the pipeline to process your video files

### Development

Make sure NodeJS v16 is installed

Install dependencies:

`npm install`

Run ESLint:

`npm run lint:fix`

Check plugins using some extra custom rules:

`npm run checkPlugins`

Run tests:

`npm run test`

### Steps to write a Tdarr Flow plugin:

1. Clone this repo
2. Set env variable `pluginsDir` to the location of the plugins repo and run Tdarr Server and Node. E.g. `export pluginsDir=C:/Tdarr_Plugins`
3. Browse the typescript plugins here https://github.com/HaveAGitGat/Tdarr_Plugins/tree/master/FlowPluginsTs/CommunityFlowPlugins and make edits locally or create a new one locally: 
4. Make sure typescript is intalled with `npm i -g typescript` then run `tsc` to compile the changes.
5. Refresh the browser and Tdarr will pick up the changes

Note, `pluginsDir` directories that contain a `.git` folder (such as when cloning this repo) will cause Tdarr to skip plugin updates to prevent overwriting development changes.
