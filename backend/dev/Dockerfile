FROM python:3.11-slim
 
WORKDIR /app
 
ENV PYTHONUNBUFFERED=1
 
# install dependencies first so Docker can cache this layer
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
 
COPY . .
 
EXPOSE 3001
 
# dev: run the Flask app directly (debug mode is already on in app.py)
CMD ["python", "app.py"]

