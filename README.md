
# 🏥 Doctor Appointment System — LangChain × LangGraph × FastAPI

A powerful conversational AI system that allows users to manage doctor appointments using **natural language**. Users can book, cancel, or reschedule appointments and check availability of doctors or specialists seamlessly. Powered by **LangChain**, **LangGraph**, **OpenAI**, and served using **FastAPI**.

---

## 🚀 Tech Stack

| Tool           | Purpose                                              |
|----------------|------------------------------------------------------|
| 🧠 LangChain   | For building the LLM-based agentic system            |
| 🔄 LangGraph   | For defining stateful, multi-step workflows          |
| 💬 OpenAI LLM  | To extract and understand user intent                |
| ⚙️ FastAPI      | For building the web API backend                    |
| 🖥️ Uvicorn      | ASGI web server to host FastAPI                     |
| 📊 Pandas      | For reading/updating doctor availability (CSV data) |
| 🔐 Pydantic    | For input validation and structured outputs          |

---

## 🎯 Features

✅ Book a session with a doctor  
✅ Cancel an existing session  
✅ Reschedule appointments  
✅ Check availability of a specific doctor or specialization  
✅ Understands flexible and conversational input  
✅ Tracks session bookings and availability through CSV updates  

---

## 🧠 How It Works

### Workflow Graph

This system is powered by **LangGraph**. Here’s a simplified version of the flow:

```mermaid
graph TD
  Start[Supervisor Node]
  Start --> |intent: information| InfoNode
  Start --> |intent: booking| BookingNode

  InfoNode --> |query: specialization/doctor| CheckerNode

  BookingNode --> |set| SetSessionNode
  BookingNode --> |cancel| CancelSessionNode
  BookingNode --> |reschedule| RescheduleNode
````

---

## 📁 Folder Structure

```
📁 Doctor_Appointment_System/
├── main.py                      # FastAPI entry point
├── Workflow.py                  # LangGraph workflow logic
├── ToolManager.py               # Tool functions (booking, cancelling, etc.)
├── Prompts/
│   └── system_prompts.py        # Prompt templates
├── data/
│   └── doctor_availability.csv  # Availability and bookings
├── requirements.txt             # Project dependencies
└── README.md                    # You are here!
```

---

## 🧪 Sample Inputs (Test Scenarios)

Here are various types of questions the system understands and responds to:

### 🟢 Booking a Session

```python
question = "I want to set session with doctor john doe on 09-08-2024 13:00"
inputs = {"question": question, "user_id": 1000041.0}
```

### 🔴 Cancelling a Session

```python
question = "I want to cancel session with doctor john doe on 09-08-2024 13:00"
inputs = {"question": question, "user_id": 1000041.0}
```

### 🔄 Rescheduling a Session

```python
question = "I want to reschedule session with doctor john doe on 09-08-2024 13:00 which was held on 08-08-2024 12:30"
inputs = {"question": question, "user_id": 1000041.0}
```

### ❓ Checking Doctor Availability

```python
question = "Is Dr. Jane Smith available on 10-08-2024?"
inputs = {"question": question}
```

### ❓ Checking Specialist Availability

```python
question = "Are any pediatric dentists available on 11-08-2024?"
inputs = {"question": question}
```

---

## 🗃️ Sample doctor\_availability.csv

| doctor\_name | specialization     | date\_slot       | is\_available | patient\_to\_attend |
| ------------ | ------------------ | ---------------- | ------------- | ------------------- |
| john doe     | general\_dentist   | 09-08-2024 13:00 | True          |                     |
| jane smith   | pediatric\_dentist | 10-08-2024 11:00 | True          |                     |

> This file is read and updated during each booking/cancellation/rescheduling.

---

## ⚙️ Setup & Installation

1. **Clone the repository**

```bash
git clone https://github.com/<your-username>/Doctor_Appointment_System.git
cd Doctor_Appointment_System
```

2. **Create a virtual environment**

```bash
python -m venv venv
source venv/bin/activate  # or .\venv\Scripts\activate for Windows
```

3. **Install required dependencies**

```bash
pip install -r requirements.txt
```

4. **Run the FastAPI app**

```bash
uvicorn main:app --reload
```

---

## 🔗 API Endpoint

Once the server is running, go to:
👉 [http://localhost:8000/docs](http://localhost:8000/docs)
Use Swagger UI to test the `/predict` endpoint with inputs like:

```json
{
  "question": "I want to cancel session with doctor john doe on 09-08-2024 13:00",
  "user_id": 1000041.0
}
```

---

## 📸 Screenshots (Optional)

* Screenshot of Swagger UI `/docs`
* LangGraph workflow visualization
* Appointment booking or rescheduling response JSON
* LangChain + LangGraph logo fusion (if needed)

---

## 🧩 Future Improvements

* ✅ Add proper database (PostgreSQL or MongoDB)
* 🔐 User login & patient history tracking
* 📱 Streamlit or React-based frontend
* 📧 Email/SMS reminders (via Twilio)
* 📊 Admin dashboard for appointment tracking

---

## 🙌 Acknowledgements

* [LangChain](https://www.langchain.com/)
* [LangGraph](https://docs.langchain.com/langgraph/)
* [OpenAI](https://openai.com/)
* [FastAPI](https://fastapi.tiangolo.com/)
* Built with ❤️ by **Abhay**, an aspiring GenAI Engineer

---

> "Let doctors treat patients, and AI handle the appointments."
> — *Doctor Appointment System, Powered by LLMs*

```

---

All done 💡 Let me know if you'd like help publishing this on GitHub or writing a killer LinkedIn post for it 🔥
```
