## Deploy FastAPI with Docker (Summary)

📁 Project Structure

my_fastapi_app/
 ├── app.py
 ├── requirements.txt
 └── Dockerfile

---

### 🧱 `app.py`
```python
from fastapi import FastAPI
app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello from FastAPI in Docker"}
```

### 📦 `requirements.txt`

```
fastapi
uvicorn
gunicorn
```

### 🐋 `Dockerfile`

```dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["gunicorn", "-w", "4", "-k", "uvicorn.workers.UvicornWorker", "app:app"]
```

### 🔧 Build Docker Image

```dockerfile
docker build -t my-fastapi-app .
```

### 🚀 Run the Container

```dockerfile
docker run -d -p 8000:8000 my-fastapi-app
```

- Visit: `http://localhost:8000`
- You’ll see: `{"message": "Hello from FastAPI in Docker"}`