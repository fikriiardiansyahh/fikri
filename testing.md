# ASAH: Cloud Computing
## About Our Project

This project aims to leverage cloud computing technologies to build a scalable and efficient system called ASAH. ASAH is a platform that combines mobile development and machine learning to create a waste management solution.

## Related Project Repositories

Here are some of the related repositories which are part of the same project:

| Repository | Link |
| --- | --- |
| 📱 Mobile Development | [MD Repository](https://github.com/ASAH-Bangkit-2023/MD.git) |
| 🤖 Machine Learning | [ML Repository](https://github.com/ASAH-Bangkit-2023/ML) |

# Deployment Steps

## 1. Cloud SQL

- Fill in the instance ID and password.
- Scroll down to create the instance.

![Create Instance](https://github.com/fikriiardiansyahh/fikri/assets/72667607/a81c2e96-53cd-4df8-8c3e-53ba5da49848)

- Change the network to public to make it accessible to clients.

![Change Network](https://github.com/fikriiardiansyahh/fikri/assets/72667607/fae32be0-3377-4019-8b1a-c0911b7cf535)

- Save the configuration.

## 2. Cloud Storage

- Create a bucket with a suitable name.

![Create Bucket](https://github.com/fikriiardiansyahh/fikri/assets/72667607/e7d1c010-90db-4c44-97ff-37d5aa9fd2e9)

- Uncheck "enforce public access prevention on this bucket" to make it accessible.

![Bucket Permissions](https://github.com/fikriiardiansyahh/fikri/assets/72667607/1f028a37-a731-4540-8564-eb2b8e16ba1e)

- Add "allUsers" and "allAuthenticatedUsers" as new principals with the role "storage viewer".

![Add Principals](https://github.com/fikriiardiansyahh/fikri/assets/72667607/265bc86c-4258-4444-b777-dc6d6ce8b707)

- Save the changes.

## 3. Create Maps API Key

- Follow the instructions below to create an API key if one doesn't exist:
  1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
  2. Select the project or create a new project.
  3. Enable the Places API for your project.
  4. Generate an API key.
  5. Copy the generated API key.

## 4. Prepare FastAPI (Using this exist repository)

- Clone the repository from the existing repo:
  ```bash
  git clone https://github.com/your-repo.git
  ```

## 5. Prepare Dockerfile

- Use the provided Dockerfile template for setting up the image.

```dockerfile
FROM python:3.11-slim

ENV PYTHONUNBUFFERED True
ENV APP_HOME /app

WORKDIR $APP_HOME

COPY . ./

ENV PORT 1234
ENV MYSQL_URL "mysql+pymysql://root:PASSWORD@SERVER-IP:PORT/NAME DATABASE"
ENV JWT_SECRET_KEY "SECRET KEY"
ENV JWT_REFRESH_SECRET_KEY "REFRESH SECRET KEY"

RUN pip install --no-cache-dir -r requirements.txt

CMD exec uvicorn main:app --host 0.0.0.0 --port ${PORT}
```

## 6. Cloud Run

- Click on "Create Service" in Cloud Run.

![Create Service](https://github.com/fikriiardiansyahh/fikri/assets/72667607/da236cde-1536-4f12-825a-72ed64d538b0)

- Connect the repository and configure the deployment settings.

![Connect Repository](https://github.com/fikriiardiansyahh/fikri/assets/72667607/6fcfa512-40d4-4140-b18f-4e3cbb36f778)

- Select the main branch and specify the deployment timeout.

![Branch and Timeout](https://github.com/fikriiardiansyahh/fikri/assets/72667607/6b1e5c38-fc3b-4a5d-8e34-6758e619a67a)

- Configure the container settings using the prepared Dockerfile.

![Container Settings](https://github.com/fikriiardiansyahh/fikri/assets/72667607/16f63ae3-093d-4cc8-9df4-4a56d92b9283)

- Set the environment variables.

![Environment Variables](https://github.com/fikriiardiansyahh/fikri/assets/72667607/6d70a5a3-5e39-4b3f-b571-6f8e3ae9f792)

- Click "Create" to deploy the service.

## 7. Testing the Application

To test the deployed application, you can use tools like `curl` or API testing tools like Postman. Here is an example of how to test the API using `curl`:

```bash
curl -X GET https://your-app-url.com/api/endpoint
```

Replace `your-app-url.com` with the actual URL of your deployed application and `/api/endpoint` with the desired endpoint to test.

You can also use Postman to send requests to the API and verify the responses.
