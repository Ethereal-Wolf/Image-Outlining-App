**Setting Up and Running the Image Outlining App Locally**

Here’s a detailed guide to get your app running locally on your machine!

---

## Prerequisites
Make sure you have the following installed:
- **Node.js** (for running the React frontend)
- **npm** (comes with Node.js)
- **Python** (for running the Flask backend)
- **pip** (Python package manager)

---

## 1. Clone the Repository
Open a terminal and run:
```bash
git clone <your-repo-url>
cd your-repo-folder
```

Replace `<your-repo-url>` with your actual repository link.

---

## 2. Backend Setup (Flask)

Navigate to the backend folder:
```bash
cd backend
```

Create a virtual environment (optional but recommended):
```bash
python -m venv venv
source venv/bin/activate   # On Windows use: venv\Scripts\activate
```

Install the required packages:
```bash
pip install -r requirements.txt
```

Create an `uploads/` folder (if not already created):
```bash
mkdir uploads
```

Run the Flask app:
```bash
python backend.py
```
By default, the backend will run on `http://localhost:5001`.

---

## 3. Frontend Setup (React)

Navigate to the frontend folder:
```bash
cd ../frontend
```

Install dependencies:
```bash
npm install
```

Start the React development server:
```bash
npm start
```

The app should now open automatically in your browser at `http://localhost:3000`.

---

## 4. Connect Frontend to Backend

In the frontend, ensure the API URL matches your backend server:

In the UI, you can input the backend API URL:
```
http://localhost:5001/api/outline
```

Or, manually update the default URL in your React app code.

---

## 5. Test the App

- Upload an image.
- Adjust the detail level.
- Click **Process Image**.
- Download the outlined image when done!

---

## 6. Troubleshooting

- **Port conflicts:** If ports 3000 or 5001 are in use, change them in your app.
- **CORS errors:** Ensure Flask's `CORS` is enabled (already handled in your code).
- **Backend not reachable:** Double-check the Flask server is running and the URL is correct.

---

That’s it! You now have your app fully running locally. 🚀 Let me know if you’d like me to refine anything or walk you through any step more deeply!


