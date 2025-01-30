# AI-Powered Multimodal Assistant Documentation

# Overview : This application creates an AI assistant that combines visual (webcam) and audio inputs to provide contextual responses using large language models. 

# The system features:

- Real-time webcam streaming with frame capture
- Voice input processing with Whisper OpenAI model
- Multimodal AI responses (GPT-4o or Gemini)
- Text-to-speech output
- Conversational memory


## The code uses several libraries: openai for speech generation, cv2 for webcam access, threading for the webcam stream, speech_recognition for audio input, and langchain for the AI model interaction. The main components are the WebcamStream class, the Assistant class, and the setup for audio and webcam interactions.

## The WebcamStream class handles capturing video from the webcam in a separate thread to avoid blocking. It starts a thread that continuously reads frames, and provides methods to read the latest frame, encode it as base64, and stop the stream. The Lock ensures thread safety when accessing the frame.

## The Assistant class initializes an inference chain using LangChain. It uses a system prompt to set the AI's behavior, processes user prompts along with webcam images, generates responses using the specified model (either Gemini or GPT-4o), and converts the response to speech using OpenAI's TTS. The _create_inference_chain method sets up the LangChain pipeline with the prompt template, model, and message history.

## The main script initializes the webcam stream, sets up the model (commented options for Gemini or GPT-4o), creates an Assistant instance, and handles audio input via the Recognizer and Microphone. The audio callback processes the user's speech, sends the prompt and image to the Assistant, and displays the webcam feed in a window until the user quits.


