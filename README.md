ClaimSure AI
An AI-powered healthcare claims and medical coding assistance
platform
ClaimSure AI is a role-based web application designed to help doctors,
patients, and medical coders work with healthcare documentation and
insurance-claim workflows. It combines document question answering with
retrieval-augmented generation (RAG) to help users find relevant
information in uploaded medical documents.
> **Important:** ClaimSure AI is an assistance tool, not a substitute
> for a qualified medical coder, clinician, insurer, or official coding
> reference. All suggested codes, eligibility information, and claim
> forms must be reviewed and verified by an authorized professional
> before use.
Key Features
Role-based access: Separate experiences for Doctors, Patients,
and Medical Coders.
Doctor workspace: Explore possible disease and procedure codes
from clinical summaries or entered details, and assist with
preparing an insurance claim form such as the CMS-1500 where
applicable.
Patient workspace: Submit claim information and ask questions
about uploaded medical or claim documents.
Medical coder workspace: Review uploaded hospital summaries and
doctor forms, investigate possible codes, and assess insurance
eligibility against policy details supplied by the user.
Document Q&A with RAG: Upload supported PDF or DOC/DOCX
documents and ask questions grounded in their contents.
Chat history: Keep conversations organized so users can return
to earlier questions.
Profile management: Maintain account and role information.
LLM-assisted responses: Use a configured language model to
explain retrieved information in accessible language.
User Roles
Doctor
Enter a disease, procedure, or clinical summary.
Review AI-suggested medical codes and supporting context.
Ask questions about uploaded documentation.
Use assistance for preparing claim-form information.
Patient
Submit claim details through the portal.
Upload supported documents and ask questions about their contents.
Get plain-language explanations of claim-related information.
Medical Coder
Upload hospital summaries or doctor-provided forms.
Review candidate disease and procedure codes.
Compare claim details with supplied insurance policy information.
Ask document-grounded questions through the RAG chatbot.
How It Works
The user signs in and enters the workspace for their role.
The user enters a question or uploads a supported document.
The backend extracts text from the document and splits it into
manageable chunks.
The application creates embeddings and retrieves relevant chunks
from a vector store.
The retrieved context is passed to the configured language model
along with the user's question.
The application returns an answer based on the available context,
with appropriate limitations and review reminders.
``` text
User
  |
  v
Web Frontend
  |
  v
Backend API ---- Authentication / Role Checks
  |
  +---- Document Upload and Text Extraction
  |
  +---- Chunking and Embeddings
  |            |
  |            v
  |       Vector Store (e.g., FAISS)
  |            |
  +<--- Relevant Retrieved Context
  |
  v
Configured LLM
  |
  v
Grounded Response to User
```
Technology Stack
The exact stack depends on the current implementation and configuration.
The intended architecture may include:
---
Layer                               Technology
---
Frontend                            React with Vite
Backend API                         Python with FastAPI
LLM orchestration                   LangChain or equivalent
Retrieval-augmented generation      Embeddings, document chunking,
retrieval
Vector search                       FAISS or another configured vector
store
Language model                      Configured provider/model via
environment variables
Document support                    PDF and DOC/DOCX text extraction
Data storage                        Database selected by the project
configuration
Only list technologies here that are actually installed and configured
in your repository. Replace example components with the exact tools used
by your implementation.
Getting Started
The following is a general setup outline. Adjust commands and
environment variables to match the repository.
Prerequisites
Python 3.10 or later (use the version supported by your
dependencies)
Node.js and npm
Git
API key for the LLM provider, if your configured model requires one
1. Clone the repository
``` bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_PROJECT_FOLDER>
```
2. Set up the backend
``` bash
python -m venv .venv
```
Activate the environment:
Windows PowerShell
``` powershell
.\.venv\Scripts\Activate.ps1
```
macOS/Linux
``` bash
source .venv/bin/activate
```
Install backend dependencies if a `requirements.txt` file is present:
``` bash
pip install -r requirements.txt
```
Create a `.env` file using the variable names expected by your
application. For example:
``` env
LLM_API_KEY=your_api_key_here
```
Use the actual variable name required by your selected provider. Never
commit real API keys, passwords, tokens, or patient information to Git.
Start the FastAPI server using the entry point in your repository. For
example, if the application instance is `app` in `main.py`:
``` bash
uvicorn main:app --reload
```
The API may be available at `http://127.0.0.1:8000`. FastAPI's
interactive documentation is commonly available at
`http://127.0.0.1:8000/docs`.
3. Set up the frontend
Open a second terminal and navigate to the frontend directory (for
example, `frontend`):
``` bash
cd frontend
npm install
npm run dev
```
Use the local URL printed by Vite in the terminal. Your frontend may
require an environment variable for the backend API URL; configure it
according to the project code.
Environment Variables
Create a local `.env` file and use only the variable names supported by
your implementation.
Variable         Purpose
---
`LLM_API_KEY`    Example placeholder for the language-model API key
`DATABASE_URL`   Optional database connection string, if used
`BACKEND_URL`    Optional frontend/backend URL configuration, if used
Do not place actual secrets in this README or commit the `.env` file.
Add `.env` to `.gitignore`.
Example Workflow
Sign in as a Doctor, Patient, or Medical Coder.
Open the relevant workspace.
Upload a supported document or enter a question.
Review the response and the document context used.
Verify any suggested code or claim decision using authoritative
sources and the relevant insurer's rules.
Responsible Use, Privacy, and Security
Medical records and insurance documents contain sensitive information. A
production deployment should include:
Secure authentication and server-side role-based authorization.
Encryption in transit and appropriate protection at rest.
Access controls that prevent one user from viewing another user's
documents or chats.
File type and size validation, safe document processing, and upload
limits.
Secrets managed outside source control.
Logging that avoids exposing medical details, credentials, or other
sensitive data.
Clear retention and deletion policies for uploaded documents and
chat history.
Human review of medical codes, claim forms, and eligibility
interpretations.
Compliance review for applicable healthcare privacy and
data-protection requirements before real patient data is used.
Do not use unverified AI output as the sole basis for medical treatment,
billing, or insurance decisions.
Current Limitations
Accuracy depends on the quality of uploaded documents, retrieval,
the language model, and the reference data available to the
application.
Insurance eligibility cannot be confirmed unless reliable policy and
payer information is available and the applicable rules are checked.
AI-generated codes and claim-form content are suggestions and
require professional validation.
Supported file formats and model providers depend on the actual
implementation.
This README describes the intended architecture; verify the
repository's current endpoints, environment variables, and commands
before deployment.
Roadmap
Potential future improvements: - Show source excerpts for
document-grounded answers. - Add code validation against approved,
up-to-date coding references. - Add structured claim-form validation
before export. - Improve audit trails and document lifecycle controls. -
Add automated tests for role permissions, document parsing, retrieval,
and API endpoints. - Add deployment instructions and monitoring.
Contributing
Create a branch for your change.
Make focused changes and add or update tests.
Run the project's tests and lint checks.
Open a pull request with a clear description of the change.
License
Add the license that applies to this repository. Until a license is
specified, do not assume that the project is open source or grant
permission to reuse it.
