# Voice AI Assistant (Twilio + OpenAI Realtime API)

A Node.js application that enables phone conversations with customizable AI personas using Twilio Voice and OpenAI's Realtime API.

## Prerequisites

1. Node.js 18+
2. Twilio Account (can sign up for free at twilio.com)
3. Twilio Phone Number with Voice capabilities 
4. OpenAI Account with API Key and Realtime API access

## Quick Setup

1. **Install ngrok**
  - Download from ngrok.com
  - Run: `ngrok http 5050`
  - Copy the https URL (e.g., `https://your-subdomain.ngrok.app`)

2. **Install Dependencies**
  ```bash
  npm install

Configure Environment


Create a .env
Add your OpenAI API key:
OPENAI_API_KEY=your-key-here



Configure Twilio

Go to Twilio Console > Phone Numbers > Active Numbers
Click your phone number
Under "Voice & Fax" section:

Set "A Call Comes In" to "Webhook"
Set URL to: https://your-ngrok-subdomain.ngrok.app/incoming-call
Save changes




Start the Server
node index.js


Managing Personas
Default Persona
The system comes with a default friendly AI assistant persona.
Add New Persona
POST to /persona:
jsonCopy{
    "name": "custom_name",
    "config": {
        "systemMessage": "Your personality description here",
        "voice": "alloy",
        "temperature": 0.8
    }
}
Use Different Persona
Add ?persona=custom_name to your Twilio webhook URL:
Copyhttps://your-ngrok-subdomain.ngrok.app/incoming-call?persona=custom_name
View All Personas
GET /personas
Edit Persona
PUT /persona/custom_name with updated config
Testing

Start your server (node index.js)
Ensure ngrok is running
Call your Twilio phone number
Start talking with the AI!

API Costs

OpenAI charges for Realtime API usage
Twilio charges for voice minutes and phone number rental

Monitor your usage in respective dashboards.