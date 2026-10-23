Orbit Assistant
Orbit Assistant is a lightweight Windows desktop AI assistant. It stays available above other windows, keeps conversations on the device, can analyze images and documents, and can perform a small set of guarded desktop actions when you ask.
Status: Orbit is an independent desktop application. It is not affiliated with OpenAI, Microsoft, or the Ollama project. An AI provider account or locally running model is needed for AI chat.
Contents
·	Highlights
·	Requirements
·	Install and start
·	Set up an AI provider
·	Use Orbit
·	Attach images and documents
·	Chat history and saved data
·	Appearance and window controls
·	Desktop actions
·	Privacy and provider usage
·	Troubleshooting
·	Build from source
·	Project layout
Highlights
·	Floating, resizable desktop window with a global Ctrl+Shift+Space show/hide shortcut.
·	OpenAI-compatible chat provider support and local Ollama support.
·	Conversation history, chat switching, and starting a new conversation.
·	Image understanding and text extraction from common document formats.
·	Light, dark, and Windows system-preference themes.
·	A limited set of desktop tools, with checks before tool actions run.
·	A few local slash commands that work without an AI provider.
Requirements
·	Windows on an x64 PC.
·	For the prebuilt self-contained release, no separate .NET installation is needed.
·	For AI chat, either an OpenAI API key or a working local Ollama installation and model is needed.
·	Internet access is needed for OpenAI and web search. Ollama can run locally; model downloads require internet access.
Install and start
1.	Download the complete Orbit Assistant ZIP from the project’s GitHub Releases page.
2.	Extract the ZIP to a folder you can write to, such as your user Downloads or Documents folder.
3.	Run OrbitAssistant.exe from the extracted folder.
4.	If Windows shows a security prompt, verify that you downloaded the release from the project you trust before choosing to run it.
5.	Open Settings using the gear button to configure a provider before sending an AI prompt.
Keep the extracted files together. The executable depends on files shipped alongside it.
Set up an AI provider
Open Settings from Orbit’s gear button, select a provider, fill in its fields, then click Save.
OpenAI API
1.	Select OpenAI API.
2.	Enter an OpenAI API key.
3.	Enter a model available to your API account. The initial model value is gpt-6-luna; change it if that model is not enabled for your account.
4.	Save the settings and send a message.
Orbit sends requests to https://api.openai.com/v1/chat/completions. API usage is billed by OpenAI according to your account and model. A ChatGPT subscription and OpenAI API billing are separate.
Ollama (local)
1.	Install and start Ollama.
2.	Download a model in Ollama that supports chat.
3.	Select Ollama (local) in Orbit Settings.
4.	Set the endpoint to your Ollama OpenAI-compatible chat completions endpoint. The default is http://localhost:11434/v1/chat/completions.
5.	Set the model name to an installed model (the initial value is qwen2.5:7b), then save.
The model name must match a model available in your Ollama installation. Image analysis requires a vision-capable model. Ollama runs locally on your computer, but its models may need to be downloaded first.
Use Orbit
·	Type a question or instruction in the message box and press Enter or click Send. Use Shift+Enter for a new line.
·	Click the new-chat button to start a conversation.
·	Open the chat-history control to revisit a previous conversation and continue it.
·	Click the paperclip to attach files. See Attach images and documents for formats and limits.
·	Click the gear to open provider and theme settings.
·	Use Ctrl+Shift+Space to show or hide Orbit. Clicking outside the window hides it automatically.
·	Use the window’s minimize control to minimize it, or its close control to close it.
·	Drag the bottom-right resize grip to resize the main window. The Settings window can also be resized.
Local slash commands
These commands are handled on the computer and do not require a configured AI provider:
Command	What it does
/help	Shows available local commands.
/open edge	Opens Microsoft Edge. Other supported app names are listed under Desktop actions.
/find filename	Searches supported folders for matching file names.
/system	Shows basic Windows and device information.
/web search terms	Opens a Google search in the default browser.

Attach images and documents
Click the paperclip, select one or more files, and send your prompt. You can ask Orbit to describe an image, summarize a document, or answer a question about the attached content.
Supported image types: .png, .jpg, .jpeg, .webp
Supported document/text types: .txt, .md, .csv, .json, .log, .xml, .html, .htm, .docx, .pdf
Limits per message:
·	Up to 10 files.
·	Up to 20 MB total, with a 12 MB maximum for one file.
·	Extracted document text is limited to 200,000 characters in total.
·	PDF text extraction reads up to the first 100 pages.
Orbit extracts text from PDFs; scanned pages and images embedded in PDFs are not OCR-processed. Attach an image file separately if you want it analyzed. Image analysis depends on the selected provider and model supporting vision. With Ollama, use a vision-capable model.
Chat history and saved data
Orbit saves settings and chat history under your Windows local application data folder:
%LOCALAPPDATA%\OrbitAssistant\

