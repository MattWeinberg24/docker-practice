# adapted from https://fastapi.tiangolo.com/deployment/docker/

# Start from official Python base image
FROM python:3.9

# Set the working directory to /code
WORKDIR /code

# Copy requirements file (this step cached since does not change often)
COPY ./requirements.txt /code/requirements.txt

# Install or upgrade pip packages from the requirements file (if not cached)
RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

# Copy the ./app directory inside the /code directory (changes frequently)
COPY ./app /code/app

# Start server (add "--proxy-headers" in case using nginx later)
CMD ["uvicorn", "--proxy-headers", "app.main:app", "--host", "0.0.0.0", "--port", "80"]