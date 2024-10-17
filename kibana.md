# 🚀 Curl Automate Logs Creation Process

Automate the logs creation process using Curl. This script performs a POST request with a payload, retrieves the output, and opens Notepad with the output on a Windows machine.

## 🎯 Objective
- Streamline the process of creating and viewing logs.

## 🔑 Key Results
- Efficiently send POST requests with payloads.
- Automatically retrieve and display the output.
- Open the output in Notepad on Windows for easy viewing.

## 🛠️ Sample Code

Here's a sample script to automate the logs creation process using Curl and PowerShell:

```powershell
# Define the URL and payload
$url = "https://example.com/api/logs"
$payload = @{
    "key1" = "value1"
    "key2" = "value2"
} | ConvertTo-Json

# Perform the POST request and retrieve the output
$response = Invoke-RestMethod -Uri $url -Method Post -Body $payload -ContentType "application/json"

# Save the output to a file
$outputFile = "C:\path\to\output.log"
$response | Out-File -FilePath $outputFile

# Open the output in Notepad
Start-Process notepad.exe $outputFile
```

This script sends a POST request to the specified URL with a JSON payload, saves the response to a log file, and opens the log file in Notepad.