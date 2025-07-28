# 🧠 Flask Web App on AWS EC2 (with Gunicorn + Nginx)

This is a simple Flask-based blog web application deployed on an AWS EC2 instance using **Gunicorn** as the WSGI server and **Nginx** as the reverse proxy. It demonstrates how to serve production-ready Python apps on the cloud using Linux services and Python environments.

---

## 📌 Features

- Basic Blog App (Add/View Posts)
- Flask + Jinja2 Templates
- Gunicorn (Production WSGI Server)
- Nginx (Reverse Proxy)
- Systemd Service Setup
- EC2 Deployment with Ubuntu/Amazon Linux
- HTML Templates for UI

---

## 🧱 Project Structure

flask-webapp-on-ec2/
├── app.py
├── templates/
│ ├── index.html
│ ├── post.html
│ ├── new_post.html
│ ├── not_found.html
│ └── error.html
├── gunicorn.log
├── README.md
└── venv/


---

## 🚀 Deployment Architecture

```text
Browser
   |
   | HTTPS (Port 443)
   ↓
Nginx (Reverse Proxy)
   |
   ↓
Gunicorn (Python WSGI Server)
   |
   ↓
Flask Application (app.py)


⚙️ How to Run (on EC2)
1️⃣ Launch EC2 Instance
Use Amazon Linux 2 or Ubuntu

Enable HTTP/HTTPS ports in Security Group

2️⃣ Connect to EC2 and Install Dependencies

sudo yum update -y            
sudo yum install python3 git -y
sudo pip3 install virtualenv

3️⃣ Clone or Upload This Project

git clone https://github.com/DEEPAKMISAL01/flask-webapp-on-ec2.git
cd flask-webapp-on-ec2

4️⃣ Setup Python Virtual Environment

virtualenv venv
source venv/bin/activate
pip install flask gunicorn


5️⃣ Run Gunicorn

nohup gunicorn -w 1 -b 127.0.0.1:5000 app:app > gunicorn.log 2>&1 &

6️⃣ Configure and Start Nginx

sudo vi /etc/nginx/nginx.conf     # Add reverse proxy config
sudo systemctl restart nginx


Sample config in nginx.conf:

location / {
    proxy_pass http://127.0.0.1:5000;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
}


🛠️ Commands Reference

# Check Gunicorn Logs
tail -f gunicorn.log

# Restart Gunicorn
pkill gunicorn
nohup gunicorn -w 1 -b 127.0.0.1:5000 app:app > gunicorn.log 2>&1 &

# Restart Nginx
sudo systemctl restart nginx
sudo tail -n 20 /var/log/nginx/error.log


## 🧑‍💻 Author

**Deepak Misal**  
Aspiring AWS DevOps Engineer  

🔗 [GitHub Profile](https://github.com/DEEPAKMISAL01)  
🔗 [LinkedIn](https://www.linkedin.com/in/deepak-misal/)


🪪 License
This project is licensed under the MIT License. Free to use and modify.




Let me know if you want:
- 📁 A downloadable ZIP with everything
- 🎨 A custom logo for this project
- 💡 Add database support like SQLite/PostgreSQL

I’m ready when you are!
