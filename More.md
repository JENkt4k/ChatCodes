```python
import google.auth
from googleapiclient.discovery import build
from googleapiclient.errors import HttpError

# Authenticate with the Google Drive API
credentials, _ = google.auth.default()
service = build('drive', 'v3', credentials=credentials)

# Retrieve the file from Google Drive
file_id = 'YOUR_FILE_ID'
try:
    file = service.files().get(fileId=file_id).execute()
    file_name = file['name']
    print(f'File name: {file_name}')
except HttpError as error:
    print(f'An error occurred: {error}')

# Download the file
request = service.files().get_media(fileId=file_id)
content = request.execute()

# Convert the binary content to a text string
text = content.decode('utf-8')

# Do something with the text string
print(text)
```
