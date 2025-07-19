# Student-Project-Tracker Web APP
A simple FastAPI web application for registering students and tracking their weekly progress during the Cloud Native Series.

### Key Features:
- Register new students (generates a unique ID).
- Track weekly progress for each student.
- All students use one central MongoDB (hosted on MongoDB Atlas or similar).
- Simple endpoints for registration, status check, and progress update.

## 📦 Prerequisites
- Python 3.10+
- Git
- MongoDB Atlas account (to get your connection string)

---

## 💻 Local Development Setup

### 1. Clone the Repository
```bash
git clone To https://github.com/MaryBamisile/My-students-projects-tracker.git
cd student-project-tracker
```

### 2. Create Virtual Environment & Install Dependencies
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install -r requirements.txt
```

### 3.Db Conenctions
- navigate to app/main and update vault ip :

```
export VAULT_ADDR=http://YourvaultVMIP:8200
export VAULT_ROLE_ID=**********************
export VAULT_SECRET_ID=********************
```

### 4. Run the Application Locally
```bash
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```
Visit `http://vmip:8000` to see your app in action.

---

## 🐳 Docker Instructions

### 1. Build Docker Image
```bash
docker build -t student-tracker .
```

### 2. Run Docker Container
```bash
docker run --env-file .env -p 8000:8000 student-tracker
```

### 3. Push to Docker Hub
Ensure you're logged in:
```bash
docker login
```
Tag and push your image:
```bash
docker tag student-tracker your-dockerhub-username/student-tracker

docker push your-dockerhub-username/student-tracker
```

---

## 📬 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/register?name=YourName` | Register new student |
| GET    | `/status/{student_id}`    | View registration and progress |
| POST   | `/update/{student_id}?week=week1` | Update progress by week |

---

### GitHub Actions deployment
- Write your cicd workflow using github action that deploys this app to your VM. 
- Go to GitHub → Settings → Secrets and Variables → Actions and add all the secrets declared in the ci-cd workflow
- Ensure your VM is ready.

   ```
  # On your VM, ensure docker is installed. Otherwise, run the following:
   sudo apt update
   sudo apt install -y docker.io
   sudo systemctl enable --now docker
   sudo usermod -aG docker $USER
   ```
- Feel free to update the Readme with anything and commit to trigger your cicd or test deployment
- Check successfull deployment (Go to the Actions tab). If pipeline runs successfully, uour app should be functional via: http://yourVMIP:port

## My working app:

<img width="757" height="400" alt="image" src="https://github.com/user-attachments/assets/3a9ea264-88a1-4d13-8ac9-90efe98f2e78" />

## My GitHub Actions deployment:

<img width="1434" height="359" alt="image" src="https://github.com/user-attachments/assets/63cef6d7-c737-4133-b70a-c5a57320d732" />

## My VS code workings:

<img width="1132" height="513" alt="image" src="https://github.com/user-attachments/assets/1e63b8c8-ee03-418d-9e74-0f8bb1314c0d" />

## My docker image:

<img width="722" height="59" alt="image" src="https://github.com/user-attachments/assets/8551ec35-bb15-46e7-bc2e-f4958e423a35" />


Note: Ensure your port is added to the Network security group of the VM.

---

## 👩🏽‍💻 Built for the Cloud Native Series 
This project is used for learning cloud-native tools and Handson-Project.

Feel free to fork and extend it!