·	settings.json stores settings. The OpenAI key is protected with Windows DPAPI for the current Windows user.
·	chats.json stores conversations so you can reopen them and continue later.
·	Attached image data and extracted document text are retained in the corresponding local conversation history.
Removing the application folder does not necessarily remove these files. To clear saved settings and conversations, close Orbit and remove the OrbitAssistant folder under %LOCALAPPDATA%. This permanently deletes local history and settings.
Appearance and window controls
In Settings → Theme, choose one of:
·	System Preference — follows the Windows app theme (light or dark).
·	Dark Mode — uses Orbit’s dark appearance.
·	Light Mode — uses Orbit’s light appearance.
Orbit is a floating window. It can be resized using the bottom-right grip, minimized with the minimize button, hidden by clicking outside it, or shown and hidden with Ctrl+Shift+Space. Settings has its own resizable window.
Desktop actions
When a request clearly asks Orbit to perform a supported action, the assistant may use its desktop tools. Orbit currently supports opening Edge, Chrome, Notepad, Calculator, File Explorer, Windows Settings, and Paint; searching file names in the Desktop, Documents, and Downloads folders; opening files from those folders; saving notes under Documents\Orbit Assistant\Notes; showing basic system information; and opening a Google search in the default browser.
Orbit limits file search to names in those folders (up to five directory levels and 20 results). Opening an existing file is restricted to those same folders. These tools do not run arbitrary shell commands, delete files, or make unrestricted changes to the computer. File attachments are a separate way to provide content for analysis.
Privacy and provider usage
·	Conversation history and settings are stored locally under %LOCALAPPDATA%\OrbitAssistant.
·	When you send a message, its text and any attached image or extracted document content are sent to the provider selected in Settings. Review that provider’s data and privacy terms before sending sensitive information.
·	OpenAI requests use your API key and may incur API charges. Ollama requests go to the endpoint configured in Settings, which defaults to the local computer.
·	/open, /find, and /system are local commands. /web opens a search page in your browser and sends the search terms to Google.
Troubleshooting
Orbit does not open
·	Extract the full ZIP before launching; do not run the executable from inside the ZIP preview.
·	Keep the extracted files together and try launching OrbitAssistant.exe again.
·	If Windows blocked the download, use the file’s Windows security properties to review its blocked status, then launch only if you trust the source.
The assistant cannot reach the provider
·	Open Settings and check the selected provider, model name, API key, and endpoint.
·	For OpenAI, confirm that the key is valid, the model is available to the API account, and network access is working.
·	For Ollama, confirm Ollama is running, the endpoint is reachable, and the configured model has been downloaded.
·	Read the error displayed in the chat; provider errors are returned there when available.
Image analysis does not work
·	Use a supported image extension and remain within the file size limits.
·	Choose a vision-capable model. Not every chat model can process images.
·	For Ollama, verify the installed model supports vision.
A document has missing or unreadable content
·	PDF extraction does not OCR scanned pages and is limited to the first 100 pages.
·	Check that the file is one of the supported types and that the combined extracted text stays below the limit.
·	If a PDF is a scan, use an OCR tool to create a searchable PDF or attach its pages as supported image files.
The shortcut or click-outside hide behavior is not working
·	Make sure Orbit is running and try Ctrl+Shift+Space again.
·	If another application uses the same global shortcut, close or reconfigure that application and retry.
·	Click Orbit’s minimize control to hide it from the desktop while troubleshooting.
Build from source
Prerequisites
·	Windows x64.
·	.NET 9 SDK.
·	Internet access for restoring NuGet packages.
From the OrbitAssistant project directory, run:
dotnet restore .\OrbitAssistant.csproj
dotnet build .\OrbitAssistant.csproj -c Release
dotnet publish .\OrbitAssistant.csproj -c Release -r win-x64 --self-contained true -o .\publish

The publish folder contains the runnable Windows application and its dependencies. Zip the contents of that folder to create a portable release archive. This project uses Windows desktop/WPF APIs and is intended to run on Windows.
Project layout
OrbitAssistant/
├── OrbitAssistant.csproj
├── App.xaml
├── MainWindow.xaml
├── SettingsWindow.xaml
├── Services/
├── Models/
└── README.md

The project README describes the source package. This document is a standalone getting-started and user guide for the application.
