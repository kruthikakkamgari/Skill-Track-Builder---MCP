This project is a Streamlit web application that acts as a "Day-wise Learning Path Generator." It leverages a powerful language model to create personalized, structured learning plans based on a user's goal. The generated learning path is saved to a Google Drive document or a Notion page and includes a corresponding YouTube playlist of curated videos for each topic.

This application is a proof-of-concept for the Model Context Protocol (MCP), demonstrating how an AI agent can interact with various external tools (Google Drive, Notion, YouTube) to fulfill a complex user request.

## Core Functionality

  - **AI-Powered Learning Path Generation**: Enter a learning goal (e.g., "learn Python basics in 3 days"), and the AI agent will generate a day-by-day curriculum.
  - **Dynamic Content Curation**: The agent searches YouTube for relevant educational videos for each topic in the learning path and selects the most suitable one.
  - **Multi-Tool Integration**: Seamlessly integrates with Google Drive and Notion to store the generated learning path, and with YouTube to create a public playlist.
  - **User-Friendly Interface**: A simple Streamlit interface allows users to input their API keys, service URLs, and learning goals.
  - **Real-time Progress Updates**: The application provides real-time feedback on the agent's progress as it generates the learning path.

-----

## How It Works

The application follows a structured, multi-step process orchestrated by an AI agent:

1.  **Plan the Learning Path**: Based on the user's goal, the agent devises a logical, day-wise structure of topics.
2.  **Research Video Resources**: It searches for relevant YouTube videos for each topic.
3.  **Select Core Videos**: The agent selects the best foundational video for each day's topic.
4.  **Format Document**: The learning path is formatted with titles, daily topics, and YouTube links.
5.  **Create and Populate Document**: A new Google Drive document or Notion page is created and populated with the formatted learning path.
6.  **Create YouTube Playlist**: A public YouTube playlist is created with the curated videos.
7.  **Provide Final Output**: The application returns the links to the newly created document and YouTube playlist.

-----

## File Structure

  - **`app.py`**: The main Streamlit application file. It handles the user interface, inputs, and displays the final results.
  - **`utils.py`**: Contains the core logic for setting up the AI agent, initializing the language model, and running the learning path generation process. It uses `langchain` and `langgraph` to create and manage the agent.
  - **`prompt.py`**: Defines the main instruction prompt that guides the AI agent's behavior and ensures it follows the required step-by-step execution flow.
  - **`requirements.txt`**: Lists the necessary Python packages for running the application.

-----

## Setup and Usage

### Prerequisites

  - Python 3.7+
  - A Google API Key.
  - Pipedream accounts to create webhook URLs for YouTube, Google Drive, and/or Notion.

### Installation

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```
2.  **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```

### Configuration

1.  **Run the Streamlit application:**
    ```bash
    streamlit run app.py
    ```
2.  **Open the application in your browser.**
3.  **In the sidebar, you will need to configure the following:**
      * **Google API Key**: Enter your secret Google API key.
      * **Pipedream URLs**:
          * **YouTube URL (Required)**: Provide the Pipedream webhook URL for YouTube actions.
          * **Secondary Tool**: Choose between "Drive" or "Notion".
          * **Drive URL / Notion URL**: Provide the corresponding Pipedream webhook URL for the selected secondary tool.

### How to Use

1.  Complete the configuration steps in the sidebar.
2.  Enter your learning goal in the text input field (e.g., "I want to learn the basics of data analysis in 7 days").
3.  Click the "Generate Learning Path" button.
4.  Wait for the process to complete. You can monitor the progress in the main area of the application.
5.  Once finished, the application will display links to your generated Google Drive document/Notion page and the YouTube playlist.

-----

## Dependencies

The project relies on the following major Python libraries:

  - `streamlit`: For creating the web application interface.
  - `langchain`, `langgraph`, `langchain-google-genai`: For building and running the AI agent with Google's generative models.
  - `langchain-mcp-adapters`: To facilitate communication between the LangChain agent and the external tools via the Model Context Protocol.
