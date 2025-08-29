# AutoGen-Gemini

A demonstration of multi-agent collaboration using AutoGen framework with Google's Gemini models for building intelligent applications.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/adityasahu2/AutoGen-Gemini/blob/main/AutoGen_Gemini.ipynb)

## Overview

This repository showcases how to integrate Google's Gemini models with Microsoft's AutoGen framework to create collaborative AI agents that can work together on complex tasks. The notebook demonstrates two main scenarios:

1. **Simple Task Execution**: A basic bubble sort implementation
2. **Complex Multi-Agent Collaboration**: Designing a multimodal accessibility application for visually impaired users

## Features

- **Multi-Agent Orchestration**: Utilizes AutoGen's group chat functionality for agent collaboration
- **Gemini Integration**: Configured to work with various Gemini model variants
- **Practical Applications**: Demonstrates real-world use cases including accessibility technology design
- **Collaborative Planning**: Shows how different agent roles (Product Manager, Coder, Tester) can work together

## Prerequisites

- Python 3.7+
- Google AI API key for Gemini models
- Basic understanding of AI agents and multi-agent systems

## Installation

### Option 1: Google Colab (Recommended)
Click the "Open in Colab" badge above to run the notebook directly in Google Colab.

### Option 2: Local Installation

```bash
# Clone the repository
git clone https://github.com/adityasahu2/AutoGen-Gemini.git
cd AutoGen-Gemini

# Install required packages
pip install autogen-ext
pip install autogen
pip install flask  # If running backend components
```

## Configuration

### API Setup

1. **Get Gemini API Key**: 
   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Generate your API key

2. **Update Configuration**:
   ```python
   OAI_CONFIG_LIST = [
       {
           "model": "gemini-1.5-flash-latest",
           "api_key": "YOUR_API_KEY_HERE",  # Replace with your actual API key
           "api_type": "google"
       }
   ]
   ```

## Usage

### Basic Example - Bubble Sort
```python
import autogen
from autogen import AssistantAgent, UserProxyAgent

# Configure agents
assistant = AssistantAgent(
    "assistant", 
    llm_config={"config_list": config_list_gemini, "seed": 25}
)

user_proxy = UserProxyAgent(
    "user_proxy",
    code_execution_config={"work_dir": "coding", "use_docker": False},
    human_input_mode="NEVER"
)

# Start conversation
result = user_proxy.initiate_chat(
    assistant, 
    message="Sort the array with Bubble Sort: [4, 1, 5, 2, 3]"
)
```

### Advanced Example - Multi-Agent Collaboration

The notebook demonstrates a sophisticated multi-agent system for designing "SeeAI" - an accessibility application:

- **Product Manager**: Designs product features and user experience
- **Coder**: Implements technical solutions and prototypes
- **Tester**: Validates functionality and accessibility compliance
- **User Proxy**: Coordinates execution and manages the workflow

## Key Components

### Agent Roles

1. **Assistant Agent**: Handles code generation and technical tasks
2. **Product Manager**: Creative design and product strategy
3. **Coder**: Technical implementation and architecture
4. **Tester**: Quality assurance and validation
5. **User Proxy**: Execution coordinator and human interface

### Supported Gemini Models

- `gemini-1.5-flash-latest`
- `gemini-1.5-pro-001`
- `gemini-1.5-pro`
- `gemini-pro-vision`

## Project Structure

```
AutoGen-Gemini/
├── AutoGen_Gemini.ipynb    # Main notebook with examples
├── README.md               # This file
├── coding/                 # Output directory for generated code
└── requirements.txt        # Dependencies (if added)
```

## Example Output

The multi-agent collaboration produces:

- **Product Design**: Complete specification for SeeAI accessibility app
- **Technical Architecture**: Flutter frontend with Flask backend prototype
- **Implementation Strategy**: Detailed development roadmap
- **Quality Validation**: Testing protocols for accessibility compliance

## Applications Demonstrated

### SeeAI - Accessibility Application
A multimodal product for visually impaired users featuring:
- Real-time image analysis using computer vision
- Audio descriptions of surroundings
- Haptic feedback for spatial awareness
- Object detection and localization
- Cross-platform mobile implementation

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Security Notes

⚠️ **Important**: Never commit API keys to version control. The notebook contains placeholder API keys that should be replaced with your actual credentials.

## Limitations

- Requires active internet connection for Gemini API calls
- API rate limits may apply based on your Google AI usage tier
- Some advanced features may require additional setup

## Troubleshooting

### Common Issues

1. **API Key Errors**: Ensure your Gemini API key is valid and properly configured
2. **Package Installation**: Some package combinations may conflict; use virtual environments
3. **Model Availability**: Not all Gemini models may be available in all regions

### Getting Help

- Check the [AutoGen Documentation](https://microsoft.github.io/autogen/)
- Review [Google AI Documentation](https://ai.google.dev/docs)
- Open an issue in this repository for specific problems

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Microsoft AutoGen team for the multi-agent framework
- Google for providing Gemini models and APIs
- Contributors and the open-source community

## Related Projects

- [Microsoft AutoGen](https://github.com/microsoft/autogen)
- [Google AI Python SDK](https://github.com/google/generative-ai-python)

---

**Note**: This is a demonstration project. For production use, implement proper error handling, security measures, and scalability considerations.
