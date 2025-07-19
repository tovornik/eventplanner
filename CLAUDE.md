# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

EventPlanner is a mobile application with a companion web landing page for event planning and social interactions. The repository currently contains only the web assets for deep linking and app promotion.

## Architecture

This repository contains static web assets hosted in the `docs/` directory:

- **Landing Page**: `docs/index.html` - Main entry point for web visitors and app deep linking
- **Privacy Policy**: Available in both HTML (`docs/privacy-policy.html`) and Markdown (`docs/privacy_policy.md`) formats
- **404 Page**: `docs/404.html` - Custom error page

## Key Features

### Deep Linking System
The landing page (`docs/index.html:115-141`) implements a sophisticated deep linking mechanism:
- Extracts event IDs from URL paths (`/event/{eventId}`)
- Attempts to open the mobile app using custom URL schemes (`eventplanner://event/{eventId}`)
- Falls back to Google Play Store if app is not installed
- Auto-launches app when event ID is present in URL

### Web-to-App Flow
1. Users receive event links that load the web landing page
2. Page attempts to open EventPlanner mobile app with the specific event
3. If app is not installed, users are directed to download from Google Play Store
4. Manual "Open in App" button available as fallback

## Development Notes

### Static Site Structure
- No build process required - pure HTML/CSS/JavaScript
- All assets are self-contained in the `docs/` directory
- Designed for GitHub Pages or similar static hosting

### Styling Architecture
- Uses modern CSS with CSS Grid and Flexbox
- Implements glassmorphism design with backdrop filters
- Responsive design with mobile-first approach
- CSS is embedded in HTML files for simplicity

### Privacy Policy Maintenance
The privacy policy exists in two formats:
- `privacy_policy.md` - Source of truth for content
- `privacy-policy.html` - Web-formatted version for user viewing

When updating privacy content, ensure both files remain synchronized.

## Mobile App Integration

The web assets support a mobile app with the following characteristics:
- **Package ID**: `dev.jt.eventplanner`
- **Custom URL Scheme**: `eventplanner://`
- **Platform**: Android (Google Play Store)
- **Backend**: Google Firebase for authentication and data storage
- **Error Tracking**: Sentry integration
- **Social Features**: Friend connections, event sharing, contact suggestions

The mobile app handles:
- Google account authentication
- Event creation and management
- Social interactions and friend requests
- Push notifications
- Contact access for friend suggestions