# Cybersecurity Awareness Chatbot - Version 1

## Overview

This is a simple console-based chatbot designed to raise awareness about fundamental cybersecurity concepts. It greets the user, asks for their name, and provides basic information in response to specific cybersecurity-related questions.

## Features

* **Voice Greeting:** Upon launching, the chatbot plays a recorded voice message welcoming the user.
* **ASCII Art Logo:** Displays a simple ASCII art logo to provide a visual element.
* **Personalized Greeting:** Asks the user for their name and uses it in subsequent interactions.
* **Basic Question Answering:** Responds to predefined questions about password safety, phishing, and safe browsing.
* **Input Validation:** Handles empty user input gracefully by prompting the user to rephrase.
* **Slight Delay:** Introduces a small delay after the bot's response to simulate a more natural conversation flow.

## Getting Started

### Prerequisites

* **Visual Studio 2022:** This project was developed using Visual Studio 2022.
* **.NET SDK:** Ensure you have the .NET Software Development Kit installed.
* **Audio File (`recording-audio.wav`):** You will need a WAV format audio file named `recording-audio.wav` for the voice greeting. Place this file in the `bin\Debug` folder of your project. The current code assumes the file is located at `C:\Users\Cedri\OneDrive\Documents\chat10bot\ConsoleApp1\bin\Debug\recording-audio.wav`. **You will need to change this path to the actual location of your audio file.**

### Running the Chatbot

1.  **Open the Project in Visual Studio 2022:** Locate the project folder and open the solution file (likely a `.sln` file) in Visual Studio.
2.  **Verify Audio File Path:** In the `Program.cs` file, within the `PlayVoiceGreeting()` method, **ensure the `myPlayer.SoundLocation` path correctly points to the `recording-audio.wav` file on your system.**
3.  **Build the Project:** In Visual Studio, navigate to `Build` > `Build Solution`.
4.  **Run the Chatbot:** Navigate to `Debug` > `Start Debugging` (or press F5).

## Usage

Once the chatbot starts in the console window:

1.  You will hear a voice greeting (if the audio file is correctly configured).
2.  An ASCII art logo will be displayed.
3.  The chatbot will ask for your name. Type your name and press Enter.
4.  The chatbot will provide a personalized welcome message and indicate the topics you can ask about.
5.  You can then type your cybersecurity-related questions and press Enter.
6.  The chatbot will attempt to provide a relevant response based on the predefined keywords.
7.  If you enter an empty line or a question it doesn't understand, it will prompt you to rephrase.
8.  To exit the chatbot, simply close the console window.

## Example Interactions
## Future Enhancements

This is a basic version of the chatbot. Future improvements could include:

* Expanding the knowledge base with more cybersecurity topics and detailed information.
* Implementing more sophisticated natural language processing (NLP) for better understanding of user input.
* Adding logging and error handling.
* Creating a more visually appealing user interface.
* Integrating with external resources or APIs for more comprehensive information.

## Project Structure

* `ChatbotV1.csproj`: The project file for the C# console application.
* `Program.cs`: Contains the main source code for the chatbot logic.
* `bin\Debug\`: (or similar) Contains the compiled executable and where the `recording-audio.wav` file should be placed.

## Version Control

This project is intended to be managed using Git for version control. You can initialize a Git repository in the project directory and use platforms like GitHub for collaboration and tracking changes.

## CI/CD Workflows

For continuous integration and continuous delivery (CI/CD), you could set up workflows using GitHub Actions. This would allow for automated building, testing, and potentially deployment of the chatbot whenever changes are pushed to the repository. A basic GitHub Actions workflow for building a .NET project might look like this (create a file `.github/workflows/build.yml`):

```yaml
name: Build

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Setup .NET
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: '6.0.x' # Or your project's .NET version
    - name: Restore dependencies
      run: dotnet restore
    - name: Build
      run: dotnet build --no-restore -c Release
