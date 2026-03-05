# AI Code Vulnerability Examples (Defensive)

Real-world vulnerability patterns commonly produced by AI code generation tools. Use these for code review training and SAST rule validation.

---

## SQL Injection

### Vulnerable
```python
# User input concatenated directly into query
def get_user(username):
    query = "SELECT * FROM users WHERE username = '" + username + "'"
    cursor.execute(query)
    return cursor.fetchone()
```
**Attack input:** `' OR '1'='1` → returns all users

### Safe
```python
def get_user(username):
    cursor.execute("SELECT * FROM users WHERE username = ?", (username,))
    return cursor.fetchone()
```

---

## Command Injection

### Vulnerable
```python
import os

def ping_host(hostname):
    os.system(f"ping -c 1 {hostname}")
```
**Attack input:** `8.8.8.8; rm -rf /tmp/data`

### Safe
```python
import subprocess

def ping_host(hostname):
    subprocess.run(["ping", "-c", "1", hostname], capture_output=True, timeout=5)
```

---

## Hardcoded Credentials

### Vulnerable
```python
import openai

client = openai.OpenAI(api_key="sk-proj-abc123secretkey...")
```

### Safe
```python
import os
import openai

client = openai.OpenAI(api_key=os.environ["OPENAI_API_KEY"])
```

---

## Path Traversal

### Vulnerable
```python
def read_file(filename):
    with open(f"/app/uploads/{filename}") as f:
        return f.read()
```
**Attack input:** `../../etc/passwd`

### Safe
```python
import os

UPLOAD_DIR = "/app/uploads"

def read_file(filename):
    safe_path = os.path.realpath(os.path.join(UPLOAD_DIR, filename))
    if not safe_path.startswith(UPLOAD_DIR):
        raise ValueError("Invalid file path")
    with open(safe_path) as f:
        return f.read()
```

---

## Weak Password Hashing

### Vulnerable
```python
import hashlib

def hash_password(password):
    return hashlib.md5(password.encode()).hexdigest()
```
MD5 is fast and reversible via rainbow tables.

### Safe
```python
import bcrypt

def hash_password(password):
    return bcrypt.hashpw(password.encode(), bcrypt.gensalt())

def verify_password(password, hashed):
    return bcrypt.checkpw(password.encode(), hashed)
```

---

## Insecure Deserialization

### Vulnerable
```python
import pickle

def load_session(data):
    return pickle.loads(data)  # data from user request
```
Arbitrary code execution possible with crafted pickle payload.

### Safe
```python
import json

def load_session(data):
    return json.loads(data)  # only deserialize known-safe formats
```

---

## Missing Authentication on API Endpoint

### Vulnerable
```python
@app.route("/api/admin/users")
def list_users():
    return jsonify(db.get_all_users())
```

### Safe
```python
from functools import wraps

def require_admin(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        if not current_user.is_authenticated or not current_user.is_admin:
            return jsonify({"error": "Unauthorized"}), 403
        return f(*args, **kwargs)
    return decorated

@app.route("/api/admin/users")
@require_admin
def list_users():
    return jsonify(db.get_all_users())
```

---

## Verbose Error Exposure

### Vulnerable
```python
@app.errorhandler(Exception)
def handle_error(e):
    return jsonify({"error": str(e), "traceback": traceback.format_exc()}), 500
```

### Safe
```python
import logging

@app.errorhandler(Exception)
def handle_error(e):
    logging.exception("Unhandled error")
    return jsonify({"error": "Internal server error"}), 500
```

---

## Insecure Random for Security Tokens

### Vulnerable
```python
import random
import string

def generate_token():
    return ''.join(random.choices(string.ascii_letters, k=32))
```
`random` is not cryptographically secure.

### Safe
```python
import secrets

def generate_token():
    return secrets.token_hex(32)
```

---

## CORS Wildcard on Sensitive Endpoint

### Vulnerable
```python
@app.after_request
def add_cors(response):
    response.headers["Access-Control-Allow-Origin"] = "*"
    return response
```

### Safe
```python
ALLOWED_ORIGINS = ["https://app.example.com"]

@app.after_request
def add_cors(response):
    origin = request.headers.get("Origin")
    if origin in ALLOWED_ORIGINS:
        response.headers["Access-Control-Allow-Origin"] = origin
    return response
```
