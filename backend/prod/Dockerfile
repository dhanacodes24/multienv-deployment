FROM python:3.11-slim
 
WORKDIR /app
 
ENV PYTHONUNBUFFERED=1
 
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt gunicorn
 
COPY . .
 
EXPOSE 3002
 
# prod: gunicorn instead of the Flask dev server
CMD ["gunicorn", "--bind", "0.0.0.0:3002", "--workers", "2", "app:app"]

