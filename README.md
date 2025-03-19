# GitHub Stars Explorer

This project helps you analyze, search, and visualize your GitHub starred repositories using semantic search, LLM-based summarization, and interactive visualizations.

## Features

- **Fetch GitHub Starred Repositories**: Retrieve all your starred repositories with comprehensive metadata
- **README Analysis**: Extract and summarize README files using various LLM providers
- **Semantic Search**: Use hybrid search with embeddings to find repositories based on concepts
- **Auto-Tagging**: Generate descriptive tags for better categorization and filtering
- **Interactive UI**: Explore your starred repositories through a Streamlit interface
- **Visualizations**: Gain insights with tag clouds, language distribution charts, and network graphs

## Setup Instructions

### Prerequisites

- Python 3.9+
- GitHub personal access token
- At least one of the following LLM API keys: Azure OpenAI, OpenAI, Anthropic, Google, or local Ollama setup

### Installation

1. Clone this repository:
   ```bash
      git clone https://github.com/yourusername/github-stars-explorer.git
         cd github-stars-explorer
            ```

            2. Install dependencies:
               ```bash
                  pip install -r requirements.txt
                     ```

                     3. Create a `.env` file in the project root and add your API keys:
                        ```
                           GITHUB_TOKEN=your_github_token_here
                              AZURE_API_KEY=your_azure_openai_api_key_here
                                 AZURE_ENDPOINT=your_azure_endpoint_here
                                    OPENAI_API_KEY=your_openai_api_key_here
                                       ANTHROPIC_API_KEY=your_anthropic_api_key_here
                                          GOOGLE_API_KEY=your_google_api_key_here
                                             OLLAMA_API_BASE=http://localhost:11434
                                                ```

                                                   You only need to provide API keys for the services you intend to use. At minimum, you'll need the GitHub token and at least one LLM API key.

                                                   ### Usage

                                                   1. Run the data collection script:
                                                      ```bash
                                                         python github_star_explorer.py
                                                            ```
                                                               This will process all your starred repositories and store them in a local ChromaDB database.

                                                               2. Launch the Streamlit app:
                                                                  ```bash
                                                                     streamlit run streamlit_app.py
                                                                        ```

                                                                        3. Open your browser and navigate to http://localhost:8501 to explore your repositories.

                                                                        ## How It Works

                                                                        ### Data Collection Process

                                                                        1. **Fetch Repositories**: Retrieve all starred repositories using the GitHub API
                                                                        2. **Extract Metadata**: Collect repository details, languages, topics, and other metadata
                                                                        3. **Process READMEs**: Extract and summarize README content using LLMs
                                                                        4. **Generate Tags**: Create descriptive tags based on repository content and metadata
                                                                        5. **Embed Summaries**: Generate vector embeddings for semantic search capabilities
                                                                        6. **Store Data**: Save all processed data in a ChromaDB vector database

                                                                        ### Search and Visualization

                                                                        The Streamlit app provides several ways to explore your repositories:

                                                                        - **Semantic Search**: Find repositories based on concepts, not just keywords
                                                                        - **Filtering**: Narrow down results by language, tags, or star count
                                                                        - **Repository Cards**: View detailed information about each repository
                                                                        - **Tag Cloud**: Visualize the most common tags across your starred repositories
                                                                        - **Language Distribution**: See the breakdown of programming languages
                                                                        - **Repository Network**: Explore connections between repositories based on shared tags

                                                                        ## Customization

                                                                        - **LLM Providers**: The system will automatically try different LLM providers in the following order: Azure OpenAI, OpenAI, Anthropic, Google, and local Ollama models.
                                                                        - **Embedding Models**: By default, the system uses OpenAI's text-embedding-3-large or falls back to local embeddings if no API keys are available.
                                                                        - **Token Limits**: README content is truncated to stay within LLM token limits (12,000 characters)
                                                                        - **Database Location**: You can modify the `DB_DIRECTORY` constant in the scripts to change where data is stored

                                                                        ## LLM Provider Configuration

                                                                        The system is designed to work with multiple LLM providers and will try them in the following order:

                                                                        1. **Azure OpenAI**: If you have Azure OpenAI credentials configured
                                                                        2. **OpenAI**: If you have an OpenAI API key
                                                                        3. **Anthropic**: If you have an Anthropic API key for Claude models
                                                                        4. **Google**: If you have a Google API key for Gemini models
                                                                        5. **Ollama**: If you have Ollama running locally

                                                                        You only need one working provider for the system to function. The priority order can be modified by changing the `LLM_PRIORITY` list in the main script.

                                                                        ## Troubleshooting

                                                                        - **Rate Limiting**: If you're processing many repositories, you might encounter GitHub API rate limits. The script includes built-in delays to minimize this risk.
                                                                        - **Missing READMEs**: Some repositories don't have README files or have them in non-standard locations. The system handles these cases gracefully.
                                                                        - **LLM API Errors**: If an LLM provider fails, the system will automatically try the next one in the priority list.
                                                                        - **Database Connection**: Make sure the ChromaDB directory has proper write permissions.

                                                                        ## Contributing

                                                                        Contributions are welcome! Please feel free to submit a Pull Request.

                                                                        ## License

                                                                        This project is licensed under the MIT License - see the LICENSE file for details.
