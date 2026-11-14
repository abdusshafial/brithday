HAPPY BIRTHDAY WEBSITE ? FLASK EDITION

This project is a Flask web app. The original HTML/CSS/JavaScript and all photo assets are kept in this folder.

RUN LOCALLY

1. Open a terminal in this folder.
2. Create and activate a virtual environment (optional but recommended):
   Windows:  py -m venv .venv
             .venv\Scripts\Activate.ps1
   macOS/Linux: python3 -m venv .venv
                source .venv/bin/activate
3. Install dependencies:
   pip install -r requirements.txt
4. Start the app:
   python app.py
5. Open http://127.0.0.1:5000 in your browser.

DEPLOY TO PYTHONANYWHERE

1. Upload this entire folder (including app.py, requirements.txt, index.html, and assets/) to your PythonAnywhere account. For example, use:
   /home/yourusername/happy_birthday_website
2. In a PythonAnywhere Bash console, create a virtual environment using the Python version you plan to select for the web app, then install Flask:
   cd /home/yourusername/happy_birthday_website
   mkvirtualenv --python=/usr/bin/python3.13 birthday
   workon birthday
   pip install -r requirements.txt
   If you choose a different Python version in the Web tab, use its matching /usr/bin/pythonX.Y path instead.
3. Open the Web tab, create a Manual configuration web app, and select the same Python version used for the virtual environment.
4. Set the virtualenv path to:
   /home/yourusername/.virtualenvs/birthday
5. Open the WSGI configuration file linked from the Web tab. Replace its contents with the following, changing the username and project path:

   import sys
   project_home = '/home/yourusername/happy_birthday_website'
   if project_home not in sys.path:
       sys.path.insert(0, project_home)
   from app import app as application

6. Save the WSGI file and click Reload on the Web tab.
7. Open your PythonAnywhere site. The app serves index.html at / and photos from /assets/.

The app does not need a database. The birthday melody and animations run in the visitor's browser. Browser audio starts after the visitor clicks Start Here.
