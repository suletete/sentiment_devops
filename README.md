# Dockerized Sentiment Analysis Application

**Developed by:**
Suleiman Abdulkadir
Fellow ID: FE/23/22599501
Cohort 3
Course: DevOps

---

This project is a **Dockerized Sentiment Analysis web application** built from scratch to demonstrate the integration of AI and DevOps practices. It consists of two main services packaged as Docker containers:

* An AI model service (*ml\_service*) that processes user input to predict sentiment.
* A UI service (*ui\_service*) that provides a web interface for users to interact with the model.

You can find related inspiration and references in [this repo](https://github.com/suletete/sentiment_devops/).

---

## Development Overview

1. Build a Docker container serving the sentiment analysis model as the **ml\_service**. The model loads once when the container starts.
2. Build a Docker container serving the web UI called **ui\_service**. This service sends user input to the model container and displays the sentiment score.
3. Use **docker-compose** to start both services and link them seamlessly.

---

## Running the Application Locally

1. From the project root directory, build Docker images by running:

   ```bash
   docker-compose build
   ```

   *Note: TensorFlow and other packages may take time to download and build.*

   Verify the images with:

   ```bash
   docker images
   ```

   You should see `sentiment_analysis_ml_service` and `sentiment_analysis_ui_service`.

2. Start the ML service container in detached mode:

   ```bash
   docker-compose up -d ml_service
   ```

   Confirm it’s running with:

   ```bash
   docker ps
   ```

   Open [http://localhost:8000/](http://localhost:8000/) in your browser; you should see:

   > "ML model service is running!"

3. Start the UI service:

   ```bash
   docker-compose up ui_service
   ```

   In a new terminal, verify with `docker ps` that the UI container is running.
   Visit [http://localhost:8001/](http://localhost:8001/) to access the web interface.

4. Use the app by typing sentences to get real-time sentiment predictions.

5. To stop and clean up containers:

   ```bash
   docker rm -f ui_service ml_service
   ```

   Check no containers are running with:

   ```bash
   docker ps -a
   ```

---

## Alternative Way to Run

You can start both services together with:

```bash
docker-compose up
```

This will build and run both containers, with logs streaming in your terminal.
Then visit [http://localhost:8001/](http://localhost:8001/) to use the application.

---
