# ACTMS - Anti-Corruption Tender Management System

## Overview

ACTMS (Anti-Corruption Tender Management System) is a comprehensive web application designed to ensure transparency and integrity in government tender processes. The system combines traditional tender management with advanced AI-powered fraud detection to create a centralized platform where government departments can publish tenders, companies can submit bids, and administrators can monitor the entire process for irregularities using machine learning algorithms.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Backend Architecture
The system uses a **Flask-based REST API** architecture with modular service components. The main application (`app.py`) serves as the central controller that orchestrates various specialized services:

- **Database Service**: SQLite-based data persistence layer handling tenders, bids, and audit logs with comprehensive tracking
- **ML Service**: Isolation Forest-based anomaly detection system for identifying suspicious bid patterns using scikit-learn
- **Chatbot Service**: OpenAI GPT integration with FAQ fallback system for user assistance and support
- **NLP Service**: Text analysis service using spaCy for proposal evaluation and quality scoring
- **File Handler**: Secure file upload and validation system with hash verification and content filtering

### Frontend Architecture
The system uses a **static HTML/CSS/JavaScript frontend** with Tailwind CSS-inspired custom styling and Chart.js for data visualization. The frontend implements a glassmorphism design system with monochrome colors (black/gray/white) and radiant beam effects. Communication with the backend occurs through RESTful API calls using vanilla JavaScript with custom ACTMS utility classes.

### Data Storage Solutions
**SQLite Database** serves as the primary data store with three main tables:
- **Tenders**: Store tender information including metadata, requirements, budgets, and file references
- **Bids**: Store bid submissions with anomaly scores, suspicious flags, and company information
- **Audit Logs**: Track all system actions including user activities, security events, and system changes

File storage uses a **local filesystem approach** with uploads stored in `/uploads` directory and trained ML models persisted in `/models` directory using joblib.

### Machine Learning Architecture
The system employs **Isolation Forest algorithm** from scikit-learn for unsupervised anomaly detection featuring:
- 10% contamination threshold for flagging potentially suspicious bids
- Feature extraction from bid amounts, proposal text quality, timing patterns, and company information
- Model persistence and retraining capabilities with performance metrics tracking
- Integration with NLP service for text analysis and quality scoring

### Security and Validation
Multi-layered security approach includes:
- **File validation**: Size limits (15MB), extension filtering, MIME type verification, and dangerous signature detection
- **Hash verification**: SHA-256 hashing for file integrity and tamper detection
- **Audit logging**: Comprehensive action tracking for transparency and accountability
- **Input sanitization**: Secure filename handling, request validation, and SQL injection prevention

### User Interface Design
The frontend implements a **glassmorphism design system** with:
- Monochrome color palette (black, gray, white only)
- Frosted glass panels with backdrop blur effects
- Radiant beam background animations
- Responsive grid layouts and animated transitions
- Progressive enhancement with JavaScript utilities

## External Dependencies

### Core Framework Dependencies
- **Flask**: Python web framework serving as the main application server
- **Flask-CORS**: Cross-origin resource sharing support for API endpoints
- **Werkzeug**: WSGI utilities for secure file handling and request processing

### Machine Learning Stack
- **scikit-learn**: Machine learning library providing Isolation Forest algorithm for anomaly detection
- **pandas**: Data manipulation and analysis library for ML feature engineering
- **numpy**: Numerical computing support for ML operations
- **joblib**: Model serialization and persistence for trained ML models

### Natural Language Processing
- **spaCy**: Advanced NLP library with English language model (`en_core_web_sm`) for text analysis and quality scoring

### AI Integration
- **OpenAI Python SDK**: Integration with GPT models for chatbot functionality and intelligent user assistance

### Frontend Libraries
- **Chart.js**: Data visualization library for rendering interactive charts and graphs in the dashboard
- **Google Fonts**: Inter font family for consistent typography across the application

### Development and Utilities
- **SQLite3**: Embedded database engine for local data persistence without external database server requirements
- **hashlib**: Cryptographic hashing utilities for file integrity verification
- **logging**: Built-in Python logging framework for system monitoring and debugging