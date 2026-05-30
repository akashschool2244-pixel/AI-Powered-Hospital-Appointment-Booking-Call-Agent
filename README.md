# AI Voice Agent for Hospital Appointment Booking

An AI-powered hospital receptionist that can answer patient phone calls, hold natural conversations, understand appointment requests, and automatically book appointments with available doctors.

The system combines conversational AI, speech processing, telephony, and healthcare workflow automation into a single platform.

---

### Example Conversation

**Patient:** "I have a heart problem and would like to see a doctor tomorrow."

**AI Receptionist:** "I can help with that. Dr. Sharma, our cardiologist, is available tomorrow at 10:00 AM and 2:00 PM. Which slot would you prefer?"

**Patient:** "10 AM works."

**AI Receptionist:** "Great. May I have your name and phone number to confirm the appointment?"

---

## Features

### AI Receptionist

* Answers incoming patient calls
* Holds natural multi-turn conversations
* Understands symptoms and appointment requests
* Maps symptoms to medical specialties
* Requests clarification when uncertain
* Suggests the closest available appointment slot
* Collects patient information
* Confirms booking details before scheduling
* Prevents double-bookings through atomic database transactions

### Hospital Admin Dashboard

* Add and manage doctors
* Configure medical specialties
* Create and manage appointment slots
* View all appointments
* View patient information
* Monitor doctor availability

---

## System Architecture

```text
Patient Call
     │
     ▼
 Twilio (Telephony)
     │
     ▼
 Deepgram (Speech-to-Text)
     │
     ▼
 Gemini (LLM Reasoning)
     │
     ▼
 ElevenLabs (Text-to-Speech)
     │
     ▼
 Patient Response

           │
           ▼

  Hospital Database
           ▲
           │

 Admin Dashboard
```


```md
![Architecture](images/arch.png)
```

---

## Tech Stack

### Backend

* FastAPI
* SQLAlchemy
* PostgreSQL
* Pydantic

### AI & Voice

* Google Gemini
* Deepgram
* ElevenLabs
* Twilio

### Frontend

* React
* Vite
* Tailwind CSS

---

## Key Technical Highlights

### Intelligent Specialty Detection

Patients do not need to know medical terminology.

Example:

```text
"Heart problem" → Cardiology
"Breathing issue" → Pulmonology
"Skin rash" → Dermatology
```

The AI performs semantic matching against specialties available in the database.

---

### Multi-Turn Conversation Management

The receptionist maintains context throughout the conversation and guides the patient through:

1. Understanding medical needs
2. Selecting a doctor
3. Choosing an appointment slot
4. Collecting patient information
5. Confirming the booking

---

### Safe Concurrent Booking

The system prevents double-booking even under concurrent requests using:

* Database transactions
* Row-level locking (`SELECT FOR UPDATE`)
* Unique constraints on appointment slots

This ensures that only one patient can reserve a slot.

---

## Project Structure

```text
hospital-ai/
├── main.py
├── database.py
├── models.py
├── schemas.py
├── crud.py
├── ai_engine.py
├── conversation.py
├── routes/
│   ├── doctors.py
│   ├── slots.py
│   ├── patients.py
│   ├── chat.py
│   └── twilio_voice.py
├── requirements.txt
├── .env
└── frontend/
```

---



## Future Improvements

* Multi-language support
* SMS appointment reminders
* Appointment cancellation and rescheduling
* Doctor portal
* Analytics dashboard
* Hospital FAQ support using RAG
* Voice authentication
* Calendar integration

---

## Screenshots



### Doctor Management

![Doctors](Screenshot%202026-05-30%20114009.png)

### Slot Management



### Appointment Dashboard


![Appointments](Screenshot%202026-05-30%20114036.png)

---

## Author

Akash

Built as a real-world conversational AI system combining telephony, speech processing, large language models, and healthcare workflow automation.
