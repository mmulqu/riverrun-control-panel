# Riverrun Control Panel

A web-based control panel for managing the Riverrun Bluesky bot with integrated Letta self-hosted server support.

## Features

### 🎮 Control Tab
- Start/Stop bot with single click
- Real-time status monitoring
- Post statistics (daily and hourly)
- Current settings overview

### 💰 Costs Tab
- AI Model selection (Google Gemini, OpenAI GPT, Anthropic Claude)
- Max posts per hour limiter (1-60 posts/hour)
- Cost estimation per model

### ⏰ Schedule Tab
- Cron frequency configuration
- Quiet Hours settings (UTC timezone)
- Schedule preview with cost savings estimation

### 🧠 Letta Tab (NEW!)
Self-hosted Letta server integration for dynamic LLM model switching.

#### Setup Instructions:

1. **Configure Your Letta Server**
   - Enter your Letta server URL (ngrok or Tailscale Funnel)
   - Examples:
     - ngrok: `https://your-id.ngrok-free.app`
     - Tailscale: `https://nucboxg3.tail903c5f.ts.net`
   - Enter your Letta server password (from `.env` file)

2. **Test Connection**
   - Click "Test Connection" button
   - Successful connection will display Letta version
   - Agent management section will appear

3. **Select Agent**
   - Choose from available Letta agents
   - View agent details:
     - Agent name
     - Current LLM model
     - Memory backend configuration

4. **Switch Model**
   - Select a new model from available models list
   - Click "Update Agent Model"
   - Model change takes effect immediately

## Letta API Integration

The control panel uses the following Letta API endpoints:

- `GET /v1/health` - Server health check
- `GET /v1/agents` - List all agents
- `GET /v1/agents/{id}` - Get agent details
- `GET /v1/models` - List available models
- `PATCH /v1/agents/{id}` - Update agent configuration

## Authentication

- **Riverrun Bot**: Password stored in localStorage (`riverrun_secret`)
- **Letta Server**: Bearer token authentication with LETTA_SERVER_PASSWORD

## Browser Storage

The control panel stores the following in localStorage:
- `riverrun_secret` - Bot control panel password
- `letta_base_url` - Letta server URL
- `letta_password` - Letta server password

## Technical Details

- **Tech Stack**: Vanilla JavaScript, HTML5, CSS3
- **Architecture**: Client-side SPA with REST API backends
- **Styling**: Dark water theme with responsive design
- **Dependencies**: None (pure vanilla JS)

## Setup & Deployment

Simply host the `index.html` file on any static web server or open directly in browser.

### Backend Requirements:

1. **Riverrun Bot Backend**: Cloudflare Worker at specified API_URL
2. **Letta Server**: Self-hosted Letta instance accessible via HTTPS

## Security Notes

- Credentials stored in browser localStorage
- Use HTTPS for all API endpoints
- Letta server should require authentication (Bearer token)
- Consider using Tailscale for persistent, secure URLs

## Development

The codebase is organized as follows:

- Lines 1-521: CSS styling (dark water theme)
- Lines 524-749: HTML structure and tabs
- Lines 766-1355: JavaScript functionality
  - Lines 766-791: Configuration and initialization
  - Lines 793-967: Riverrun bot functions
  - Lines 969-1236: Letta integration functions
  - Lines 1238-1352: Helper functions and event listeners

## Changelog

### v2.0 - Self-Hosted Letta Integration
- Added Letta tab for self-hosted server management
- Implemented agent listing and selection
- Added dynamic LLM model switching
- Letta server connection testing
- LocalStorage persistence for Letta credentials

### v1.0 - Initial Release
- Bot control (start/stop)
- Cloud model selection
- Cost management
- Schedule configuration
- Quiet hours feature

## License

MIT

## Support

For issues or questions, please refer to the Letta documentation:
- Letta Docs: https://docs.letta.com
- Letta GitHub: https://github.com/letta-ai/letta
