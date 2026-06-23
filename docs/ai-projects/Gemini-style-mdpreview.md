# Offline Gemini-style Markdown Previewer

Google gemini is a great AI chatbot tool. I interact with the chatbot whenever I have some queries.
I had a issue with the chatbot responses. It was that I had to use the scroller everytime, I wanted to check the previous query in the chat.
To reduce frequent scrolling, I decided to have an offline chat window. I asked gemini to build me one. And I got this one.

I tried a python based markdown previewer

## Pre-requisites

- **Python 3**: `python -m http.server 8000`
- **Python 2**: `python -m SimpleHTTPServer 8000`

Then open your browser and go to `http://localhost:8000`.

## Troubleshooting

### 1. Check Python's Terminal Output (The Clue)

Look at the terminal window where you ran `python -m http.server 8000`. Every time you refresh your browser, Python logs the requests.

Refresh your page and look at the last few lines in that terminal:

* **If you see `GET /chat.md HTTP/1.1" 404 -`:** This means Python is working perfectly, but it **cannot find** a file named `chat.md` in the folder it is currently serving.
* **If you see `GET /chat.md HTTP/1.1" 200 -`:** This means Python *successfully* sent the file to your browser, meaning the issue is inside your JavaScript code or browser cache.

### 2. Verify Your "Terminal Path"

Python only serves the folder your terminal was pointing to *at the exact moment* you ran the command.

If you opened your terminal, and immediately typed `python -m http.server 8000` without navigating to your project folder first, Python is likely serving your computer's user profile folder instead of your project folder.

**The Fix:**

1. Stop the server in your terminal by pressing `Ctrl + C`.
2. Navigate to your project folder. For example:
```bash
cd path/to/your/project-folder

```
3. Restart the server:
```bash
python -m http.server 8000

```

### 3. The Hidden `.txt` Extension (Most Common)

If Python is giving you a `404` error and you are positive you are in the right folder, your operating system has likely hidden the true extension of your file.

If you created `chat.md` using Notepad (Windows) or TextEdit (Mac), the file is likely actually named **`chat.md.txt`**, but the system is hiding the `.txt` from your eyes. Because your code looks for `./chat.md`, it fails.

**The Fix:**

* **Windows:** In File Explorer, click the **View** tab at the top and check **File name extensions**. If it says `chat.md.txt`, rename it to delete the `.txt`.
* **Mac:** Right-click the file, select **Get Info**, and look under **Name & Extension**. Remove `.txt` if it's there.

---

### How to see the exact error code

To know for sure what's failing, right-click your blank webpage, click **Inspect**, and open the **Console** tab.

* Do you see a red error message there?
* If you click the **Network** tab in that inspector and refresh, does `chat.md` show up in red with a `404` status?

Let me know what your browser console or your Python terminal says, and we'll pinpoint it!

# yes, it showing it as error, but the chat.md file is being downloaded everytime

Ah, that is a massive clue! If the `chat.md` file is actively **downloading** to your computer every time the page loads instead of displaying on the screen, your local server setup is working perfectly.

The issue is how the Python server is telling your browser to handle the file.

By default, some versions of Python's `http.server` send `.md` files with a header that tells the browser: *"Hey, this is a random binary file, don't read it, just download it!"* Because the browser forces a download, JavaScript's `fetch()` function gets blocked or receives empty data, throwing that console error.

Here are the two easiest ways to fix this immediately:

---

### Fix 1: Change the File Extension to `.txt` (Easiest)

Browsers and Python *always* know how to handle `.txt` files properly without forcing a download.

1. Rename your markdown file from `chat.md` to **`chat.txt`**. (Keep all the markdown content inside it exactly the same!)
2. In your `index.html` file, update the file path line at the top of your script to look for the text file:
```javascript
const filePath = './chat.txt'; 

```


3. Save the HTML file and refresh your browser. It will stop downloading and display perfectly.

---

### Fix 2: Tell Python to Map `.md` Files Correctly

If you strictly want to keep the `.md` extension, you can tell Python to serve `.md` files as plain text instead of downloadable attachments.

Instead of running the standard command, create a tiny script to launch your server.

1. Create a file named `server.py` in your project folder.
2. Paste this code into it:
```python
import http.server
import socketserver

# Tell the server to treat .md files as plain text
handler = http.server.SimpleHTTPRequestHandler
handler.extensions_map.update({
    '.md': 'text/plain',
})

PORT = 8000
with socketserver.TCPServer(("", PORT), handler) as httpd:
    print(file=f"Server started at http://localhost:{PORT}")
    httpd.serve_forever()

```


3. Run this file in your terminal instead:
```bash
python server.py

```



Go with **Fix 1** if you want a 5-second fix, or **Fix 2** if keeping the `.md` extension is important for your workflow. Which route do you prefer?
