# PROJECTEDU

PROJECTEDU is a letter-writing website with an AI help desk and an AI writing helper when used with its local server.

The public static website is available at <https://edwinkens13-pixel.github.io/project-edu/>. The root opens the welcome page; choose **Start writing** to open the letter editor.

## Run the website and AI features

The help desk and writing helper use the OpenAI API through the local PowerShell server. An OpenAI API key with API access is required.

1. Open PowerShell in this folder.
2. Enter the key securely and start the server:

   ```powershell
   $secureApiKey = Read-Host "OpenAI API key" -AsSecureString
   $env:OPENAI_API_KEY = (New-Object System.Net.NetworkCredential("", $secureApiKey)).Password
   try {
       .\server.ps1
   } finally {
       Remove-Item Env:OPENAI_API_KEY -ErrorAction SilentlyContinue
   }
   ```

3. Keep that PowerShell window open and visit <http://127.0.0.1:8000/>.
4. Open the letter editor at <http://127.0.0.1:8000/letter.html>, then use **Help & AI chat** or **Polish with AI**.

The public GitHub Pages site hosts static files only; it cannot run the PowerShell AI backend. The AI features work when using the local server above and are not available on the public Pages site. Hosting AI publicly requires deploying the backend separately and configuring the API key as a private server-side secret. Never put an API key in website files or send it in chat.
